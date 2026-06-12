---
title: "Unable to compile and install software (configure not found)"
date: 2017-11-15
forum: General Help
---

### Post by asb3 on 2017-11-15
I want to install gnu octave 4.2.1 and symlinks.  Both installations failed at the configure stage.
I'll describe my attempt to compile octave.
I downloaded, unzipped, and untarred octave, placing the files in their own directory.

I then tried to run configure:
> ./configure
bash: ./configure: No such file or directory.

There is no configure script in the directory.  I tried to generate one with automake

> automake
automake: error: 'configure.ac' is required

There is no configure.ac file in the distribution.

What do I do?

---

### Post by Yellow Pasque on 2017-11-16
It would probably be easier to use the PPA.
[https://launchpad.net/~octave/+archive/ubuntu/stable](https://launchpad.net/~octave/+archive/ubuntu/stable)

---

### Post by asb3 on 2017-11-16
I used the PPA and was able to install octave 4.2.1.
I still can't install symlinks.  I have the same problem; there is no configure file in the release.
> ls
LICENSE  Makefile  Readme.md  symlinks  symlinks.8  symlinks.c
Readme.md contains
Installation
------------

### Source:

    $ ./configure
    $ make
    $ make install

But I can't do this because there is no configure file:
>./configure
bash: ./configure: No such file or directory
>automake
automake: error: 'configure.ac' is required

---

### Post by asb3 on 2017-11-16
I managed to compile and install symlinks.
I skipped the configure step, and instead executed
>make symlinks
which generated the executable "symlinks"

I tried to install using
>make install
and it failed, so I installed it by hand
sudo mv symlinks /usr/bin
sudo mv symlinks.8 /usr/share/man/man8

It seems to be installed correctly.

---

