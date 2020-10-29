---
title: sortAlphabeticallyThunkCreator
tags: string,sorting,thunk
---

To be used when sorting an array of objects alphabetically by 1 key. The thunk is created dynamically, so you can specify the key. A thunk is just a function that delays an action.

For example, this can be used when trying to sort the following pokemon array by `type` or by `name`.
- Call the function with the key to create the thunk, and store in a variable.
- Use the `.sort` method on the array you wish to sort, and pass in the thunk.

```js
// The function
function sortAlphabeticallyThunkCreator(key) {
  return function(a, b) {
    if (a[key] < b[key]) {
      return -1;
    } else if (a[key] > b[key]) {
      return 1;
    }
    return 0;
  };
}
```

```js
// Example usage

const pokeList = [
	{type: "fire", name: "Charmander"},
	{type: "water", name: "Squirtle"},
	{type: "grass", name: "Bulbasaur"},
];

const sortByTypeThunk = sortAlphabeticallyThunkCreator("type");
const sortByNameThunk = sortAlphabeticallyThunkCreator("name");

pokeList.sort(sortByTypeThunk);
/*
[
	{type: "fire", name: "Charmander"}, 
	{type: "grass", name: "Bulbasaur"},
	{type: "water", name: "Squirtle"}
]
*/

pokeList.sort(sortByNameThunk); 
/*
[
	{type: "grass", name: "Bulbasaur"},
	{type: "fire", name: "Charmander"},
	{type: "water", name: "Squirtle"}
]
*/
```



