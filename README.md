# Comparative between frameworks frontend
Comparative between Vue 3, Svelte, React, SolidJS and Qwik creating an input text.

### Vue 3
```html
<script setup>
import { ref } from "vue";
const text = ref("Hello World");
</script>

<template>
  <p>{{ text }}</p>
  <input v-model="text">
</template>
```

### Svelte
```html
<script>
  let text = "Hello World";
</script>

<p>{text}</p>
<input bind:value={text} />
```

### React
```js
import { useState } from "react";

export default function InputHello() {
  const [text, setText] = useState("Hello");

  function handleChange(event) {
    setText(event.target.value);
  }

  return (
    <>
      <p>{text}</p>
      <input
        value={text}
        onChange={handleChange}
      />
    </>
  );
}
```

### SolidJS
```js
import { createSignal } from "solid-js";

export default function InputHello() {
  const [text, setText] = createSignal("Hello");

  function handleChange(event) {
    setText(event.target.value);
  }

  return (
    <>
      <p>{text()}</p>
      <input
        value={text()}
        onInput={handleChange}
      />
    </>
  );
}
```

### Qwik
```js
import { component$, useStore, $ } from "@builder.io/qwik";

const InputHello = component$(() => {
  const store = useStore({ text: "" });

  const handleChange = $((event: InputEvent) => {
    store.text = (event.target as HTMLInputElement).value;
  });

  return (
    <>
      <p>{store.text}</p>
      <input
        value={store.text}
        onInput$={handleChange}
      />
    </>
  );
});

export default InputHello;
```
