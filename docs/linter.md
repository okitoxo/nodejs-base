# Linter y estilo de código

A continuación se detalla la forma de como configurar el linter y estilo de código un nuevo proyecto escrito en NodeJS con Typescript. La siguiente configuración es una convención dada por el area de arquitectura.

## ¿Porqué ESLint y Prettier?

### Prettier

Prettier para el estilo de código porque, si bien se puede se puede tener un estilo de código personalizado, llegar a un acuerdo con los interesados podria tornarse extenso. Para esto Prettier nos da un estilo de código por convención para ahorrarnos esfuerzo.

### ESLint

Es el linter por excelencia para Javascript y se preocupa por la calidad de código y estilo de código escrito. Se puede integrar con el IDE de preferencia para tener un analisis en tiempo real.

Para poder integrar ambos se tiene que descartar las configuraciones de estilo de código de ESLint para que no tenga conflicto con Prettier para lo cual Prettier cuenta con un paquete que configura ESLint.

## Configuración

### Prettier

1. Instalar Prettier

```
yarn -D prettier
```

2. Agregar el archivo `.prettierrs.json` con el contenido con el contenido `{}`

```
echo {}> .prettierrc.json
```

3. Aplica Prettier a tus archivos

```
npx prettier --write ./src/
```

4. Opcional. Configurar tu Editor: [Editor Integration](https://prettier.io/docs/en/editors.html)

### ESLint (Typescript)

1. Instalar ESLint

```
yarn add -D eslint typescript @typescript-eslint/parser @typescript-eslint/eslint-plugin
```

2. Crear el archivo de configuración `.eslintrc.js` llenar con lo siguiente

```
module.exports = {
  root: true,
  parser: '@typescript-eslint/parser',
  plugins: [
    '@typescript-eslint',
  ],
  extends: [
    'eslint:recommended',
    'plugin:@typescript-eslint/recommended',
  ],
};
```

3. Para ignorar los archivos no necesarios para el linter crear `.eslinignore`

```
node_modules
dist
coverage
```

4. Integracion con tu IDE o Editor favorito: [Editor Integrations](https://eslint.org/docs/user-guide/integrations)

### Integración Prettier + ESLint

Para que Prettier y ESLint convivan se tienen que desactivar las reglas de estilo de código de ESLint. Prettier cuenta con un paquete para esto.

1. Instalar `eslint-config-prettier`

```
yarn add -D eslint-config-prettier
```

2. Agregar paquete a las extensiones de ESLint en el archivo `.eslintrc.js`

```
{
  "extends": [
    "some-other-config-you-use",
    "prettier"
    "prettier/@typescript-eslint"
  ]
}
```

3. Reinicia tu editor

### Integración con Husky

Adicionalmente se puede integrar con los Git Hooks para asegurar que cualquier commit tenga
...
