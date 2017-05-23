<!--
title: 12 - Publishing npm packages
featured: true
-->

# Publishing npm packages

<iframe src="https://www.youtube.com/embed/BkotrAFtBM0" frameborder="0" allowfullscreen></iframe>

You can publish any directory that has a `package.json` file, e.g. a [node module](/getting-started/creating-node-modules).

## Creating a user

To publish, you must have a user on the npm registry. If you don't have one, create it with `npm adduser`. If you created one on the site, use `npm login` to store the credentials on the client.

Test: Use `npm config ls` to ensure that the credentials are stored on your client. Check that it has been added to the registry by going to [https://npmjs.com/~](https://npmjs.com/~)<username>.

## Publishing the package

Use `npm publish` to publish the package.

Note that everything in the directory will be included unless it is ignored by a local `.gitignore` or `.npmignore` file as described in [`npm-developers`](/misc/developers).

Also make sure there isn't already a package with the same name, owned by somebody else.

Test: Go to `https://npmjs.com/package/<package>`. You should see the information for your new package.

## Public vs. private packages

An unscoped package can only be public, so any package you publish without a scope will be public. Scoped packages can be public or private, and are private by default. See [working with scopes](/getting-started/scoped-packages) for more information.

## Updating the package

When you make changes, you can update the package using `npm version <update_type>`, where update_type is one of the semantic versioning release types, patch, minor, or major. This command will change the version number in `package.json`. Note that this will also add a tag with this release number to your git repository if you have one.

After updating the version number, you can `npm publish` again.

Test: Go to `https://npmjs.com/package/<package>`. The package number should be updated.

The README displayed on the site will not be updated unless a new version of your package is published, so you would need to run `npm version patch` and `npm publish` to have a documentation fix displayed on the site.
