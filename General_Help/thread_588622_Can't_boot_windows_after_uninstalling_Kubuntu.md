---
title: "Can't boot windows after uninstalling Kubuntu"
date: 2007-10-23
forum: General Help
---

### Post by Sup3rkirby on 2007-10-23
Please someone help me here.  I honestly haven't gotten a single reply, none the less some help on any of my recent topics.

Ok, so I wanted to install Kubuntu as a dual boot on XP.  Everything seemed to work, and I had Kubuntu running and when I booted I had a DOS screen that asked for the OS I wanted to boot.  Everything was great.

But of course something must have been corrupted as I couldn't boot XP at this point(possibly an error(that for some reason was never alerted to me) when I was creating/resizing partitions).  So there isn't exactly an 'uninstall' in Linux.  I deleted the linux partition and resized my Windows one(which appeared to be empty at this point).

So basically now, after using the recovery disc twice and trying several options, it seems that when I boot, it runs this 'GRUB 1.5' blah blah thing that was booted when the Linux dual boot was run.  Of course Linux should no longer exist, but somehow it does.

So since this runs at the boot, it returns some error(22 I think) and so Windows will NOT boot, even after a full recovery.


Why on earth is that loading still?  and what is wrong with this because Windows is installed(factory), but will not boot.

---

### Post by solar george on 2007-10-23
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

Super Grub Disk

---

### Post by NilsE on 2007-10-23
When the problem first occured all you needed to do was add Windows to the grub menu but it may be too late for that now.

Using the super grub linked by Solar George you may be able to get rid of the master boot record created by the Ubuntu install and restore it back to where it was when just Windows was on the drive.

---

### Post by mikeserv on 2007-10-23
I did something like this last week...  

After upgrading from Fiesty to Gutsy I decided that I wanted a fresh install instead so I formatted my Linux harddrive (a USB external) and installed afresh.  But rather than edit the MBR on the first harddrive (Windows internal) I decided to make the USB bootable of its own right.  Well, I expected the internal's harddrive to revert back to its Windows only MBR afterwards, but this was not the case.  In order to boot Windows I had to use Super Grub to delete the Grub MBR on the internal harddisk and then run the Windows Recovery CD.  From there I told Windows to check the startup procedure and it recognized that the MBR was gone and reinstalled the bootloader.  Now when I start my computer it will automatically boot into Windows, unless I halt the boot process with F12 and tell the BIOS to boot from the USB drive.  This helps keep the wife and kids out of Linux.

-Mike

---

### Post by Sup3rkirby on 2007-10-23
Thank you all for your help.  That super GRUB disc did the trick.  It took a bit of playing with(found out I had to activate my windows partition), but I got it working and everything is back to normal.

Say, I hate to stray off topic here but mikeserv, when you tell it to boot from the USB drive, is that just changing the boot order temporarily, or does your pc actually have an option to boot from that drive?  I was just curious as I've never seen USB in the boot order, so I have never booted from a usb, and I would like to do something like keep a copy of linux on there, just to have it handy :)

---

