---
title: "source packages"
date: 2019-12-14
forum: General Help
---

### Post by Skaperen on 2019-12-14
i read that i must "enable sources" to install source packages.  how is that done?

also, when source is installed, where does it go?  is there a standardized way to build a binary web from that with my own patches?

---

### Post by deadflowr on 2019-12-15
Source repositories are those pesky deb-src source entries in your /etc/apt/sources.list file.
You need to manually edit the entries yourself from cli.

They download the source package into whatever working directory you current are in.
```
apt source <package-name>
```
will download the source to the current working directory
you can then cd into the source directory and start working from there.

I guess the standard way is to apply the patches then build the package.
Some prerequisites are needed see:
[https://help.ubuntu.com/community/CompilingSoftware]("https://help.ubuntu.com/community/CompilingSoftware")
reference for applying patches:
[https://unix.stackexchange.com/questions/96197/how-do-i-apply-software-patches]("https://unix.stackexchange.com/questions/96197/how-do-i-apply-software-patches")

---

### Post by guiverc on 2019-12-15
In `Software Sources` I have a 'check-box' underneath "Canonical-Supported..", "Community..", "Prop..", Software restr" there titled "Source code".   It could be though I've manually added them earlier, or it's an option given I'm on a development release (20.04).

I'd `vim /etc/apt/sources.list` myself as I find it faster than GUI...  A line using my mirror is
```
deb-src [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) focal main multiverse universe restricted
```

---

### Post by Skaperen on 2019-12-15
i am unfamiliar with what you refer to as "Software Sources" since i do CLI all the time and almost no GUI.  i am familiar with building software.  getting a .deb package is what i don't know about, yet.  my goal is to fix a bug in a package.  i'll need to make the patch myself.  and once i have it working, i'll also need to package the source.

---

### Post by norobro on 2019-12-15
[FONT=arial][SIZE=2]A caveat: I have not done this on Ubuntu, but have several times on Debian.
[/SIZE][/FONT]
[LIST]
[*][FONT=arial][SIZE=2]As @deadflower stated, uncomment the deb-src line in your sources.list file or enter a line for the source repository for the package you are patching. An example line from  my disco file is: ```
# deb-src http://us.archive.ubuntu.com/ubuntu/ disco universe
```[/SIZE][/FONT]
[*][FONT=arial][SIZE=2]execute: apt-get update[/SIZE][/FONT]
[*][FONT=arial][SIZE=2]execute: apt-get source <pkg name>[/SIZE][/FONT]
[*][FONT=arial][SIZE=2]edit, compile and test.[/SIZE][/FONT]
[*][FONT=arial][SIZE=2]run: dpkg-buildpackage  - see the man page[/SIZE][/FONT]
[/LIST]
[FONT=arial][SIZE=2]Debian recommends commenting out the deb-src line when you are finished downloading to reduce the load on the servers. I assume this applies to Ubuntu also.

HTH[/SIZE][/FONT]

---

### Post by Skaperen on 2019-12-15
it probably does.  that lets them avoid scaling up the source servers.

---

### Post by Skaperen on 2019-12-15
perhaps what i need to learn is how to build a binary package and a source package of my own for both a C program that needs to be compiled and a Python program that doesn't need to be compiled.  ultimately a Makefile for the C program would have 2 targets "deb" and "srcdeb" (or is that "src-deb"?).  maybe the Python program needs the same.  if these steps involve special features of the program, that should always be included in the source.

---

### Post by norobro on 2019-12-15
Sorry, I misunderstood. I thought you wanted to patch an existing package.

The Debian wiki has a couple of pages on packaging:
[https://wiki.debian.org/HowToPackageForDebian](https://wiki.debian.org/HowToPackageForDebian)
[https://wiki.debian.org/Packaging/Intro?action=show&redirect=IntroDebianPackaging](https://wiki.debian.org/Packaging/Intro?action=show&redirect=IntroDebianPackaging)

Also, this site has a simple binary package example: [https://linuxconfig.org/easy-way-to-create-a-debian-package-and-local-package-repository](https://linuxconfig.org/easy-way-to-create-a-debian-package-and-local-package-repository)

---

### Post by Skaperen on 2019-12-16
it is an existing package called [COLOR=#006400][FONT=courier new]**dclock**[/FONT][/COLOR] that displays time in a wrong way.  sometimes it skips 1 second.  sometimes it does the skip in 1 second and sometimes in 2 seconds.  sometimes it displays the same time for 2 seconds instead of just one.  i've seen this exact problem before and i think i know what the cause in this program is.  if i am correct about that, what i think will fix it might work right.  so, i want to try it.  if my fix works, i want to send my source patch to the author and Canonical.  i want to also make a .deb file and send that to Canonical

---

