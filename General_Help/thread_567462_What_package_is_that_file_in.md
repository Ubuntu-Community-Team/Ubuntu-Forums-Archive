---
title: "What package is that file in?"
date: 2007-10-04
forum: General Help
---

### Post by jharr on 2007-10-04
One question I get all the time is "What package is that file in?" There's a really easy way to find out yourself. It's called apt-file and it can search for a file in any package (installed or not). It's really easy to use:

    $ sudo apt-get install apt-file
    $ sudo apt-file update
    $ apt-file search autoexpect
    expect-dev: usr/share/doc/expect-dev/examples/autoexpect.1.gz
    expect-dev: usr/share/doc/expect-dev/examples/autoexpect.gz
    expect-tcl8.3: usr/share/doc/expect-tcl8.3/examples/autoexpect
    expect-tcl8.3: usr/share/doc/expect-tcl8.3/examples/autoexpect.1
    manpages-ja: usr/share/man/ja/man1/autoexpect.1.gz

Apt-file comes in handy many times. One thing to note is that you don't need to run 'apt-file update' very often (once every release upgrade) since the file names don't change that much, just the file contents.

For the record, if you want to figure out which installed package a file belongs to, use 'dpkg -S'. This doesn't always work for config files, and files in /var, since those are generated after the package is extracted.

---

### Post by Jussi Kukkonen on 2007-10-04
Tutorials & tips might be a better sub-forum for this, the support sub-forums are meant for questions.

---

### Post by Zootropo on 2007-10-04
You can also use auto-apt which install the corresponding package automagically when  trying to access a file which is contained in a package which is not installed yet.

[apt-get en busca del archivo perdido](http://mundogeek.net/archivos/2005/02/08/apt-get-en-busca-del-archivo-perdido/)

---

