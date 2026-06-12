---
title: "Problem during &quot;Installing Base System&quot;"
date: 2007-06-24
forum: General Help
---

### Post by jal4568 on 2007-06-24
Hello, I looked around to see if anyone also had this problem. If the post is redundant, I apologize. I'm very new to this. 

I downloaded Wubi last night and successfully got through the re-boot phase no problem. However, when I get to "Installing Base System", it gets stuck at 75% ("Storing language.."). The first time, I left it overnight and after 8hrs there was no change. 

I attempted to re-install Wubi with a smaller partition size but there was no change (this time I only waited 2hrs). 

Attached is a screen shot of the log from when I get stuck. 

My system info:
OS: Windows XP SP2
HD: WDC (NTFS)
Free Space: 17GB
Partition Set-up: 5GB (2nd time), 10GB (1st Time)

Any help would be greatly appreciated. I really want to give Ubuntu a try.

---

### Post by ago on 2007-06-24
Looks like you keep running out of memory, but I need more info to understand why

---

### Post by abn91c on 2007-06-24
did you defrag windows?

---

### Post by jal4568 on 2007-06-25
I defragmented my HD before I attempted to install Wubi. Also, there's 128MB of RAM on my computer. 

I tried a 3rd time to install Wubi yesterday with the partition set at 4GB but I had the same problem. Looking at the log, it was getting stuck forming the swap disk. It tries several times, runs out of memory and then stops.

---

### Post by ago on 2007-06-25
> **jal4568 said:**
> I defragmented my HD before I attempted to install Wubi. Also, there's 128MB of RAM on my computer. 

I tried a 3rd time to install Wubi yesterday with the partition set at 4GB but I had the same problem. Looking at the log, it was getting stuck forming the swap disk. It tries several times, runs out of memory and then stops.

You ay try to disable the swap disk by renaming swap.virtual.disk before rebooting, but with only 128MB that might create problems later on. 

If even Xubuntu proves to heavy, What you might also do is edit preseed.cfg so that it does NOT install the ubuntu-desktop package. Then manually install IceWM or OpenBox and GDM.

---

### Post by jal4568 on 2007-06-25
Ok, I tried to install Xubuntu. This time it got past the "Installing Base System" but still ran out of memory during a process called '/sbin/debian-installer'. 

It sounds like editing preseed.cfg is my next option. I was looking at it and, is this the portion that I change? From red to green?
> ## PACKAGE SELECTION
[COLOR="Red"]tasksel tasksel/first multiselect ubuntu-desktop[/COLOR]
[COLOR="Green"]#tasksel tasksel/first multiselect ubuntu-standard[/COLOR]
#tasksel tasksel/first multiselect ubuntu-standard, lamp-server
#tasksel tasksel/first multiselect ubuntu-standard, kubuntu-desktop
#d-i pkgsel/include string openssh-server build-essential

---

### Post by ago on 2007-06-26
#tasksel tasksel/first multiselect ubuntu-desktop
tasksel tasksel/first multiselect ubuntu-standard

This will give you a simple prompt, but from there you can install the bits and pieces that you want (assuming that you have internet working).

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install fluxbox gdm

---

### Post by ArtDeco on 2007-07-12
I have a similar issue with a 128 mb laptop hanging at language-en-base. I don't think 128mb is really enough memory for the debian installer, even though it is enough to run Ubuntu. I ordered another 256mb memory stick - it can't hurt and ram is cheap today.

---

### Post by sethm on 2007-08-03
I'm stuck at the exact same spot: 75%.  My screen doesn't have lots of text, just a blue background with a red status bar going across.  Any idea what I should do?  CtrlAltDel doesn't even work, it looks like I'll have to do a hard reboot.  Then what?

I'm also a noob.

---

### Post by ago on 2007-08-06
You can use alt+f4 to see more detailed progress report or use alt+f2 for a shell.

But you normally need 256MB+

---

