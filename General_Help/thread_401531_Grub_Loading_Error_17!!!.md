---
title: "Grub Loading Error 17!!!"
date: 2007-04-04
forum: General Help
---

### Post by dametalone on 2007-04-04
hey people, i booted my computer today and i got this:

GRUB Loading stage1.5

GRUB loading, please wait...
Error 17


my computer is a dual boot

i have windows xp on 1 and ubuntu on another.  But because of this error, i cant do anything....help

---

### Post by dametalone on 2007-04-04
anybody?

---

### Post by brentoboy on 2007-04-04
was grub ok before?
how long has it been ok before it up and died?

any updates lately?

---

### Post by aodhon on 2007-04-04
Error 17 occours whem the partition you are trying to boot up exists but it cannot recognize the filesystem.  I'm not too sure as to how this could have happened, did you reformat it by any chance?

---

### Post by dametalone on 2007-04-04
there was an update earlier today but there were no problems with it.  It was fine until i got home today and had to reboot it cuz i hooked up a new keyboard.  I have not reformated it recently.  I booted off the live cd and sorta went through the install process so i could get to the partitioner.  My ntfs (/dev/sda1 looks ok...its also set on boot fyi).  Under that (/dev/sda2) instead of ext2 or ext3 (i forget what i formated it to) it says unkown.  And then i have my swap for /dev/sda 3

---

### Post by brentoboy on 2007-04-04
I had a grub problem when I apt-got (is that a word) a kernel that was too cool for my processor.  I had to click escape (or something) when grub popped up so I could see the boot menu.  then, I could boot the older kernel that I had been using before that point.   (of course the first thing I did after I booted was remove the incompatible kernel package)

---

### Post by aodhon on 2007-04-04
Can you get to the recovery mode?  Can you get into XP?

---

### Post by dametalone on 2007-04-04
> **aodhon said:**
> Can you get to the recovery mode?  Can you get into XP?


negative.  I turn on my computer and the initial bios show up and all and when its supposed to give me the list of OS's to choose from i get the 

Grub loading

Error 17

---

### Post by aodhon on 2007-04-04
You could try reinstalling grub from a live cd [http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by dametalone on 2007-04-04
> **aodhon said:**
> You could try reinstalling grub from a live cd [http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

that wont work, when i enter in the command "find /boot/grub/stage1"  i get "Error 15: File Not Found"

---

### Post by aodhon on 2007-04-04
Here's another possible solution that I came across [http://www.gentoo.org/doc/en/grub-error-guide.xml]("http://www.gentoo.org/doc/en/grub-error-guide.xml")

---

### Post by brentoboy on 2007-04-04
> **dametalone said:**
> ...  Under that (/dev/sda2) instead of ext2 or ext3 (i forget what i formated it to) it says unkown.  ...

Do you mean that it cant read your /dev/sda2 at all?

Time to reinstall.

if it can read it, then maybe the grub install is just corrupted.  you can fix that from the liveCD with some toying around.

you would wander in to the old /boot/grub directory grab menu.lst and put it in the live CD file system hierarchy, and then update grub.

maybe even open up the menu.lst file and adding yourself a longer timeout or whatever.
this wiki page has some info on modifying and updating grub manually (toward the bottom)
[https://wiki.ubuntu.com/InstallingOrBootingUsingIsoFile?highlight=%28update+grub%29](https://wiki.ubuntu.com/InstallingOrBootingUsingIsoFile?highlight=%28update+grub%29)

-----
if you end up reinstalling, make yourself a separate boot partition with a half GB or whatever  (half gig is very liberal number.  Yo could get away with 256 MB easy.  format the boot partition with ext2 (not ext3).  It doesn't need to be journalized, it almost never changes anyway.
And then i have my swap for /dev/sda 3
and, if you have a separate partition for home, reinstalling doesn't make life suck because you don't loose documents.

---

### Post by Cappy on 2007-04-04
Just as a random thought, you should try a ```
e2fsck -f /dev/sda2
``` from a Live CD. If it gives you stuff to fix you can just hit <ENTER>.

---

### Post by m.musashi on 2007-04-04
I believe this error happens when your partitions change. For example, if your root partition was on sda5 and then you made a change and now it sda6 (or if you changed the drive order in your BIOS it could be sdb5).

Your best option is to boot a live cd and then edit menu.lst to reflect the correct partitions. Boot a live CD and the open a terminal and type
```
sudo fdisk -l
```
That last part is a small letter L.

From the output you should be able to discern which partition is your root. Then do
```
sudo gedit /boot/grub/menu.lst
```
and edit it to reflect the correct root partition. If you change drives in your bios hd0 might now be hd1 so fix that too.

Alternatively, if you made a change in the bios just change it back. If you made other edits to the partitions that is harder to undo.

If you made no changes at all then that is odd. Try and post the output of fdisk -l and your menu.lst. Perhaps we can see what is up.

---

### Post by duojet on 2007-04-07
I have almost the same problem!

I booted up my box this morning to find a nasty surprize-

GRUB now loading....
GRUB error 17

Boo. I'm running the Live CD at the moment.
I tried to re-install grub from a post on the ubuntu forums and it didn't work, nor did the super grub disk - but both of those attempted to install grub stage 1 . my grub claims to be stage 1.5...

I am aware that error 17 means grub can't find anything it can read- but Gparted from the live disk sees everything in my dual boot partition.
fdisk -l says this:

Disk /dev/hda: 60.0 GB, 60060155904 bytes
255 heads, 63 sectors/track, 7301 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 1 3787 30419046 7 HPFS/NTFS
/dev/hda2 3788 7154 27045427+ 83 Linux
/dev/hda3 7155 7301 1180777+ 5 Extended
/dev/hda5 7155 7301 1180746 82 Linux swap / Solaris

when I run gedit on the list from the CD I get NOTHING

I haven't changed anything recently, and the disk has been dual boot for 3 months now, at least. The last thing I did was burn a CD with K3b - just before that I installed and removed azeureus, but I'm not sure how this happened.

When I boot into the live CD, as it sets up the Enterprise Volume business, it says:
Buffer I/O error logical block 26
Buffer I/O error logical block 27

it repeats that a couple of times, then it goes on about its business.

ideas?

---

### Post by duojet on 2007-04-07
FIXED! - at least for me!

THANK YOU CAPPY!
e2fsck worked!

---

### Post by Scotsgait on 2007-04-12
I'm completely new to Linux and grub just about sent me back to Windows....

I loaded Kubuntu on my new pc where I had transferred my back up drive (FAT 32) into the system.

On installing, it correctly partitioned the new drive but on boot, grub started looking for (hd1,0) instead of (hd0,0) - and the dreaded Error 17 appeared.

After I finally worked out what the problem was, I went into edit mode there. amended the appropriate line and booted.  It worked. I then went to /boot/grub and directly edited device.map and menu.lst files to make sure that (hd0,0) mapped to my main drive and referred to throughout the menu.

Hey presto, it worked. And it's still working....

:D

---

