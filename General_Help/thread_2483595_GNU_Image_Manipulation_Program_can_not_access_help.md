---
title: "GNU Image Manipulation Program can not access help manual"
date: 2023-02-03
forum: General Help
---

### Post by BBQdave on 2023-02-03
Installed GNU Image Manipulation Program with Ubuntu Software (snap) and loaded gimp-help-en, the user manual.
The manual installed in /usr/share/doc/gimp-help-en

When I try to access the manual through GNU-IMP Help, the on-line manual is blocked by AppArmor.
When I check on **Edit > Preferences > Interface > Help System**, message says *The user manual is not installed locally*. Therefore I can not access the installed manual.

Thoughts on how to resolve this? Thanks :)

---

### Post by ajgreeny on 2023-02-04
I wonder if this is yet another of the restrictions related to a snap version of GIMP or maybe firefox?

I have no snaps on any of my systems so can not check this in any way but I do run GIMP installed using the normal .deb package from the repos and I also have the English help installed which opens in my Firefox, a non snap version..
Are you aware that even when installed locally on your system the help runs in your default web-browser and if that is the now default snap Firefox, it may not be able to access the help.

I don't know how or even if it's possible to overcome this so will let other users help with these details.

---

### Post by sudodus on 2023-02-04
I use gimp installed via apt (the classical way) in Ubuntu 22.04.x LTS and the help system works for me.

So, when you have the snap version of gimp and access to the help system is important, I suggest that you remove the snap version and install the apt version (which might be older than the snap version, but good enough for me). I think that we are talking about help pages that need access via the internet, so if the computer has no access to the internet, there will be problems also with the apt version of gimp.

---

### Post by ajgreeny on 2023-02-04
Further to my post #2 the GIMP help is installed locally to your drive if you use the normal repository version of GIMP and does not need Internet access; it reads those help files from your disk but it does now open the help in your default browser  not in the dialogue window that had been used in the past.

Of course, whether the default Firefox, a snap, can now read and open those help files which are not in your user's home, is another question which I can not answer fully.

---

### Post by mIk3_08 on 2023-02-04
Mine too, I also have my Gimp in 22.04 LTS. Gimp help works smoothly fine. I haven't encounter any error so far. 
```
Package: gimp
Version: 2.10.30-1build1
Priority: optional
Section: universe/graphics
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian GNOME Maintainers <pkg-gnome-maintainers@lists.alioth.debian.org>
Installed-Size: 21.1 MB
```
Regards and cheers.

---

### Post by BBQdave on 2023-02-04
Thanks for all the information, this verifies my thoughts. Gimp and FireForx are *snap* packages on my system, hence they are sandbox and I believe have limited access to the system.
As *snap* develops, perhaps the manuals will drop in the snap folder.

My work around is to have the Gimp on-line manual bookmarked in my browser :) Easy enough.
Thanks again all, for your thoughts and set up information.

---

### Post by ajgreeny on 2023-02-04
Great! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction, even if this is not perhaps a complete solution.

It is a great help to other users searching the forum.

---

### Post by monkeybrain20122 on 2023-02-04
It means you also cannot install some addons such as the darktable addon. I compile gimp from source so I am up to date and not subjected to silly restrictions. It is quite easy once you gathered the dependencies, though the first time can be time consuming since you have to compile some of those from source as well (system versions might be too old)

This is the kind of things that turn people away from Ubuntu. New users have no idea about snap or deb and just get the impression that Ubuntu apps are crippled and think that is the case for Linux in general and go back to Windows or Mac.

P.S I think gimp also has an appimage from upstream (snap is not from gimp, but downstream packagers) and I think that one does not have problem with addons though I haven't used that.

---

