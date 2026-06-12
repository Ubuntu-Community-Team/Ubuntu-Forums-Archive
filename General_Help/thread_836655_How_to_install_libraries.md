---
title: "How to install libraries?"
date: 2008-06-21
forum: General Help
---

### Post by mishathegoat on 2008-06-21
Hey everyone,
I was wondering how I could install "libraries" in Ubuntu Server since there is no package manager.. I need to install these:

xlibs-dev
x-window-system-dev
x11-devel

to install fluxbox

---

### Post by x1a4 on 2008-06-21
Hi,

Doesn't the server come with apt-get and/or aptitude?  If so use ```
aptitude install xlibs-dev x-window-system-dev x11-devel fluxbox
```
Or apt-get instead of aptitude if you prefer.  Aptitude is better, though.  It also has a curses interface.  Just run it without any options.

---

### Post by mishathegoat on 2008-06-21
Oh.. I also forgot to mention that this particular computer does not have an internet connection.. sorry..

---

### Post by sdennie on 2008-06-21
If you are trying to build fluxbox from source you could also try:

```

sudo apt-get build-dep fluxbox

```

Which will install all the things needed to build fluxbox.  However, fluxbox is also in the repos so, you could just as easily just install it from there without compiling it with:

```

sudo apt-get install fluxbox

```

---

### Post by x1a4 on 2008-06-21
> **mishathegoat said:**
> Oh.. I also forgot to mention that this particular computer does not have an internet connection.. sorry..

Using a computer with an Internet connection, visit [archive.ubuntu.com/ubuntu/]("http://archive.ubuntu.com/ubuntu/") download the desired packages along with their dependencies, burn to CD and install on server.

---

### Post by mishathegoat on 2008-06-21
> **x1a4 said:**
> Using a computer with an Internet connection, visit [archive.ubuntu.com/ubuntu/]("http://archive.ubuntu.com/ubuntu/") download the desired packages along with their dependencies, burn to CD and install on server.

Hmm.. I can't see where to download the dependencies.. There's only the packages

---

