---
title: "need to compile a program for the first time"
date: 2008-02-26
forum: General Help
---

### Post by gamelord12 on 2008-02-26
I need to use the CVS feature in Eclipse, an IDE I'm using to program Java projects for my computer science class.  Unfortunately, CVS doesn't work in the 3.2 version of Eclipse in Ubuntu's repositories, so I'm going to need to compile the new version, Europa.  The binaries they offer are only in .rpm format.  So...how do I go about compiling this thing?  Also, just as a side question, why is it that a program compiled for Red Hat won't work on Debian-based operating systems?  What makes them different?

---

### Post by Crafty Kisses on 2008-02-26
> **gamelord12 said:**
> I need to use the CVS feature in Eclipse, an IDE I'm using to program Java projects for my computer science class.  Unfortunately, CVS doesn't work in the 3.2 version of Eclipse in Ubuntu's repositories, so I'm going to need to compile the new version, Europa.  The binaries they offer are only in .rpm format.  So...how do I go about compiling this thing?  Also, just as a side question, why is it that a program compiled for Red Hat won't work on Debian-based operating systems?  What makes them different?

First, you might need build-essentials. :)

---

### Post by jken146 on 2008-02-26
[http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually](http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually)

---

### Post by oldos2er on 2008-02-26
There's a program called "alien" that can convert *rpms to *debs, but it isn't always successful. Still, I don't think it would hurt to try it. You can install it through Synaptic, or at the terminal with "sudo aptitude install alien". Then you run alien against the *rpm file, "alien [filename.rpm]", and if you're lucky it'll build a usable *deb file for you.

---

### Post by SOULRiDER on 2008-02-26
> **gamelord12 said:**
> I need to use the CVS feature in Eclipse, an IDE I'm using to program Java projects for my computer science class.  Unfortunately, CVS doesn't work in the 3.2 version of Eclipse in Ubuntu's repositories, so I'm going to need to compile the new version, Europa.  The binaries they offer are only in .rpm format.  So...how do I go about compiling this thing?  Also, just as a side question, why is it that a program compiled for Red Hat won't work on Debian-based operating systems?  What makes them different?

You can solve it easily, get easy eclipse.

[http://easyeclipse.org](http://easyeclipse.org)

Problem solved :P

---

### Post by bodhi.zazen on 2008-02-26
:lolflag:

To answer the question :

```
sudo aptitude update
	sudo aptitude install build-essential checkinstall
```

	download the source code, unpackage.

	Open a terminal, cd into the package directory.

	Now, 

	[list=number][*]Read the README and/or INSTALL file.```
gedit README
```
	[*]List the options: ```
./configure --help | less
```You may scroll through the output with up and down arrows, page up, page down ... 
	Type q to exit less.


	[*]./configure --prefix=/usr
	[*]make
	[*]sudo checkinstall -D[/list]


======

You should use Alien ONLY as a LAST RESORT, can cause breakage :(
	[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

---

