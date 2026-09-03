# Sedativ support for VS Code

Official Visual Studio Code extension for the Sedativ framework. Provides syntax highlighting for HTML and SQL tagged template literals and snippets for rapid code insertion.

---

## Syntax Highlighting

Provides automatic inline syntax highlighting inside `.js` and `.mjs` files for:

- **HTML:** <code>html&#96;...&#96;</code> and <code>ref.html&#96;...&#96;</code>
- **SQL:** <code>sql&#96;...&#96;</code> and <code>ref.sql&#96;...&#96;</code>

Supports arbitrary nesting with template literal expressions `${ ... }`.

---

## Snippets

Type a snippet prefix in the editor and press `Tab` to insert it. Use `Tab` to navigate between tabstops (`⁝1`, `⁝2`, etc.).



**$s** - Inserts signal:
```js
const ⁝1 = $(⁝2)
```

**$d** - Inserts persisted signal:
```js
const ⁝1 = $(⁝3, '⁝2')
```

**$e** - Inserts side effect:

```js
$(() => {
  ⁝1
})
```

**$w** - Inserts component:

```js
$(ref => {
  ref.html`⁝2`
}, '⁝1')
```

**$f** - Inserts form request handler:

```js
$(ref => {
  ref.html`
    <form action="⁝2" method="⁝3">⁝4</form>
  `

  ref.onsubmit = async event => {
    event.preventDefault()
    await fetch(event.target.action, {
      method: event.target.method,
      body: new FormData(event.target),
    })
  }
}, '⁝1')
```

**$r** - Inserts JSON request handler:

```js
$(ref => {
  ref.onsubmit = async event => {
    event.preventDefault()
    await fetch('⁝2', {
      method: '⁝3',
      headers: { 'content-type': 'application/json' },
      body: JSON.stringify({ ⁝4 }),
    })
  }
}, '⁝1')
```

**$q** - Inserts text response handler:

```js
$(req => {
  if (req.method === '⁝1') {
    return new Response(
      '⁝2',
      {
        status: 200,
        statusText: 'OK',
        headers: { 'content-type': 'text/plain' }
      }
    )
  }
})
```

**$a** - Inserts JSON response handler:

```js
$(req => {
  if (req.method === '⁝1') {
    return new Response(
      JSON.stringify({ ⁝2 }),
      {
        status: 200,
        statusText: 'OK',
        headers: { 'content-type': 'application/json' }
      }
    )
  }
})
```