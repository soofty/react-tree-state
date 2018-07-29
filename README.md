# React Shared State

## React Shared State

[![](https://travis-ci.org/soofty/react-shared-state.svg?branch=master)](https://travis-ci.org/soofty/react-shared-state)

Very simple shared state for your react app.

```jsx
import React from 'react'
import { createProvider } from 'react-shared-state'

const SimpleProvider = createProvider('simple_provider')

const HelloComponent = (props) => {
  return <div>
    <h1> Hello, {props.name} </h1>
    <button onClick={() => props.store.setState({ name: 'Max' })}>Set Name</button>
  </div>
}
const Hello = SimpleProvider.connect((store) => ({ 
  name: store.state.name,
  store: store 
}))(HelloComponent)

export function App() {
  return (
    <SimpleProvider initialState={{ name: 'Anonymous' }}>
      <Hello />
    </SimpleProvider>
  )
}
```

### Install

`yarn add react-shared-state`  
or  
`npm install react-shared-state`

### Quickstart

[https://soofty.gitbook.io/react-shared-state/quickstart](https://soofty.gitbook.io/react-shared-state/quickstart)

### Documentation

[https://soofty.gitbook.io/react-shared-state/documentation](https://soofty.gitbook.io/react-shared-state/documentation)

### Live example

[https://codesandbox.io/s/wy308n0k88](https://codesandbox.io/s/wy308n0k88)

## 0.1.x =&gt; 0.2.x migration guide

**Important!** 0.2 has changed `connect`'s behavior.

1. mapStateToProps now accepts `store` instead of `store.state` as first argument
2. `connect` no longer passes `store` by it's name to a component
3. Preferable way to use connect is `YourProvider.connect` instead of building custom function
4. Changed Typescript's generics order from TOuterProps, TInnerProps to TInnerProps, TOuterProps \(recompose format\)

