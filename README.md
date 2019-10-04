# LXML Buildpack

We have the need for some specific versions of shared libraries installed using
buildpacks on certain machines. This buildpack provides a vendored package of
those libraries so they can be reliably installed.

It is a buildpack that extracts the following libraries onto a machine:

- `libxml2-2.9.1`
- `libxslt-1.1.28`

It does this by building those two libraries within a docker container and then
packaging them into a tar archive. When the buildpack is run it extracts these
files and adds a script to update `LD_LIBRARY_PATH` to include the path to the
file that was extracted.

## Development

Run `make dist` to create a new version of `dist.tar.gz`. This will unpack the
vendored dependencies and build them.

Run `test/compile` to check that the compile script can run.

