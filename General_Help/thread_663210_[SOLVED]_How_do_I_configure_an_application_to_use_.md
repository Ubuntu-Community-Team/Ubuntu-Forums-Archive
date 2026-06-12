---
title: "[SOLVED] How do I configure an application to use a newer version of a dependency?"
date: 2008-01-09
forum: General Help
---

### Post by aephex on 2008-01-09
I've just installed the Themes Creator from Sony Ericsson. When I run it it looks for an old version of libgstreamer. 
```
:***@****:~$ ThemesCreator
ThemesCreator: error while loading shared libraries: libgstreamer-0.8.so.1: cannot open shared object file: No such file or directory

```
I have Ubuntu 7.10 which has libgstreamer-0.10 installed which I have been informed is a newer version.

I'd like to try and tell the program to reference this newer version of libgstreamer as a possible workaround. If this is feasible how would I go about it?

Barring that; is it possible to have two versions of libgstreamer installed? If so, how?

---

### Post by dcstar on 2008-01-09
> **aephex said:**
> I've just installed the Themes Creator from Sony Ericsson. When I run it it looks for an old version of libgstreamer. 
```
:***@****:~$ ThemesCreator
ThemesCreator: error while loading shared libraries: libgstreamer-0.8.so.1: cannot open shared object file: No such file or directory

```
I have Ubuntu 7.10 which has libgstreamer-0.10 installed which I have been informed is a newer version.

I'd like to try and tell the program to reference this newer version of libgstreamer as a possible workaround. If this is feasible how would I go about it?

Barring that; is it possible to have two versions of libgstreamer installed? If so, how?

Use Synaptic to install the other library.

---

### Post by aephex on 2008-01-09
> **dcstar said:**
> Use Synaptic to install the other library.

The older version isn't available through synaptic, be it in the standard repository, multiverse or universe.

I do have access to an RPM version of it.

Do you know if there are any problems with installing multiple versions of the same library?

---

### Post by dagnabit dang doohickey on 2008-01-09
You can download a feisty deb of libgstreamer0.8 from [packages.ubuntu.com]("http://packages.ubuntu.com/feisty/libs/libgstreamer0.8-0").

---

### Post by aephex on 2008-01-09
> **dagnabit dang doohickey said:**
> You can download a feisty deb of libgstreamer0.8 from [packages.ubuntu.com]("http://packages.ubuntu.com/feisty/libs/libgstreamer0.8-0").

I added all of the Feisty repos to synaptic and it made collecting all the different libraries and plugins real easy. I suppose now it is time to find out how much Ubuntu likes multiple versions installed. 

Thanks for the shortcut, it made this whole process alot quicker (go figure =P). 

Hopefully, you guys won't be hearing back from me.

---

