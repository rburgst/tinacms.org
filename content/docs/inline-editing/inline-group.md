---
title: Inline Group
prev: /docs/inline-editing/inline-image
next: /docs/inline-editing/inline-blocks
consumes:
---

The `InlineGroup` represents a collection of inline fields. It serves as a wrapper for providing additional UI for inline elements outside of blocks. This group provides its own _simple controls_ — exposing the ability to display a **modal with additional form fields**.

## Definition

Below is an example of how `InlineGroup` may be used in an [Inline Form](/docs/inline-editing).

```jsx
import { useForm, usePlugin } from 'tinacms'
import {
  InlineForm,
  InlineGroup,
} from 'react-tinacms-inline'

// Example 'Hero' Component
export function Hero(props) {
  const [data, form] = useForm(props.data)

  usePlugin(form)

  return (
    <InlineForm form={form}>
      <InlineGroup
        name="hero"
        fields={[
          {
            name: 'typography.style',
            label: 'Type Style',
            description: 'Select a type style for the hero copy',
            component: 'select',
            options: ['Swiss-Style','Art-Nouveau', 'Command-Line'],
          },
          {
            name: 'typography.color',
            label: 'Type Color',
            description: 'Select a color for the hero copy',
            component: 'color'
            widget: 'block'
            colors: ['#404040', '#ff0000', #1B1E25],
          },
        ]}
        >
          <HeroCopy typography={data.hero.typography}>
            <InlineText focusRing={false} name="heroCopy" />
          </HeroCopy>
      </InlineGroup>
    </InlineForm>
  )
}
```

This example assumes your data looks something like this:

```json
{
  "hero": {
    "heroCopy": "Call me Ishmael",
    "typography": {
      "style": "Swiss-Style",
      "color": "#1B1E25"
    }
  }
}
```

## Options

| Key      | Description                                                                                                                            |
| -------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| `name`   | The path to some value in the data being edited. If no value is provided, the child fields will reference the root of the source file. |
| `fields` | An array of [Tina Fields](/docs/fields) to display in a settings modal form.                                                           |

## Interface

```typescript
interface InlineGroupProps {
  name: string
  fields: TinaField[]
}
```
