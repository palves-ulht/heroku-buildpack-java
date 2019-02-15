Heroku buildpack for Java with Maven 
=========================

A modified Heroku buildpack that makes maven available at runtime.

## What's hacked?

This buildpack has the only change from the source:

For example if you want to have maven binaries available to use at runtime in your application you simply have to copy it from the cache directory to the build directory by adding the following lines to the compile script:

    for DIR in ".maven" ; do
         cp -r $CACHE_DIR/$DIR $BUILD_DIR/$DIR
    done

This will copy maven binaries into your slug.

To use this build-pack:

```
# Create a new Heroku app that uses your buildpack
heroku create --buildpack <this-github-url>

# Configure an existing Heroku app to use your buildpack
heroku buildpacks:set <this-github-url>

# You can also use a git branch!
heroku buildpacks:set <this-github-url>#your-branch
```

License
-------

Licensed under the MIT License. See LICENSE file.
