---
title: "Need help with making a Debian package from source code"
date: 2005-05-03
forum: General Help
---

### Post by anton123 on 2005-05-03
Hello,

Since I am very new to Linux, I have some difficulties. I downloaded GStreamripper as source code in a tar.gz archive. I extracted it and ran as root, two commands, "./configure" and "make" to compile and link the objects. Now, I want to make a Debian package. My question is how to do it. Do I use "debhelper" or which utility? When making the package, should I refer to the directory where the changes took place after the two commands were run or to the "src" directory withing the directory to which I extracted the archive? I would really appreciate if someone can direct me through the steps to make the Debian package.

Thank you

---

### Post by cutOff on 2005-05-03
The application that you need is called **checkinstall**.

```
$ sudo apt-get install checkinstall
``` 
Once you have it, you will be able to make deb packages.

```
$ man checkinstall
```

---

### Post by az on 2005-05-03
Checkinstall is not a reccommended way to make a deb package.  It may work for you, but I would not redistribute it, nor would I wonder if my system ever got borked.

Mind you, checkinstall may be what you want if you do not want to get your hands dirty.

Google for the debian new maintainers' guide and the debian reference.  there are also tutorials for makeing packages with debhelper.  You can also do it all by hand and not use debhelper (there is a debian-women article about this -  -use google for it...)

---

### Post by philipacamaniac on 2005-05-12
I have checkinstall working, sort of, on a Kubuntu install. It wasn't working at first, for KDE programs, and I realized that it was installing the packages into /usr/local/kde/...  where as Kubuntu omits the /kde directory in both /usr and /usr/local. To fix the problem, I copied everything I had already installed in /usr/local/kde over to /usr/local, and then I made a symbolic link /usr/local/kde that pointed to /usr/local. A quick, and very dirty fix, but checkinstall packages work now.

Of course, these packages I'm making for myself won't work on other systems, unless the other system has that symbolic link in place.

---

