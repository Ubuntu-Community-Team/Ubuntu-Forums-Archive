---
title: "Tutorial for building from source?"
date: 2007-02-01
forum: General Help
---

### Post by thevinn on 2007-02-01
Is there a tutorial or some kind of reference somewhere that I can read to learn about how to set up my Ubuntu installation for retrieving source packages, building them, making changes, and debugging? I sort of know how to use Linux but I dont know the details of things like using apt-get, where to get sources.

What would be a small tool to practice building/changing on?

Is there a guide somewhere?

Thanks!!

---

### Post by cactaur on 2007-02-01
Well, I'm not that sure about a tutorial. But the way you get the source packages for programs is by typing:

```
apt-get source *packagename*
```
(No sudo)

The sources will then be copied to your home folder. And I think you just compile them like you would anything else from source. Some packages don't have source files attached to them, so that's something else you should know. I hope this was of help to you.

---

### Post by thevinn on 2007-02-02
> **cactaur said:**
> 
...
```
apt-get source *packagename*
```
(No sudo)


Yep, I figured that out. I went beyond Ubuntu, to this Debian site:

[http://www.debian.org/doc/FAQ/ch-pkg_basics.en.html](http://www.debian.org/doc/FAQ/ch-pkg_basics.en.html)

and did

apt-get source abiword

Unfortunately I used sudo but I will correct that mistake. Now apparently I need a bunch of dependencies so I was considering using

apt-get build-dep abiword

Seems like there are a lot of dependencies. It wanted to install an extra 70 mb of development libraries and such. I decided against it because I did not want a bunch of files to get sent to random places in the file system that I don't know about. Also I read something about a "chroot" environment for development, to segregate development files from regular files needed to run Ubuntu as a plain user?

Is trying to compile abiword a little too ambitious?

---

### Post by lamego on 2007-02-02
Give a look at the script I have created to help building the chroot environment:
[http://www.getdeb.net/wiki/doku.php?id=package_builder:preparing](http://www.getdeb.net/wiki/doku.php?id=package_builder:preparing)

---

### Post by pseudonym on 2007-02-02
> **thevinn said:**
> Yep, I figured that out. I went beyond Ubuntu, to this Debian site:

[http://www.debian.org/doc/FAQ/ch-pkg_basics.en.html](http://www.debian.org/doc/FAQ/ch-pkg_basics.en.html)
Debian.org manuals is where you want to be. The website of [this Debian developer]("http://people.connexer.com/~roberto/howtos/debcustomize") may also be useful to you.

> **thevinn said:**
> Unfortunately I used sudo but I will correct that mistake. Now apparently I need a bunch of dependencies so I was considering using

apt-get build-dep abiword

Seems like there are a lot of dependencies. It wanted to install an extra 70 mb of development libraries and such. I decided against it because I did not want a bunch of files to get sent to random places in the file system that I don't know about.
This is what you will get if you want to build source packages - you need to install loads and loads of development files.

> **thevinn said:**
> Is trying to compile abiword a little too ambitious?
I'm sure you have your reasons, but if you are an ordinary user just wanting to set their system up, there is no point compiling from source when everyting you could ever want is available in pre-compiled packages from the repositories (unless you have some obscure program which only comes in source form, in which case it's better to try and find a suitable packaged program).

If, on the other hand, you want to learn packaging because you are interested, then the best thing to do is set up a chroot build environment as mentioned.

---

### Post by thevinn on 2007-02-02
> **pseudonym said:**
> I'm sure you have your reasons, but if you are an ordinary user just wanting to set their system up, there is no point compiling from source when everyting you could ever want is available in pre-compiled packages from the repositories (unless you have some obscure program which only comes in source form, in which case it's better to try and find a suitable packaged program).

If, on the other hand, you want to learn packaging because you are interested, then the best thing to do is set up a chroot build environment as mentioned.

I'm interested mainly in fixing bugs in the applications that I am using. My short term goals are the following

1. Get source code to a simple utility
2. Set up a chroot environment (is this the right way to go?)
3. Get a development IDE
4. Build the utility and get a breakpoint with a debugger, step through it to make sure everything in the IDE works
5. Get sources to a main application (Firefox to start)
6. Build the application
7. Run application, make sure my build works
8. Get a break point with a debugger and step through it
9. Make a change, recompile, test, etc...

I tried following the link to the chroot tutorial, no luck there (links is broken). Should I be getting sources as root? Or using my regular user login? What about the other library dependencies, do I get those as root, or as myself? Is the chroot environment built as sudo?

I'm a fairly good developer but I don't really know much about this new way of doing things under Linux. Specifically, I'm none too familiar with packages, creating a chroot environment, etc. although I do know how to use makefiles, configure, etc...

---

