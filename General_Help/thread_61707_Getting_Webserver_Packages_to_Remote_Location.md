---
title: "Getting Webserver Packages to Remote Location"
date: 2005-09-01
forum: General Help
---

### Post by Saibei on 2005-09-01
Hey all,

I need to get a set of packages over to a remote location without an internet connection. I've been trying for about 3 days so far, and each time run into more unsolved dependencies.

What would be the best way to download a package and all the packages required to run it?

Specifically, I'm looking for apache2, php4, phpmyadmin, webmin, and mysql packages.

---

### Post by plb on 2005-09-01
[QUOTE=][/QUOTE]
 well you could always just download all the packages you need and burn them?

---

### Post by Saibei on 2005-09-02
[QUOTE=plb]well you could always just download all the packages you need and burn them?[/QUOTE]
 That's the problem. Dependencies upon dependencies. I probably downloaded around 120 packages - **manually** - and there are still unresolved dependencies.

Like I said, I'm wondering if there was a program that would map these dependencies and allow me to download them all in one go, rather than having to search through [http://packages.ubuntu.com](http://packages.ubuntu.com) for hours.

---

### Post by s_p_a_r_k_y on 2005-09-02
if your on a machine brand new machine or live cd (i think) if you type from the command line
```
 sudo apt-get install package
```

it will mention all the packages it will upgrade, install, replace and remove. save the output from it. You can also have it install the packages (it will download all of them which you can burn to a cd.

---

