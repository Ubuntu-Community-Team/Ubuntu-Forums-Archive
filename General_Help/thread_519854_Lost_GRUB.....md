---
title: "Lost GRUB...."
date: 2007-08-07
forum: General Help
---

### Post by stuarticus on 2007-08-07
Been using Ubuntu for acouple of months, loving it and spreading the word! But trouble, Just decided that i wanted to have a proper bactrack install rather than waiting for the liveCD to load, install went well but thought that the bootloader would be as smart as the GRUB loader that came with Ubuntu and would autoconf - no such luck...
Now system boots up straight into BT through LILO, and I'm not sure how to restore GRUB or setup LILO, tried using the guides to help by following the instructions for XP dual boot - LILo.conf:
boot = /dev/sda
prompt
timeout = 20
bitmap=/boot/splash.bmp
change-rules
reset
vga = 0x317
default=Ubuntu
image = /boot/vmlinuz
root = /dev/sda3
initrd = /boot/splash.initrd
label = Backtrack
read-only
other=/dev/sda1
label=Ubuntu
table=/dev/sda

But error message on lilo -v:

Warning: LBA32 addressing assumed
Reading boot sector from /dev/sda
Using BITMAP secondary loader
Calling map_insert_data
Mapping bitmap file /boot/splash.bmp
Calling map_insert_file

Boot image: /boot/vmlinuz
Mapping RAM disk /boot/splash.initrd
Added Backtrack

Boot other: /dev/sda1, on /dev/sda, loader CHAIN
Fatal: First sector of /dev/sda1 doesn't have a valid boot signature

Now scared to reboot in case I have bricked MBR any suggestions?

---

### Post by confused57 on 2007-08-07
You need to install grub to the Ubuntu root partition for chainloading to work, you can do this with the Ubuntu live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Read the instructions in the link, but "find /boot/grub/stage1" should return something like "root (hd0,0)", so to install grub to the root partition, you would:
```
root (hd0,0)
setup (hd0,0)
quit
```

---

### Post by stuarticus on 2007-08-07
Thanks for the quick reply, sure enough now I can't find my LiveCD and will have to redownload....


  Oh well.

---

### Post by stuarticus on 2007-08-07
Thought this might be handy for anyone else with similar lilo grub problems (and no blank CDs or patience)

  In backtrack or other linux

code:
```
$ cvs -z3 -d:psnerver:anonymous@cvs.savannah.gnu.org:/sources/grub co grub
```

$ cd /root/grub

$ ./configure

$ make install grub



Then as other post (Catlett)


Code:

sudo grub

This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands

Code:

find /boot/grub/stage1

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

Code:

root (hd?,?)

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

Code:

setup (hd0)

Finally exit the grub shell
Code:

quit

That is it. Grub will be installed to the mbr.
When you reboot, you will have the grub menu at startup.

---

### Post by Fenrirwulf on 2008-03-11
Wow, thanks for this post. It is a life saver for newbies. I had to do a reinstall of XP and then lost my GRUB. I hope to have it back later tonight. :)

---

