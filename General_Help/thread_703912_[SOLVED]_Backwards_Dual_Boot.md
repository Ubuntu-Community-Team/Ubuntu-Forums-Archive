---
title: "[SOLVED] Backwards Dual Boot"
date: 2008-02-21
forum: General Help
---

### Post by dedtr9 on 2008-02-21
I have what seems to be the opposite problem of most people. I have Ubuntu installed on one drive, and another drive full of stuff that will be soon formatted windows XP. Once i do that, how can i set it up so that i get to choose between those. It seems that all of the tutorials on the internet are taking windows and installing Ubuntu, but i don't know which parts are relevant.

---

### Post by ace007 on 2008-02-21
You can add an entry to /boot/grub/menu.lst that will appear in the GRUB menu when you boot up.  Right now with only Ubuntu you dont see the GRUB menu, but once you add the appropriate lines to the menu.lst file, a prompt will ask you which OS to boot to when you start the computer.  

Open a terminal and type:

```

sudo gedit /boot/grub/menu.lst

```

Read the file and check out the section where it provides an example as to how to add an entry for windows.  You will have to alter the root entry to tell GRUB where to boot Windows from.

The entry MIGHT look like this:
```

title		Windows 95/98/NT/2000
root		(hd1,0)
makeactive
chainloader	+1

```

The root entry is telling GRUB to boot from device "hd1" which is actually the second hard drive, and "hd0" is the first. and after the comma is a number saying which partition.  So if Windows XP is the only partition the number is 0.  

Use the following command to find out some information about your disks.  However, the devices will be listed with alphabetical indexs.  For instance, the first drive, hd0, will be listed as hda, or the second drive, hd1 is listed as hdb. 

```

sudo fdisk -l

```

---

### Post by BLTicklemonster on 2008-02-21
stash this away somewhere where you can find it later.


[http://ubuntuforums.org/showthread.php?t=703907](http://ubuntuforums.org/showthread.php?t=703907)

---

### Post by dedtr9 on 2008-02-21
Thanks, i'll try that when i get time.

---

