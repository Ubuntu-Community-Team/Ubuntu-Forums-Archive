---
title: "please help me install tomoe handwriting recognition software"
date: 2007-11-08
forum: General Help
---

### Post by cwmccabe on 2007-11-08
I'm struggling to install a program called tomoe that will allow me to draw Chinese* characters on the computer (I'm on Ubuntu Feisty).  However, I'm a bit of a newbie and don't know what steps to follow.  This program is not in the standard repositories.

The program looks like this: [http://www.geocities.jp/ep3797/tomoe_01.html](http://www.geocities.jp/ep3797/tomoe_01.html)

And it should apparently integrate with scim, using scim-tomoe.  

I have downloaded the following files from Sourceforge, but I don't know which ones to install or how to install them (I'm assuming tomoe and scim-tomoe at least):

[LIST]
[*][tomoe-0.6.0.tar.gz]("http://sourceforge.net/project/showfiles.php?group_id=193138&package_id=227469&release_id=519559")
[*][scim-tomoe-0.6.0.tar.gz]("http://sourceforge.net/project/showfiles.php?group_id=193138&package_id=237021&release_id=519563")
[*][uim-tomoe-gtk-0.6.0.tar.gz]("http://sourceforge.net/project/showfiles.php?group_id=193138&package_id=237020&release_id=519562")
[*][tomoe-gtk-0.6.0.tar.gz]("http://sourceforge.net/project/showfiles.php?group_id=193138&package_id=237019&release_id=519560")
[/LIST]

How can I get this installed?  (I already have scim installed and working.)

* The original version of the program was for writing Japanese characters, but it appears that as of 0.6.0 it will also write Chinese.

---

### Post by ChameleonDave on 2008-05-21
Forget compiling from source.  Just add these repos to /etc/apt/sources.list:

```

## Japanese repositories
deb http://archive.ubuntulinux.jp/ubuntu-ja hardy/
#deb-src http://archive.ubuntulinux.jp/ubuntu-ja hardy/

deb http://archive.ubuntulinux.jp/ubuntu-ja hardy-ja/
#deb-src http://archive.ubuntulinux.jp/ubuntu-ja hardy-ja/

```

---

### Post by Zorael on 2008-06-21
> **ChameleonDave said:**
> Forget compiling from source.  Just add these repos to /etc/apt/sources.list:

```

## Japanese repositories
deb http://archive.ubuntulinux.jp/ubuntu-ja hardy/
#deb-src http://archive.ubuntulinux.jp/ubuntu-ja hardy/

deb http://archive.ubuntulinux.jp/ubuntu-ja hardy-ja/
#deb-src http://archive.ubuntulinux.jp/ubuntu-ja hardy-ja/

```
Those repos are all well and good unless you're not running an i386 system.

Know of any similar with -all or -amd64 packages?

---

### Post by ChameleonDave on 2008-06-28
> **Zorael said:**
> Those repos are all well and good unless you're not running an i386 system.

Know of any similar with -all or -amd64 packages?

No, sorry.

OK, let's compile from scratch then.  It is tricky.

First of all, I can tell you that I have not managed to get tomoe working with UIM, due to unresolvable dependency issues.  So, forget the uim-tomoe-gtk package.  Instead, I have it working via SCIM.

These are the tomoe packages that I have installed on my system:
```
libtomoe0  libtomoe-gtk0  tomoe-dic  tomoe-doc  tomoe-gtk-common  tomoe-gtk-l10n  tomoe-l10n  scim-tomoe
```

They may not all be strictly necessary, but I can tell you that none others will be needed because that's all I have and it works for me.

If you look on these fora, or on the Ubuntu documentation wiki, or on Google, you will fiond guides to installing software from source code.  Follow them.

However, I can give you this advice.  Extract the code from its tarball, go into the directory with the "cd" command, then type "ls" to list the contents.  Read any README files or suchlike.  Type "./configure" to prepare the code for your system, then "make" to compile the code into a program.  Study the output of these commands for signs that you are missing dependencies.  Install those dependencies in Synaptic.  If they are not there, then download the source code for those dependencies and install them first.

Also make sure you have some good-quality regular-style fonts for these characters.  Once you get tomoe working, change the default font (which is small, ugly and hard to read).

---

### Post by Zorael on 2008-06-28
I went to the tomoe homepage ([http://tomoe.sourceforge.jp/cgi-bin/en/blog/index.rb](http://tomoe.sourceforge.jp/cgi-bin/en/blog/index.rb)) and downloaded the source. However, when trying to compile it stops at one point and just sucks in all my available memory; 2gb ram and 3gb swap goes down the drain in a few minutes. At this point there's so much swapping going on that the computer gets completely unresponsive.

Any ideas? :<

---

