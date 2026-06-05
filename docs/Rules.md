# Quicktool Rules

Quicktool defines a consistent set of conventions for Quickshell projects.
These rules are designed to improve readability, maintainability, and cross-project compatibility.

Rules are **strict by default**, but individual projects may opt into a relaxed profile.

## 1. Naming Conventions

### Components

- Use **PascalCase** for all QML components

Example:
```text
UserProfile.qml
StyledButton.qml
Workspaces.qml
```

### Identifiers

* Use **camelCase** for IDs and internal properties
* Avoid abbreviations unless they are widely understood

```qml
Item {
    id: mainContainer
}
```

## 2. File Structure Rules

### Folder Organization

* Group related components into feature-based folders
* Prefer composition over inheritance

## 3. Hierarchy & Layout

* Avoid deeply nested `Item` hierarchies
* Extract reusable logic into separate components
* Prefer flat structures where possible

Rule of thumb:

> If you need more than 4–5 nesting levels, refactor.

## 4. Styling & Formatting

### Property Order

Recommended order:

1. `id`
2. `anchors`
3. `width / height`
4. `positioning`
5. `visual properties`
6. `behavior / signals`
7. `content / children`

### Formatting

* Consistent indentation (**4 spaces** recommended)
* One property per line for readability
* Group related properties visually

### Bindings

* Avoid redundant or identity bindings
* Do not wrap static values in expressions

Bad:

```qml
width: 200 + 50
```

instead:

```qml
width: 250
```

or:

```qml
property int commonProperty: 50
width: 200 + commonProperty
...
// OtherComponent
width: 100 + commonProperty
```

## 5. Component Design

* Prefer composition over large monolithic components
* Keep components single-responsibility
* Expose only necessary properties via `property alias`

## 6. Documentation

* All public components must include a short description
* Complex logic **MUST** be documented inline
* Projects **SHOULD** include a `README.md`

Optional but recommended:

* Usage examples per component
* .awesome.md file for AwesomeQs description

## 7. Repository Compliance

Projects can declare Quicktool compliance in metadata:

```yaml
quicktool:
  version: 1
  complianceScore: 100
```

### Score

| Score     | Description                        |
| --------- | ---------------------------------- |
| 100       | Fully compliant with Quicktool     |
| 50        | Partially compliant with Quicktool |
| 0         | Not compliant with Quicktool       |

## 8. Recommended Repository Layout

```text
project/
├── shell.qml
├── modules/
│   ├── Bar/
│   ├── Launcher/
│   └── Dashboard/
├── components/
├── services/
├── assets/
├── scripts/
├── docs/
├── meta/
├── .awesome.md
└── README.md
```

## 9. Quicktool Metadata File

Optional project descriptor:

```yaml
quicktool:
  version: 1
  complianceScore: 100
  linting:
    enabled: true
  formatting:
    indent: 4
```

## 10. Philosophy

Quicktool is built on:

* **Predictability over freedom**
* **Readability over cleverness**
* **Structure over improvisation**
