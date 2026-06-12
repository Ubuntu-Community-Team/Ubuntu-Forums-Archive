---
title: "Boot problem (I need help fast)"
date: 2008-04-17
forum: General Help
---

### Post by Punkristo on 2008-04-17
Last time I turned off the computer it didnt wanted to turn off so I had to press the power button until it turned off. Now Im getting this error and I cant get into Ubuntu:

> *An automatic file system check (fsck) of the root filesystem failed.
the fsck should be performed in  maintenance mode with the root filesystem in read-only mode.

*The root filesystem is currently mounted in read-only mode.
A maintenance shell will now be started.
After performing system maintenance, press CONTROL-D to terminate the maintenance shel and restart the system.
Give root password for maintenance.
--------------------------------
After I put the root password this is what I get:

> bash: no job control in this shell
bash: lesspipe: command not found
bash: Command: command not found
bash: The: command not found
bash: dircolors: command not found
bash: Command: command not found
bash: The: command not found
------------------------

And this is what I get in the /etc/fstab

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=7e997cd3-f1b9-48c8-84e6-b6c0191a2fdd /               ext2    defaults,errors=remount-ro 0       1
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


---

### Post by danwood76 on 2008-04-17
When  it throws you into the maintenence shell run fsck:

```

fsck

```

This will check all partitions in your fstab (you only have 1 anyway)

it looks like you have some currupt data and its not liking it.
fsck should be able to fix it.

---

### Post by Punkristo on 2008-04-17
Is does it automaricly but it comes up with the error I posted above. It did this too me before and I just reinstalled the Ubuntu but I want to fix it this time cause it took me a while to set it up correctly and I have some downloads on pause that I need to finish downloading.

---

### Post by Trail on 2008-04-17
> 
bash: no job control in this shell
bash: lesspipe: command not found
bash: Command: command not found
bash: The: command not found
bash: dircolors: command not found
bash: Command: command not found
bash: The: command not found 

I am getting this to. I don't think you should worry about it, sounds like it's loading a dumb terminal and not handling some exports properly.

---

### Post by daengbo on 2008-04-17
type

fsck -t ext2 -y /dev/sda1

By the way, why are you using ext2 instead of a journailing filesystem?

---

### Post by Trail on 2008-04-17
You can undelete on ext2? :)

---

### Post by Punkristo on 2008-04-17
OK I got it working doing this:

> sudo umount /dev/sda1
sudo fsck -y /dev/sda1
sudo init 6

But now my resolution isnt working. I have a 17" screen and the resolution should be 1280 x 800 but when I select it on widescreen the screen looks really bad.

---

### Post by Punkristo on 2008-04-17
Nevermind, I got it working completely now. Thanks for the help.

---

