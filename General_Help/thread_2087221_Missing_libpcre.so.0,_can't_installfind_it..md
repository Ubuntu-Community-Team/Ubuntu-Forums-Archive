---
title: "Missing libpcre.so.0, can't install/find it."
date: 2012-11-23
forum: General Help
---

### Post by CopaceticMan on 2012-11-23
Ubuntu 12.10 quantal
Toshiba c655d (no hardware upgrades)

FreeMat issue. I have posted to the group forums there nearing two days ago, and have not received much in the way of a solution.

So i went to freemat.sourceforge.net and downloaded freemat 4(.1-2). It was an rpm file. I googled that, and found out i had to convert it to a .deb file to run it. I did, using alien. [sudo alien -d {file name}]

Ran that .deb file and installed it via the software center. It, as far as I understand the software center, installed.

The problem is that I am missing a library.

"FreeMat: error while loading shared libraries: libpcre.so.0: cannot open shared object file: No such file or directory"

This is the error I get when I type "FreeMat" into the console.

Simple fix right? Not for me! :/ I tried installing it [sudo apt-get install libpcre(3/2/1/0)]

I already have 3 installed.

The only other thing that really comes to mind from my googling session is that I can create some reference or something, stick that reference in the specific folder for freemat and tadah, fixed.

I just don't know how to do that.

Anyway, my question is: How do I fix that error/how do I install that directory properly?

(also sorry for the background, I just felt it was obligatory)

---

### Post by ibjsb4 on 2012-11-23
Why did you start with an rpm?  FreeMat is in the software center.

[https://apps.ubuntu.com/cat/applications/precise/freemat/](https://apps.ubuntu.com/cat/applications/precise/freemat/)

---

### Post by CopaceticMan on 2012-11-23
> **ibjsb4 said:**
> Why did you start with an rpm?  FreeMat is in the software center.

[https://apps.ubuntu.com/cat/applications/precise/freemat/](https://apps.ubuntu.com/cat/applications/precise/freemat/)

Like I said, I wanted the latest version. FreeMat 4.1-2. The software center has version 4.0-5

Just me being picky. Sorry.

---

