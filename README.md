# npm-to-yarn

NPM to Yarn is a collection of scripts that help in the transition from NPM. It introduces 2 scripts:

## 1. npm-to-yarn
`./bin/npm-to-yarn` migrates the project from using NPM towards the use of Yarn by executing the following steps:

1. Requests the user to install yarn in case it detects yarn is missing.
2. Removes `package-lock.json` and `.npmrc` if it exists.
3. Replaces all the occurrences of `npm run` and `npm` with `yarn` in `package.json`.
4. Generates a `.yarnrc` file with a default configuration.
5. Generates the `yarn.lock` file by executing `yarn install`.

## 2. release automation
`./bin/setup-release` automates the process of releasing npm packages. However it assumes a certain setup.
In order to use this process, make sure that you have the following:

1. `travis` defined as a script in your `package.json`, for CI purposes. It might have defined steps like running a linter, unit tests, etc.
2. `build` defined as a script in your `package.json`.
4. `publishConfig` with a defined registry in your `package.json`.
5. It assumes that the build file is generated in the `../dist/` directory relative to this script. Feel free to rewrite the path according to your needs.
