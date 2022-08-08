Script to update all descriptions automatically:

```shell
for f in $(find packages -name 'desc.yaml'); do
  dir=$(dirname $f)
  tag=$(basename $dir)
  without_tag=$(dirname $dir)
  url=${without_tag/packages/https:\/}
  toit.pkg describe $url v$tag --out-dir=$PWD
done
```
The github.com/xal88/TOIT_PCF8574/1.0.0/desc.yaml package uses UTF-16 in
its README. This is currently not recognized by our package tools. The
description was checked in by hand. There is currently no good way to
regenerate it automatically.
