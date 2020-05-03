# Desafio 03 - Conceitos do ReactJS

Nesse desafio, você deve criar uma aplicação para treinar o que você aprendeu até agora no ReactJS!

Agora você deve continuar desenvolvendo a aplicação que irá armazenar repositórios do seu portfólio, que você já desenvolveu o backend no último desafio utilizando o Node.js.

## Funcionalidades da aplicação

Código para atingir os objetivos de cada funcionalidade.

### `Listar os repositórios da sua API`

Deve ser capaz de criar uma lista com o campo **title** de todos os repositórios que estão cadastrados na sua API.

```javascript
useEffect(() => {
  api.get("repositories").then((response) => {
    setRepositories(response.data);
  });
}, []);
```

### `Adicionar um repositório a sua API`

Deve ser capaz de adicionar um novo item na sua API através de um botão com o texto **Adicionar** e, após a criação, deve ser capaz de exibir o nome dele após o cadastro.

```javascript
async function handleAddRepository() {
  const response = await api.post("repositories", {
    title: "rocketseat-gostack-bootcamp-desafios",
    url: "https://github.com/costaruan/rocketseat-gostack-bootcamp-desafios",
    techs: ["Node.js", "ReactJS", "React Native"],
  });

  const repository = response.data;

  setRepositories([...repositories, repository]);
}
```

### `Remover um repositório da sua API`

Para cada item da sua lista, deve possuir um botão com o texto **Remover** que, ao clicar, irá chamar uma função para remover esse item da lista do seu frontend e da sua API.

```javascript
async function handleRemoveRepository(id) {
  await api.delete(`repositories/${id}`);

  const repositoriesData = [...repositories];
  const repositoryIndex = repositories.findIndex(
    (repository) => repository.id === id
  );

  repositoriesData.splice(repositoryIndex, 1);

  setRepositories(repositoriesData);
}
```

---

**Created by** `costaruan`
