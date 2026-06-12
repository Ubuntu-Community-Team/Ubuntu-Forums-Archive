---
title: "How to save my Ubuntu files and uninstall and reinstall"
date: 2013-04-28
forum: General Help
---

### Post by WUTANG4EVER on 2013-04-28
Can someone please tell me how to save my files i have on Ubuntu or how i can copy my hard drive then uninstall then reinstall Ubuntu and put my saved files back on. Im stuck on login and it does a bootloop.

---

### Post by Impavidus on 2013-04-28
Boot from a live disk, copy your files to an external drive and savely remove the drive. After reinstalling, copy them back.

---

### Post by WUTANG4EVER on 2013-04-28
O.k  so i take it boot with my disk i installed with and when i boot the cd is it pritty simple to figure out how to copy my files or do i need to use terminal

---

### Post by Bashing-om on 2013-04-28
WUTANG4EVER; Hi !

Yeah real simple to use the GUI file manager -in two instances - to copy files from the install to a thumb drive; from the liveCD.
Only you know what files you have and where they are located, however if you are using Fire Fox and want to save your profile and bookmarks (?), See Fire Fox's help pages for instruction.
[INDENT=2]
just try'n to help

[/INDENT]

---

### Post by WUTANG4EVER on 2013-04-28
Thanks alot last time i just deleted everything and reinstalled and it took me a week nonstop getting back my files thanks.

---

### Post by Bashing-om on 2013-04-28
WUTANG4EVER;

If you have lots of files to save and mostly in your home directory, you might consider "rsync" to copy the entire "/home" directory, I have never had an occasion to use this method, but I have seen it employed by several on this forum. A search on this form on "rsync" and/or
"copy /home" might prove productive.
see:
```
man rsync
```[INDENT]
just a thought

[/INDENT]

---

### Post by Redalien0304 on 2013-04-28
Use Grsync the Gui of rsync it is on Ubuntu software cednter

---

### Post by WUTANG4EVER on 2013-04-29
Thanks 4 all the replies. I just reinstalled ubuntu 12.04 and choose to run along side of previous install of Ubuntu 12.04 and I can grab my old files inside my new home folder under devices /60g file system. I figure take the easy way out till i learn a little more about ubuntu

---

### Post by 3rdalbum on 2013-04-29
It's a pity I didn't reply quicker. If you use the Something Else partitioning screen to select your existing Ubuntu partition as the install target WITHOUT formatting it, the installer will do a clean install but preserving your files.

Also, a login loop is usually caused by not having read/write access to /~.Xauthority.

---

### Post by Bashing-om on 2013-04-30
WUTANG4EVER;

Hey, Whatever works for you. This is ubuntu; numerous roads to one end. With good backups and a liveCD, there ain't no situation too tough.[INDENT=2]Happy ubuntu'n

[/INDENT]

---

