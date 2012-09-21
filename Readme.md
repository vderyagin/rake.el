# rake.el #

Rake task runner for GNU Emacs.

![screenshot](https://github.com/vderyagin/rake.el/raw/master/screenshot.png)

## Installation ##

Download `rake.el` from this repository, put it on Emacs `load-path`,
put `(require 'rake)` in your initialization file. Now you can use `M-x rake`
to run rake tasks, `C-u M-x rake` to run global rake tasks.

Alternatively, If you are using [el-get](https://github.com/dimitri/el-get),
use this recipe:

``` lisp
(:name rake.el
       :type github
       :pkgname "vderyagin/rake.el")
```


## Problems ##

This package uses Emacs compilation-mode, which does not expect process to
launch asynchronous subprocesses; if it does, and they keep running after the
main process has terminated, Emacs may kill them. Be aware of that if you are
shelling out using `IO::popen`, `Kernel#spawn` or launching async subprocesses
is some other way from your rake tasks (using ``Kernel#` ``, `Kernel#system`,
also `FileUtils#sh` and `FileUtils#ruby` added by rake is no problem, as they
work synchronously).
