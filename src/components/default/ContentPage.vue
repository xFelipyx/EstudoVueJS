<template>
    <section>
        <div>
           <p>Meu Conteúdo</p>
           <div>
                <input v-model="nome" placeholder="Digite seu nome">
                <p>Seu nome é {{ nome }}</p>
                <button @click="submeterFormulario">procurar usuario</button>
                <p v-if="url">
                    {{ url }}
                </p>
                <p v-else="url">
                    Você ainda não usou o botão
                </p>
           </div>
        </div>
    </section>
</template>
<script>
    export default{
        nome: 'ContentPage',
        data() {
            return {
                nome: '',
                url: ''
            }
        },
        methods: {
            submeterFormulario() { 
                fetch('https://api.github.com/users/' + this.nome).then((data) => {
                    this.url = data.url
                    console.log(data.url)});


            }
            
        },
    }
</script>
<style></style>