React-Principal internally using a few useful tools. We exported them.

## createReducer

This is a useFull tools for define reducer clearly

```js
import { createReducer } from "react-principal";

const SET_FOO = "SET_FOO";
const SET_BAR = "SET_BAR";

export const reducer = createReducer({
  [SET_FOO]: (state, { payload: { foo } }) => ({
    ...state,
    foo,
  }),
  [SET_BAR]: (state, { payload: { bar } }) => ({
    ...state,
    bar,
  }),
});
```

## Observe

For better performance of context you could use this

```js
import { calculateChangedBits, useContextWithObserve } from "react-principal";

const context = createContext({ foo: "foo", bar: "bar" }, calculateChangedBits);

export function app() {
  const { foo } = useContextWithObserve(context, ["foo"]);

  ...
}
```