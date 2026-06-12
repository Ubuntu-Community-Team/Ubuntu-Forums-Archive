---
title: "How do I install XP without mucking up Ubuntu?"
date: 2006-12-31
forum: General Help
---

### Post by lucid on 2006-12-31
I have two hard disks, Edgy is on the large main, and I'd like to install Windows XP on the small second. I've run XP setup off the CD and at the partition part it wants to write files to both hard disks. Probably to get rid of Grub and lay a new MBR I suppose. 

I really don't won't to have to resize partitions on my main disk to risk damaging Ubuntu (which is my main OS these days). Can anyone suggest a way to install XP on the one disk cleanly? Or should I just take out the Ubuntu drive from the computer, and put it back in after I've installed XP?

---

### Post by pay on 2006-12-31
The only way I can think of doing it is by installing xp in a virtual machine. The new kernel (2.6.20rc2) has kvm so then you can use the open source qemu to run it at near native speeds. Otherwise you will have to resize the partition.

Happy new years.

---

### Post by ashmew2 on 2006-12-31
Im not very sure  about the two hard drive thingy , but I have an 80 GB Hard Disk on which ive installed XP on Drive C: after i had already installed Ubuntu.After I installed XP , it prevented GRUB from showing (Cuz XP , like most XP users , thinks that it is the only Operating System.). Anyways , so after intsalling XP , i booted from the Ubuntu Live CD , opened up the terminal and put the following commands :
sudo grub
Find /boot/grub/stage1 
(After this command , it will say something like "(hd0,x)" or in my case "(hd0,7)". Use whatever your computer spits out for the following lines) :

root (hd0,3)
setup (hd0)
quit

That's for only one Hard Drive though and i really have no idea for two hard drives :(

---

### Post by landcross12 on 2006-12-31
Consider using settings in your bios to choose  the boot drive selection.

Uninstall your Linux drive (just remove the cable)

Load Windows onto the other drive with normal setup procedures.

Then when finished reconnect your cable, Linux will work as normal.

When you want Windows just change the boot drive sequence in the bios

---

### Post by sloggerkhan on 2006-12-31
Yeah, what landcross says will work. If you disconnect your Ubuntu drive, xp will not know it's there. Then you can add a chainloader option to your grub file.

You could actually just let xp install and then restore grub. I think there are a few linux utility disks design to do it easy, but it's most likely easier to do it the other way.

---

### Post by lucid on 2007-01-01
Yep, that was the way to go. I pulled out the Ubuntu drive, installed XP, and whacked the Ubuntu drive back in. 

Now my remaining question is this: How do I have Grub pick up the change to the second drive? 

There is a Howto for restoring Grub but it dates back to '05, and it doesn't look to fit my need. Rather than having to replace Grub (as it seems to be there and working) is there a way to have it redetect the drives?

---

### Post by indytim on 2007-01-01
I did something similar a couple of months ago.  I had Ubuntu installed and needed to re-install Win2k from scratch.  This was all done on my primary drive.  Here's my approach:

1.  Delete the NTFS partition (I used GParted LIve).
2.  Create a new NTFS partition (again GParted Live).
3.  Boot to your Win Install disc.
4.  When the installation comes to the partition selection, select the partition created in #2.
5.  Wait patiently for long periods of time while Windows does it's thinger.
6.  Re-boot.
7.  If your Grub was destroyed in the process, use SuperGrub Live to re-create it (I didn't have to on my installation, but it sure helps to have the SuperGrub handy... just in case).

Hope this helps,

IndyTim

---

### Post by sloggerkhan on 2007-01-01
Yeah, I've used supergrub too, but if you pulled the Ubuntu drive and the issue is that the bootloader doesn't have a windows choice all you have to do is add a chainloader +1 entry directed towards the correct HD.

---

### Post by sloggerkhan on 2007-01-01
something like this:

title		Windows XP Professional x64 Edition
root		(hd0,3)
savedefault
makeactive
chainloader	+1

addressed to your windows drive as opposed to the ubuntu drive.

now I'm guessing that your second drive would be something like (hd1,0) but I really don't have a clue because GRUB addresses are a little confusing.

(and I think the savedefault line is optional. This is a change you'd make to /boot/grub/menu.lst)

---

### Post by lucid on 2007-01-02
Thanks for the advice. :)

I can boot windows with the supergrub disk, but using it to reload grub only produced the same results: correctly listing Ubuntu on the first drive, but listing the old dapper entries on the second drive which is now XP.

I edited the menu.lst with 
title        Windows XP Professional Edition
root        (hd1,0)
savedefault
makeactive
chainloader +1

The location should be correct, for root (hd1,0) is what the old entry used to boot off that drive.  However, when I try to boot of this entry it just hangs. 

Fixed! I added this:
map            (hd0) (hd1)
map           (hd1) (hd0)

and it is now working beautifully. Big thanks all round for the help. :)

---

