---
title: "Help-Trying to load a program from CD?"
date: 2008-05-20
forum: General Help
---

### Post by Return Privacy on 2008-05-20
Hi all!
I've finally decided to rid my house of MS! I installed Ubuntu 7.10 desktop on computer. I put in a CD and tried to load a program from it, and got the message "you need root privilages". I opened terminal (that's scary for me!) and typed in "sudo -s", and it asked for pw, I gave it, and then the line read "root@server001". So I thought that did it. But I get the same "you need root privilages" when I double click on the CD's program? The CD is showing on the desktop fine, and I can see what's on it, but it won't let me load a program from it. This is probably very simple, but it is frustrating to me.
Please understand that I am COMPLETELY new at linux. I think I am going to really like using it, once I learn how to use it properly.
Thanks in advance
-

---

### Post by Lod on 2008-05-20
Entering your root password in a terminal only gives you root privileges in that terminal (and the programs you start from it), not for your entire system.
You might try entering this in the terminal
```
sudo nautilus
``` this will give you a nautilus windows with root priviliges. Browse to the cd and try again.

---

### Post by Return Privacy on 2008-05-20
Hi LOD,
I tried what you said and it opened a file browser box? I didn't bother with it, and I tried to install the program again from the CD and got the exact same message "you need root privilages". 
I'm  stumped?

---

### Post by Return Privacy on 2008-05-20
Hi again LOD,
I did the sudo natilus again, and in that browser, I went to the cdrom and tried to install the program from the CD, called 3dm2. It trys to install and I get the message

xterm: can't execvp ./packages/3dm2/linux/install.3dm: no such file or directory
root@server001:/cdrom#

the CD isn't spinning, and if I hit the eject button, it then gives the message can't eject because an application is using it.
???

---

### Post by thecowking on 2008-05-20
> **Return Privacy said:**
> Hi LOD,
I tried what you said and it opened a file browser box? I didn't bother with it, and I tried to install the program again from the CD and got the exact same message "you need root privilages". 
I'm  stumped?

That file browser window is where you can navigate to the CD and run programs from. When you try and open the program from outside that window, Ubuntu says "this action is performed at user privileges, but it wants to do things that need root privileges. No, can't let that happen, could be a bad program." This is why you need to use that file browser, which has been opened with sudo, this is an instance of the program with superuser(root) privileges that can run these programs you need to run. :)

Play around with that a while and you should get what you need to get done, done. After a while though I'm sure you'll see that the terminal isn't so scary and actually it's faster to run a program through that than the file browser windows! :)

---

### Post by Lod on 2008-05-20
> **Return Privacy said:**
> Hi again LOD,
I did the sudo natilus again, and in that browser, I went to the cdrom and tried to install the program from the CD, called 3dm2. It trys to install and I get the message

xterm: can't execvp ./packages/3dm2/linux/install.3dm: no such file or directory
root@server001:/cdrom#

the CD isn't spinning, and if I hit the eject button, it then gives the message can't eject because an application is using it.
???You probably can't eject the cd because the nautilus browser is still on it?

Concerning the install: is there a file called install(.txt) or readme(.txt)? It seems more some installation problem of 3dm2 instead of a privilige error.

---

