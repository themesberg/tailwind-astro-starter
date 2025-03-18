# Tailwind 4 Astro Starter

Astro is a full-stack web framework for building lightning-fast and content-focused websites featuring component islands, server-first API design, edge-ready deployments and supports hundreds of integrations with technologies like Tailwind CSS, Flowbite, React, Vue, Svelte, and more.

The Astro framework is used by thousands of reputable companies and projects such as Firebase, NordVPN, The Guardian, Trivago and others and it also received a $7M seed investment funding at the beginning of 2022 which guarantees continuous support and development of the technology.

Follow the next steps in [this tutorial](https://flowbite.com/docs/getting-started/astro/) to learn how to create a new Astro project, install Tailwind CSS and learn how to leverage the UI components from Flowbite to build websites even quicker.

## Requirements

Before you continue make sure that you have [Node.js](https://nodejs.org/en/) (`v16.12.0` or higher) installed on your local machine and production server to install all required dependencies.

We also highly recommend you to use VS Code as your standard editor and to install the official [language support extension for Astro](https://marketplace.visualstudio.com/items?itemName=astro-build.astro-vscode) from the VS Marketplace released by the original authors.

## Create an Astro project

1. Create a new Astro project running the following command using NPM:

```bash
npm create astro@latest flowbite-project
cd flowbite-project
```

This command will prompt you with some questions and will create a local project based on your answers.

2. Run the following command to start a local development server:

```bash
npm run dev
```

This will make the project accessible via the browser on `http://localhost:3000`.

3. To create a production build of the project run the following command in your terminal:

```bash
npm run build
```

One of the biggest advantages of Astro is the small build size that will be available once deployed to production via the build command - this way the website should load much quicker than using older technologies.

## Install Tailwind CSS

Now that you have installed and configured a working Astro project we can proceed with installing the Tailwind CSS integration based on the official package.

1. Run the following command to install Tailwind CSS and create a configuration file using the NPX command:

```bash
npx astro add tailwind
```

This command will automatically install Tailwind CSS in the `package.json` file, it will also configure the compilation process and create a new `tailwind.config.cjs` file that configures the template paths.

2. Import the `global.css` file in your `Layout.astro` file:

```html
---
import "../styles/global.css";
---
```

Now you can write Tailwind CSS classes inside any of the template files and the changes will be applied by generating a `global.css` file and including it on every page.

## Install Flowbite

After you've installed both Astro and Tailwind CSS you can also choose to use the free and open-source UI components from Flowbite to make developing websites and user interfaces even faster with interactive elements like navbars, modals, dropdowns, and more.

1. Install Flowbite as a dependency using NPM by running the following command:

```bash
npm install flowbite --save
```

2. Import the default theme variables from Flowbite inside your main `global.css` CSS file:

```css
@import "flowbite/src/themes/default";
```

3. Import the Flowbite plugin file in your CSS:

```css
@plugin "flowbite/plugin";
```

4. Configure the source files of Flowbite in your `global.css` file:

```css
@source "../../node_modules/flowbite";
```

Now that you've configured the styles for CSS from Flowbite you can now proceed by installing the JS.

## Flowbite components

To enable the interactive [UI components from Flowbite](https://flowbite.com/docs/getting-started/astro/) you need to also include Flowbite's JavaScript file which you can do by either including it in the main `Layout.astro` file as a CDN file or importing the Flowbite module inside the 

### Include via CDN

In the `Layout.astro` file add the following script tag just before the end of the `<body>` tag:

```html
<script is:inline src="https://cdn.jsdelivr.net/npm/flowbite@3.1.2/dist/flowbite.min.js"></script>
```

This allows you to use the data attributes from the Flowbite component examples and will make them interactive automatically without needing to write custom JavaScript and you can just copy-paste them from the Flowbite Docs.

### ESM/CJS imports

Alternatively, you can import standalone components such as the Modal and set up the event listeners yourself in a local `<script>` tag for the Astro files. 

Since version 1.6.0 Flowbite also supports type declarations and interfaces in TypeScript which allows you to integrate with the Astro ecosystem even better as they clearly recommend TypeScript over JavaScript.

For example, here's how you can leverage the Flowbite JS API and Astro by adding the following code inside the script tag:

```javascript
<Layout>
  <!-- markup source content and elements -->
</Layout>

<script>
  import { Modal } from 'flowbite'

  // select the two elements that we'll work with
  const $buttonElement: HTMLElement | null = document.querySelector('#button');
  const $modalElement: HTMLElement | null = document.querySelector('#defaultModal');

  // create a new modal component
  const modal = new Modal($modalElement);

  // toggle the visibility of the modal when clicking on the button
  if ($buttonElement) {
    $buttonElement.addEventListener('click', () => modal.toggle());
  }
</script>
```
