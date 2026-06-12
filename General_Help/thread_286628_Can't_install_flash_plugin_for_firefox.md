---
title: "Can't install flash plugin for firefox"
date: 2006-10-28
forum: General Help
---

### Post by x4nth3r on 2006-10-28
I tried the first method of 

sudo apt-get install flashplugin-nonfree

I got this

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package flashplugin-nonfree


And then i tried this

root@chai:/home/chai/Desktop/install_flash_player_7_linux# sudo ./flashplayer-installer


This happened

ERROR: Your architecture, \'x86_64\', is not supported by the
       Macromedia Flash Player installer.

I'm very new to Linux here so i don't know what is the problem. I followed what was said on those guides.. what is wrong here?

---

### Post by x4nth3r on 2006-10-28
Sorry i forgot to say what system i'm using, might be useful for the guys helping me out i guess?

AMD Athlon 64 3000+

Is this the cause of this problem?


ERROR: Your architecture, \'x86_64\', is not supported by the
Macromedia Flash Player installer.

---

### Post by Cable on 2006-10-28
That is indeed the cause of your problem.  Currently there is no 64 bit compatible version of Flash.

---

### Post by yatt on 2006-10-28
Two options.

1)Install Ubuntu i386

2)Write Adobe allot of emails requesting 64bit flash.

---

### Post by x4nth3r on 2006-10-28
Oh crap, that means i installed the wrong version of Ubuntu?

---

### Post by yatt on 2006-10-28
> **x4nth3r said:**
> Oh crap, that means i installed the wrong version of Ubuntu?

If you want flash, yes.

---

### Post by x4nth3r on 2006-10-28
Oh well.. I'm going to try one last method which is to copy these 2 files to the firefox plugins folder

flashplayer.xpt
libflashplayer.so

But i get and error message saying i'm not the owner of the computer, which i am.. I think it has to do with the administrative rights? How do i log on to the admin account?

---

### Post by yatt on 2006-10-28
> **x4nth3r said:**
> Oh well.. I'm going to try one last method which is to copy these 2 files to the firefox plugins folder

flashplayer.xpt
libflashplayer.so

But i get and error message saying i'm not the owner of the computer, which i am.. I think it has to do with the administrative rights? How do i log on to the admin account?

In a terminal:

sudo nautilus

If something that simple works, I think half the people on this forum will shoot themselves.

---

### Post by x4nth3r on 2006-10-28
Firefox crashed when it tried to open some flash stuff.. Damn guess i'll have to download and reinstall the whole Ubuntu thingy

---

### Post by Abhi Kalyan on 2007-03-07
Dear x4nth3r,
How many comps are you using?
If you could say that we could work out something to bring down the amount od internet bill that you ae gonna blow by repetive downloads.

---

