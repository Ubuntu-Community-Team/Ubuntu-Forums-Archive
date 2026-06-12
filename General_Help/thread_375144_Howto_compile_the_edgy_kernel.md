---
title: "Howto compile the edgy kernel?"
date: 2007-03-03
forum: General Help
---

### Post by pompos on 2007-03-03
Hey....
I just switched to Kubuntu... on my old installation I altered the speedstep-centrino.c file so that my laptop could cool off a bit.... I'd like to do the same with the edgy kernel... I followed the [instructions](https://wiki.ubuntu.com/KernelCustomBuild)... after coping (hopefully) with the heaps of config-files... I was told by the console: "make: *** No rule to make target `binary-debs'.  Stop."
I tried to compile the kernel with that command: "AUTOBUILD=1 fakeroot debian/rules binary-debs"

Later I tried it with a plain "make"... but now it gets a little wierd... my computer shutsdown during the compile process :(

---

### Post by pompos on 2007-03-04
I just found out why my laptop shuts itself down during the compile process... It gets to hot... thats new since I forced it to install Gentoo... and there it had to compile for ages...

---

### Post by pompos on 2007-03-05
I got it to work finally... a learned a lot of new things about linux and kernel compiling.... yeahhhh :D

---

