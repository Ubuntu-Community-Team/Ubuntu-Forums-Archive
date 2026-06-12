---
title: "ubuntu will not start! help!"
date: 2007-08-24
forum: General Help
---

### Post by sigurdkaare on 2007-08-24
Error when starting ubuntu.

I made folder in /media called hdb1 and added a line in fstab so it could reconize my secondary harddisk, then I shut the system down.

But I could not start up again.

It goes to "dos"-mode ad say this:

fsck died with exit status 8

*file system check failed
a log is being saved in /var/log/fsck/checkfs if what location is writable.
Please repaier the file system manually
*A maintenance shell will now be started.
CONTROL-D will terminate this shell and resume system boot
bash: no job control in this shell
Bash: lesspipe: commend not found
bash: the: commend not found
teh program 'apt-get' is currently not installed. You can install it by typing:
apt-get install apt
bash: apt-get: command not found
bash: dircolors: command not found
the program 'apt-get' is corrently not installed. You can install it by typing:
apt-get install apt
bash: apt-get: command not found
root@sigurd:~#apt-get install apt
the program 'apt-get' is corrently not installed. You can install it by typing:
apt-get install apt
bash: apt-get: command not found

what can I do to start unbuntu again!?

and what did I do wrong?

---

### Post by apetresc on 2007-08-24
For now your first priority should be to boot back into Ubuntu again, we'll add your secondary hard drive once that's fixed.

At the GRUB menu when you boot up, there should be an entry marked "(recovery)". Boot that. Once it's booted, use "vim /etc/fstab" and remove the line you added for your second hard drive, and then save the file. Then reboot back into normal Ubuntu and post back here, and we'll figure out your hard drive problem from there :)

---

### Post by sigurdkaare on 2007-08-25
I tried, but I get the same failer. It stil not enter ubuntu. 

When I try the vim /etc/fstab after I get the failer. It says:

root@sigurd:~# vim /etc/fstab
vim /etc/fstab
the program 'vim' can be found in the following packages:
*vim
*vim-perl
*vim-ruby
*vim-full
*vim-python
*vim-tcl
*vim-gnome
*vim-tiny
*vim-gtk
Try: apt-get install <selected package>
make sure you have the 'universe' component enabled
bash: vim: command not found
root@sigurd:^#

Any clue what I should do?

> **AdrianP said:**
> For now your first priority should be to boot back into Ubuntu again, we'll add your secondary hard drive once that's fixed.

At the GRUB menu when you boot up, there should be an entry marked "(recovery)". Boot that. Once it's booted, use "vim /etc/fstab" and remove the line you added for your second hard drive, and then save the file. Then reboot back into normal Ubuntu and post back here, and we'll figure out your hard drive problem from there :)

---

### Post by merlinus on 2007-08-25
Try:

```

nano /etc/fstab

```-merlin

---

### Post by sigurdkaare on 2007-08-27
> **merlinus said:**
> Try:

```

nano /etc/fstab

```-merlin


yeah it works, I have now removed the new line I added. but how do I save the changes?

---

### Post by arildknap on 2007-08-27
I have the same problem, but I can't remember to adding a new folder anywhere... But at my computer it stands: fsck died with exit station status 4...


I am pretty new with Ubuntu, and have no idea what to do...

---

### Post by sigurdkaare on 2007-08-28
Hi please help

how do I save the changes, when I used the nano /etc/fstab command?

---

### Post by Wolki on 2007-08-28
> **sigurdkaare said:**
> Hi please help

how do I save the changes, when I used the nano /etc/fstab command?

Ctrl-o. Look at the bottom lines of nano, there are hints for the most common commands.

---

### Post by merlinus on 2007-08-28
Add sudo before the command line:

```

sudo nano /etc/fstab

```

Then you will be able to save your changes.

-merlin

---

### Post by sigurdkaare on 2007-08-28
> **merlinus said:**
> Add sudo before the command line:

```

sudo nano /etc/fstab

```

Then you will be able to save your changes.

-merlin

Fantastic! I'm back in ubuntu. You are the best!

But I still have problem with my secondary hard disk. In  this thread([http://ubuntuforums.org/showthread.php?p=3172037#post3172037](http://ubuntuforums.org/showthread.php?p=3172037#post3172037)) I got some help. But I ended up getting the starting failer. I added my hdb1 disk i the fstab  like this:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=1436962e-122e-45b8-9762-a80539f23a31 /               ext3    defaults,errors=remount-ro 0       
# /dev/hda5
UUID=dd824a41-effe-4149-86da-ebbbeb6864d0 none            swap    
]# /dev/hdb1
UUID=22406a27-4f78-4fa3-a6ee-683e30c448c3  /               ext3    defaults,errors=remount-ro 0
sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


What did I do wrong?

---

### Post by Wolki on 2007-08-28
> **sigurdkaare said:**
> 
]# /dev/hdb1
UUID=22406a27-4f78-4fa3-a6ee-683e30c448c3  /               ext3    defaults,errors=remount-ro 0 
sw 0 0


Three things: that ] doesn't belong there, the end should be "0 0" instead of "0 sw 0 0" (might be even better to use "0 1"), and you're using / to mount two things, both hda1 and hdb1. You need to mount everything in different directories, so create something like /media/hdb1 ("sudo mkdir /media/hdb1", instead of hdb1 you can name it how you want) and change the / in the line I quoted to the directory you've created. Don't forget to remove the excess ] and "sw 0". Then try again, everything should work.

Oh, and don't forget to check that you're using the correct UUID. do a "blkid" and compare the UUID on the line starting with /dev/hdb1" to the one you have there. they need to exactly match.

---

### Post by merlinus on 2007-08-28
Try rw instead of sw.  Also, are you sure the uuid is correct?

Check this with:

```

blkid

```

And yes, you do have to create a mountpoint for the partition.

-merlin

---

