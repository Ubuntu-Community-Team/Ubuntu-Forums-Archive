---
title: "Delete Ubuntu partition and now GRUB boot loader wont let me start my pc."
date: 2008-06-20
forum: General Help
---

### Post by Felliph3 on 2008-06-20
Basically, I deleted Ubuntu by deleting the partition it was and now everything is fine except for the fact that I cant boot my pc! I get to the grub boot loader and it says error 22 and the underline keeps flashing, i let it stay on by mistake and when i woke up it was still flashing so im pretty sure its not working. I want to boot windows the way it does normally, without the grub. How can I do this? Im just trying to boot windows at least and then get rid of the GRUB boot loader.

---

### Post by rogier.de.groot on 2008-06-20
GRUB is upset because it can't find it's configuration file. There's basically two ways of fixing this:
a) IF you have a Windows install CD you can boot from that and get into the windows command prompt (not all CD's have that option though). I'm not exactly sure which option this is, I think "recovery console".
b) Otherwise, reinstall Ubuntu, boot into windows using your new GRUB, and fire up the windows command line from there.
Both) Run the commands FIXBOOT and FIXMBR. I think; it could also be that FIXBOOT has and MBR (=Master Boot Record) option; you might want to check with "FIXBOOT /?" what exactly all the options are. At any rate, this will restore the windows boot loader.
Good luck!

---

### Post by ibutho on 2008-06-20
You need to remove grub first. If you can get hold of [super grub disk]("http://www.supergrubdisk.org/"), use that to remove grub. Another option is to boot from a dos floppy or live disc (something like freedos) and run "fdisk /mbr". Yet another option is to boot from a Windows install cd, go into rescue mode and run "fixmbr".

---

### Post by justleen on 2008-06-20
you will have to reinstall the windows MBR.. 

I know of two ways... boot your windows cd in to rescue mode, and do a "fixmbr"
Or, get supergrub, that will enable you aswell to reinstall the windows MBR

edit : LOL, just notice your other thread " how to remove ubuntu..."  well.. the way is not to delete the partition ;)

---

### Post by bawbag31 on 2008-06-20
If you have a floppy drive, you can boot from a windows boot floppy.  You can make one by formatting a floppy from within windows and ticking the option to make a system disk or something like that.  Once at the command prompt type: -

fdisk /mbr

That will write a basic windows boot sector to you first hdd.

---

### Post by Zorael on 2008-06-20
Or you could use a live cd. Boot it up to the desktop environment, enable the universe repository in Software Sources, then install the **testdisk** package. Run it with superuser permissions in a terminal, select your harddrive and pick Write MBR. (The partition table type is likely Intel, by the way.)
```
$ sudo testdisk
```
```
TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org


Disk /dev/sda - 120 GB / 111 GiB - CHS 14593 255 63

[ Analyse  ]  Analyse current partition structure and search for lost partitions
[ Advanced ]  Filesystem Utils
[ Geometry ]  Change disk geometry
[ Options  ]  Modify options
**[ MBR Code ]  Write TestDisk MBR code to first sector**
[ Delete   ]  Delete all data in the partition table
[ Quit     ]  Return to disk selection






Note: Correct disk geometry is required for a successful recovery. 'Analyse'
process may give some warnings if it thinks the logical geometry is mismatched.
```

---

### Post by Felliph3 on 2008-06-20
Oh great, now when i go into recovery mode on the windows home xp installation cd i cant do anything bc the administrator password is wrong. I have only used 2 passwords the whole time ive had that pc and yet theyre both wrong. Even no password doesnt work. and the best part is I dont have any blank cds to burn anything to try boot it up. Im trying out the super grub disk but i cant burn it since i dont have any cds :-( . Ill figure something out.

---

### Post by Felliph3 on 2008-06-20
AHAHA yessss, while browsing my pile of cds I came across this burned cd (iolo technologies recovery something) and it had a FIX BOOT MEMBRANE option. It worked! Thanks a bunch for all those that gave me good imput!!!

---

### Post by quixote on 2009-01-14
The Ubuntu community just absolutely rocks!  I had to return an old work computer, so I took all my junk off, including my Ubuntu partition, and . . . whammo, I had exactly the problem of the original poster.

Making it worse was that the computer no longer had a functional CD drive. I did have a USB floppy drive though.

With bawbag31's suggestion to use ```
fdisk /mbr
``` at that nice little A: prompt I haven't seen in years, I was back in business in seconds.

I realize I'm on an old thread here, but I just had to thank you all and let you know you've saved yet one more person's behind!

---

