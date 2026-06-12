---
title: "Installed Feisty.. GRUB error 5 on boot.. !!"
date: 2007-04-22
forum: General Help
---

### Post by billdotson on 2007-04-22
I have sda which is my Windows hard drive.  It is internal.  My external hard drive (sdb) is where I have Edgy installed on sdb1.  I have some other ext3 partitions that contained the dd and ntfsclone backup images of Windows XP.

I installed Feisty the first time and told it to install GRUB to fd0 (floppy I had in)
Then I tried to boot from the floppy, so I could boot into Feisty.. no luck.. it just said GRUB _ and the cursor blinked and nothing happened.  Then I tried copying the Feisty menu.lst entry into the one on /boot/grub/menu.lst on Edgy.  
I booted from the external hard drive and assumed that since GRUB knew where to look for Feisty it could boot it. 

I chose the Feisty entry in the menu and it said Grub Error 5: Partition Table Invalid or Corrupt.

So I thought it might have just been Feisty.  

Then I booted into the Feisty LiveCD and told it to reinstall again but except to reinstall to to hd1 instead. (I have been installing Feisty on sdb8, a logical ext3 partition)

Then I tried to boot my external hard drive and it said "Grub stage 1.5 loading.... Error 5"
So now I can't even boot into Edgy.  Also, since it says GRUB error 5 I am guessing that my data on my external hard drive might be corrupted as well, including ALL my backup images I spent so long on AND my Edgy install, which has been heavily worked on and modified (lots of BASH scripts for automating the backup of stuff including Windows XP).
I heard but do not know if this is true but if you install GRUB to the MBR then it can corrupt or destroy the current partition table.  I do not know if this is true though.

Maybe Feisty doesn't like being an a logical partition.. I do not know.

Anyway, I am copying the contents of menu.lst (the one in Edgy's /boot/grub) into Feisty's menu.lst to see if I can at least boot Edgy. 

Should I install Feisty to something that is NOT a logical partition or is there a more serious issue going on here?

Thanks.

---

### Post by billdotson on 2007-04-22
help?

---

### Post by billdotson on 2007-04-22
no help I see..

Feisty install has made Edgy and Feisty both unbootable.. great.

I have done fsck for each of the partitions and they are all clean.  What is going on..?

---

### Post by billdotson on 2007-04-23
so I reinstalled Feisty but this type told a primary partition to be /boot.

This time I actually got to the grub menu but when I tried booting Feisty I get an error 15.
If I try to boot Windows I get an error 13.
If I try to boot Edgy I get a Error 17.

So I reinstalled Feisty, except this time had it installed on a primary partition with no /boot (just let /boot be on the install partition like it is by default).

I tried booting each OS, Feisty, Edgy an Windows and now for Feisty instead of error 15 I get error 17.
So Edgy and Feisty are getting error 17 and Windows is still getting error 13.

At least GRUB is installed on the external drive so I can at least boot into Windows if I boot from the internal.  It is nice to actually have a BOOTABLE AND WORKING OS!!

Honestly, I have wasted so much time working with Linux and not getting anywhere.  It might be time for me to stop messing with Linux, as I am beginning to hate it.  I could never hate Tux, but Linux is beginning to make me despise him.

I wonder if I will EVER get any of this crap fixed.  Maybe Something happened with the Feisty install and just plain out ruined everything on my external drive and I will have to reformat it all and start all over again.

WOW that sounds like a lot of fun.. losing all my data and all my programs I had installed in Edgy.. great.

Thanks for nothing Feisty!!!

---

