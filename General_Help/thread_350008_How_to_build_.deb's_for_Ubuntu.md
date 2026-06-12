---
title: "How to build .deb's for Ubuntu"
date: 2007-01-31
forum: General Help
---

### Post by ardchoille42 on 2007-01-31
I have 20 or so tarballs ranging from simple GTK2 themes to simple apps. I used to untar them, sudo cp the contents to the proper directories and then chmod/chown as needed. Then I learned how to do all that with shell scripts - and I realised I saved a lot of time in using scripts. For almost a year I have been wanting to create .deb packages for my tarballs to make it even easier to install them. The problem is that I have read dozens of tutorials and docs about creating .deb's and still don't understand how to do it. Some tutorials are 30 pages long with 50 or so steps, some tuts are 20 pages with less steps. No two tutorials seem to be the same and all of them want me to install a dozen or so apps - different tutorials require installing different apps.

Isn't there an app/script that sill simply ask me some questions, and if needed, ask for paths, then take that information and build a .deb package? As I see it, this could even be a script involving the following:

1. Check deps required for building/checking a .deb package
    if deps check fails, notify user and exit
2. Ask the user for a filename to be used in the final .deb filename
3. Ask the user for paths of files/folders to be included in the .deb
4. Compiling - if needed, many themes don't require compiling
5. Build the .deb package
6. Check the new .deb package for errors
7. Finish up, clean up
8. Notify the user of the result (success|errors|etc)

Isn't there a single/script that does this? It doesn't matter to me if it is GUI or CLI as I am comfy in either environment. Is building a .deb package inherently difficult? Or am I just too stupid to figure out how to do it?

---

### Post by RAOF on 2007-01-31
There are a bunch of scripts that do 4,5,6,7,8.  

It is, in general, impossible to do 1.

2 is done automatically - it depends on the name of the package, and the version of the package.

3 is done automatically - everything in the debian/packagename/ directory ends up in the root directory when you install the package (so debian/packagename/usr/bin/foo ends up at /usr/bin/foo).

There is the **checkinstall** package, which automatically makes crappy debs out of programs.  But actually, I tend to just build proper debian packages.  It's not **too** hard after you get used to it.

---

### Post by phossal on 2007-01-31
RAOF:

Building "proper" debs is something I would like to understand better. Is there a *source* for information you can point me to? Something you recommend?

---

### Post by Jucato on 2007-01-31
Ubuntu comes with a packaging guide in every default installation. You can also view the guide online:

[https://help.ubuntu.com/6.10/ubuntu/packagingguide/C/index.html](https://help.ubuntu.com/6.10/ubuntu/packagingguide/C/index.html)

This will guide you in properly building packages that will install and run well on Ubuntu.

Note: While checkinstall is an easy way to make a .deb package from source code, it's not a recommend method if you want to properly build an Ubuntu .deb package.

---

### Post by RAOF on 2007-01-31
The Ubuntu Packaging Guide is pretty good.  You can find it on wiki.ubuntu.com, or in System->Help.

Also, CDBS is excellent.  It makes the debian/rules about 4 lines.  A quick google search will pull up the CDBS manual.

---

### Post by ardchoille42 on 2007-01-31
I found the first line at [https://help.ubuntu.com/6.10/ubuntu/packagingguide/C/basic-chap.html](https://help.ubuntu.com/6.10/ubuntu/packagingguide/C/basic-chap.html) to be the source of my confusion.

From the [https://help.ubuntu.com/6.10/ubuntu/packagingguide/C/basic-chap.html](https://help.ubuntu.com/6.10/ubuntu/packagingguide/C/basic-chap.html) site:

"Two of the problems that many novice packagers face are that there are multiple ways of packaging, and there is more than one tool to do the job."

I'll have to read more about this.

---

### Post by ardchoille42 on 2007-01-31
> **Jucato said:**
> Ubuntu comes with a packaging guide in every default installation. You can also view the guide online:

[https://help.ubuntu.com/6.10/ubuntu/packagingguide/C/index.html](https://help.ubuntu.com/6.10/ubuntu/packagingguide/C/index.html)

This will guide you in properly building packages that will install and run well on Ubuntu.

Note: While checkinstall is an easy way to make a .deb package from source code, it's not a recommend method if you want to properly build an Ubuntu .deb package.

Thank you very much. This guide seems to be what I need.

---

