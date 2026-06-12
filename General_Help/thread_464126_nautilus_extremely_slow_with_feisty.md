---
title: "nautilus extremely slow with feisty"
date: 2007-06-04
forum: General Help
---

### Post by janx on 2007-06-04
I know there are other posts on this subject but I have not been able to find a useful advice.

I have upgraded from dapper to feisty (through edgy which I have not used) and now Nautilus is **extremely** slow... for a directory with 200 items often more than 30 sec... and this does not happen only for the first access to the directory (i.e. apparently no caching mechanism enabled)... not using Beryl and Beagle disabled... This did not happen with dapper. Other apps do not appear to run slower.

Is there some setting with Nautilus that may improve the situation?

---

### Post by Crafty Kisses on 2007-06-04
> **janx said:**
> I know there are other posts on this subject but I have not been able to find a useful advice.

I have upgraded from dapper to feisty (through edgy which I have not used) and now Nautilus is **extremely** slow... for a directory with 200 items often more than 30 sec... and this does not happen only for the first access to the directory (i.e. apparently no caching mechanism enabled)... not using Beryl and Beagle disabled... This did not happen with dapper. Other apps do not appear to run slower.

Is there some setting with Nautilus that may improve the situation?

Go into console and type:
```
top
```
And see if something is eating up resources. :p

---

### Post by Crafty Kisses on 2007-06-04
Anything yet?

---

### Post by atonello on 2007-06-05
I have the same problem while browsing large folders.
"top" shows nautilus taking 99% of cpu time (Athlon 64 X2 - 2200Mhz - that jumps to full clock cycle due to the high demand).

This happens even with the "save image" dialogs in firefox when the selected folder is full of files..

edit: there are no fancy things like compiz, etc. Hard drives are 1 sata and 1 ata (Uli southbridge on Asus A8R32 m/b). Graphic card is an Ati X300 with proprietary drivers correctly installed.

---

### Post by stchman on 2007-06-05
> **janx said:**
> I know there are other posts on this subject but I have not been able to find a useful advice.

I have upgraded from dapper to feisty (through edgy which I have not used) and now Nautilus is **extremely** slow... for a directory with 200 items often more than 30 sec... and this does not happen only for the first access to the directory (i.e. apparently no caching mechanism enabled)... not using Beryl and Beagle disabled... This did not happen with dapper. Other apps do not appear to run slower.

Is there some setting with Nautilus that may improve the situation?

I recommend a clean install of Feisty.

---

### Post by atonello on 2007-06-05
Well, in my case it's already a "fresh" install of feisty; just to be sure, I've also created a new /home... unfortunately, the problem still persists

---

### Post by stchman on 2007-06-06
> **atonello said:**
> Well, in my case it's already a "fresh" install of feisty; just to be sure, I've also created a new /home... unfortunately, the problem still persists

I have installed Feisty on about 5 different machines and the only one that runs slow in the P3-450 with 256MB RAM.  I attribute the slow running to the old HW.

---

### Post by atonello on 2007-06-12
[http://ubuntuforums.org/showthread.php?t=465866&highlight=nautilus+slow](http://ubuntuforums.org/showthread.php?t=465866&highlight=nautilus+slow)

particularly at post #40 
([http://ubuntuforums.org/showpost.php?p=2809572&postcount=40):](http://ubuntuforums.org/showpost.php?p=2809572&postcount=40):)
> Nautilus is slow. Opening a large folder takes a long time. My largest ones can freeze Nautilus for half a minute, easily. It also uses a lot of RAM, which is most clearly seen when you browse around folders with many images for a while; you can get it to consume hundreds of megs this way. No, I don't use it as an image viewer. I use it as a file browser, and I happen to have many image files.

p.s. running an Athlon 64 X2 - 2200Mhz + 2 Gb ram (obsolete? ;))

---

### Post by bjtuna on 2007-06-12
I am having similar issues these past couple days. Nautilus essentially hangs (recovering a minute or so later) on simple operations like opening folders, even relatively small ones.

Edit: looks like I'm actually suffering from this bug: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/113072](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/113072)

---

