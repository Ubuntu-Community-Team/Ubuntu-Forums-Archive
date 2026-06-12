---
title: "Computer will not boot after Hardy install (Far worse than it sounds)"
date: 2008-04-27
forum: General Help
---

### Post by hello_emo_boy on 2008-04-27
Ok, so I just upgraded to Hardy via the update manager and now something weird has really happened.

My computer won't boot.

I don't mean like it won't load into ubuntu, I mean it will turn on, then get to the BIOS and that's where it ends. It was working fine until the update and now, nothing.

Any suggestions? I've tried to get into the boot menu and it won't even get that far.

Thanks

---

### Post by quixote on 2008-04-27
I've had a problem that sounds similar several times.  If it's the same thing, all that's happened is that the system's current numbering of your boot drive and grub's no longer match.  It's a stupid and heart-stopping bug, but, like it says in the Hitchhiker's Guide to the Galaxy: Don't Panic!

This link [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) explains how to do it.  It's under "recovering grub manually" toward the bottom of the page. (They've changed that page since the last time I looked, and that's a different method than the one I've used.)

Briefly, you need to: 1) know which partition contains your ubuntu boot directory, and 2) edit /boot/grub/menu.lst to reflect that.

You can boot from a liveCD.  Open a terminal window and type
> $sudo fdisk -l
That will give you a list of all the partitions on your system.  Maybe you can tell just by its size and linux formatting which is the one you need.  Alternatively, you can use the regular file manager to mount various drives you have one by one until you see one that has a bunch of files like vmlinuz-2.6.24-12-generic and initrd-2.6.24-12-generic in either /boot or /.  Remember its size, go look at your fdisk list again, and figure out which one of the linux partitions is your boot partition.  Let's say it's /dev/hda7

Okay.  That was the hard part.  You're still running off the liveCD.  With your ordinary linux boot partition mounted, you need to edit /boot/grub/menu.lst.  Let's say that partition is mounted at /media/linux.
> $sudo gedit /media/linux/boot/grub/menu.lst
That uses a simple text editor to access the file.  Towards the end of it, you'll see a series of entries, one of which (the first, probably) says something like:
> title  Ubuntu, 2.6.24-12 
root   (hd0,2)

plus a few other lines for each entry, but they don't concern us.  Grub numbers the drives and partitions in its own way (of course :? ) starting from zero.  hd0 means the first physical hard drive.  If you have only one in your machine, then you need hd0.  The second number is the boot partition.  If it was /dev/hda7, then the second number would be 6:
> root   (hd0,6) 

If you're having the same problem as me, then you'll see that the number says something like "root (hd0,8 )" instead.

Once you've fixed the number, save, unmount the partitions, shutdown, and reboot.  If you have the number right, it'll find it.  If not, you get to do the whole thing again ;)

Once you have it right, you'll want to change all the menu.lst entries to the correct partitions.  It usually incorrectly increments them all, for some reason.

Hope this helps!

---

