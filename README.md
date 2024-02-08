# composer-example

## Using a git repository as a composer repository

In your source repo for the module or theme, you need to add a composer.json file with a variation of the following json code:

```
{
 "name": "szipfel/composer-example",
 "description": "Sample drupal repo for use with composer.",
 "type": "drupal-module",
 "homepage": "https://www.drupal.org/sandbox/z1pp3r/2857119",
 "authors": [{
   "name": "Steve Zipfel",
   "homepage": "https://github.com/szipfel/composer-example"
 }],
 "support": {
   "issues": "https://github.com/szipfel/composer-example/issues"
 },
 "license": "GPL-2.0+",
 "repositories": [{
   "type": "package",
   "package": {
     "name": "szipfel/composer-example",
     "version": "1.0",
     "type": "drupal-module",
     "source": {
       "url": "https://github.com/szipfel/compoer-example.git",
       "type": "git",
       "reference": "refs/heads/main"
     }
   }
 }]
}
```

### Types:

Theme: "type": "drupal-theme",
Module" "type": "drupal-module",

This works with the section of your composer.json, in your site project:

"type:" dictates where the code will be installed

```
 "installer-paths": {
            "web/core": [
                "type:drupal-core"
            ],
            "web/libraries/{$name}": [
                "type:drupal-library"
            ],
            "web/modules/contrib/{$name}": [
                "type:drupal-module"
            ],
            "web/profiles/contrib/{$name}": [
                "type:drupal-profile"
            ],
            "web/themes/contrib/{$name}": [
                "type:drupal-theme"
            ],
            "drush/Commands/contrib/{$name}": [
                "type:drupal-drush"
            ],
            "web/modules/custom/{$name}": [
                "type:drupal-custom-module"
            ],
            "web/profiles/custom/{$name}": [
                "type:drupal-custom-profile"
            ],
            "web/themes/custom/{$name}": [
                "type:drupal-custom-theme"
            ]
        },

```


If you use “minimum-stability”: “stable”  then you will need to push a tag in the repo 1.0 or it will fail.

Example fail message:

```
Could not find a version of package szipfel/composer-example matching your minimum-stability (stable).
Require it with an explicit version constraint allowing its desired stability.
```

### Tagging and Pushing a Git Tag

git tag -a 1.0  -m "1.0 Release"
git push --tags

```
Add Repository to your composer.json in the project you would like to add it to
"repositories": [
     {
           "type": "composer",
           "url": "https://packages.drupal.org/8"
       },
       {
           "type": "git",
           "url": "https://github.com/szipfel/composer-example.git"
         }
],
```

Notice:

```
{
  "type": "git",
  "url": "https://github.com/szipfel/composer-example.git"
}
```

This tells composer where to find  “szipfel/composer-example”

In your project you can now do “composer require szipfel/composer-example” and composer will pull it into the right place.
