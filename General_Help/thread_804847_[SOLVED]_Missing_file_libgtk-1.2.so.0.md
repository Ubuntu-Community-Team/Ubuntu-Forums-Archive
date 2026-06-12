---
title: "[SOLVED] Missing file libgtk-1.2.so.0"
date: 2008-05-23
forum: General Help
---

### Post by Kevbert on 2008-05-23
I'm using Ubuntu 7.10 x64 and want to run Doom3.  Originally I was going to try running it under Wine.  I read that it's possible to run in Linux without Wine and I could download doom3-linux-1.3.1.1304.x86.run from Id Software's website to run from terminal. I've copied the PAK files from my original CDs.
As soon as I run the run file with
```
sh doom3-linux-1.3.1.1304.x86.run
```
I get 'cannot find file libgtk-1.2.so.0' I've tried googling for this and get a 404 link error on the links I've tried.  It doesn't seem to be available with Synatic.
Can anyone help ?  I've also read the Wine documentation and I don't seem to get anywhere (confused).  I have Wine 0.96 on my machine.

---

### Post by phidia on 2008-05-23
> **Kevbert said:**
> I'm using Ubuntu 7.10 x64 and want to run Doom3.  Originally I was going to try running it under Wine.  I read that it's possible to run in Linux without Wine and I could download doom3-linux-1.3.1.1304.x86.run from Id Software's website to run from terminal. I've copied the PAK files from my original CDs.
As soon as I run the run file with
```
sh doom3-linux-1.3.1.1304.x86.run
```
I get 'cannot find file libgtk-1.2.so.0' I've tried googling for this and get a 404 link error on the links I've tried.  It doesn't seem to be available with Synatic.
Can anyone help ?  I've also read the Wine documentation and I don't seem to get anywhere (confused).  I have Wine 0.96 on my machine.

The key here is that you are using 64bit ubuntu. You need to have the 32 bit libraries installed. there are different ways to accomplish that. One way is installing the ia32lib package > sudo apt-get install ia32-libs but using [getlibs]("http://ubuntuforums.org/showthread.php?t=474790") will bring in the needed libraries too.

---

