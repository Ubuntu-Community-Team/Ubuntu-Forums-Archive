---
title: "Grub problem upon install"
date: 2007-02-02
forum: General Help
---

### Post by marchar on 2007-02-02
I have tried all the common Linux distros in the past couple months to learn and experiment....but, I am still pretty much a noob...

About 3 weeks ago I installed Freespire on my Sager laptop, using the whole drive.  Everything OK, but I really wanted to use Ubuntu...

So, yesterday I installed Ubuntu and in the installation process, did a manual partition of the drive and left the Freespire alone in its own partition hda1 without formatting it etc.  I installed Ubuntu in separate partitions beyond hda1.  Ubuntu works fine but in the process it somehow disabled the loading of Freespire.  After lots of head scratching, I installed GrubEd to work directly with the Grub menu list.  This is what the list now looks like... the first two memo lines were added by Ubuntu during install.... I added the rest, gleaning info from the Freespire forums etc.

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title       Freespire Ver. 1.1.73
root       (hd0,0)
kernel     /boot/vmlinuz-2.6.18-2-486  root=/dev/hda1
initrd      /boot/initrd.img-2.6.18-2-486
boot

I have tried lots of different ways of altering the Grub for Freespire....without positive results.

I installed QTParted to see if I could look into the Freespire partition.... the drive doesn't even show up.

I used System/Admin/Disks to look at the partition on this drive and this is the info....
device = /dev/hda1/
File System = ReiserFS
Access Path = none (I tried inserting various things here including /dev/hda1/ with no result & it doesn't "stick"
Size= 58 GiB (Free space not available) .... this is correct size of partition..
Status= Inaccessible   I tried "enabling" this partition.... no luck.  

Has Freespire in partition 1 gone permanently into Cyberspace or been corrupted??

Any ideas about what's goin' on with Grub and this partition??

All clues you might give will be much appreciated.... not much hair left here...

---

### Post by louieb on 2007-02-02
Just out of curiosity . Do you have a Puppy or Knoppix Live CD. 
It easy to look at your hard drives partitions with either of those. 
On the Puppy desktop look for the icon labeled "drives" click on it (single click) and it will list all the partitions. Click mount and it opens the file manage and show the contents of the partition.   The you can find the FreeSpire GRUB configuration file. (I guess it uses GRUB). and copy the Freespire entry to the Ubuntu GRUB configuration file. At least you can confirm if FreeSpire is intact or not.

---

### Post by marchar on 2007-02-03
Good mornin' louieb,
I downloaded PUPPY as you suggested.... nifty OS!  Also, found that indeed Freespire is intact in that partition.  Went into the Grub menu.lst and copied down the entry for booting Freespire.  There were numerous differences with what I earlier used...  I noted that Jiffyboot had done this grub work...
Went back to Ubuntu and edited the Grub list... 
Freespire began to load but hung up finally on KERNEL PANIC:

  "VFS: Unable to mount rootfs on unknown block (0,0) Cannot open root device "root" or unknown block (0,0)."

  Apparently, the location of the "root" has been changed... probably when I resized the partition when I installed Ubuntu.... The Grub menu says that rootdev is supposed to be located at 0x0301 but is apparently elsewhere.  This is way over my head...  I read somewhere that Grub can usually boot with a simplified boot sequence.... so removed the references to ramdisk and resume2 etc.... to no avail.

This is no catastrophe since I am in the "learning" mode.... I can focus on Ubuntu which is my preferred distro anyhow.  I did note that PUPPY actually found my video hardware properly...at least close as to resolution.... don't know about acceleration/color.....something that I have yet to achieve with Ubuntu... so the process continues...

Thanks for your efforts, I really appreciate your input.

---

