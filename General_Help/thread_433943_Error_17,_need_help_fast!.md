---
title: "Error 17, need help fast!"
date: 2007-05-05
forum: General Help
---

### Post by lyhty on 2007-05-05
Ok, I'm a complete newbie when it comes to this stuff and need help asap.

So I've been dabbling with ubuntu for a while now with Windows XP on the side. Today I decided to put my ubuntu experiments aside for a moment and casually destroyed the partition I had reserved for linux in windows (as I said, I'm really a newbie). Now when I try to restart the computer I get

GRUB Loading stage 1.5.

GRUB loading, please wait...
Error 17

and then nothing. I've tried to boot from ubuntu cd but it ends up with the same results. I also don't have XP cd with me so I can't try booting from there. Can anyone help me get my computer back on its feet? I really need help fast as I won't have an internet connection after monday if I can't get my laptop running again.

---

### Post by nikhilk on 2007-05-05
> **lyhty said:**
> I've tried to boot from ubuntu cd but it ends up with the same results.
Are you sure that your CD drive has a higher priority than your hard drive in the boot devices list? You should be able to check that from your BIOS configuration.

---

### Post by lyhty on 2007-05-05
Just checked it, and yes, the CD has a higher priority. BIOS is the only thing I can get to at the moment without getting the error.

Edit: Also, it's Ubuntu 7.04 I'm working with, if that helps.

---

### Post by nikhilk on 2007-05-05
Exactly what error are you getting when you try to boot from the CD?

---

### Post by lyhty on 2007-05-05
> **nikhilk said:**
> Exactly what error are you getting when you try to boot from the CD?

I was getting the same error as without the cd, but after working things out a bit at BIOS I managed to boot from CD. Should I try this

sudo fdisk -l

thing I found from googling my error, or just try to install ubuntu again?

---

### Post by siralphred on 2007-05-05
You can try to reinstall Grub with a Ubuntu Live Cd and see if that helps [http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub]("http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub")

---

### Post by lyhty on 2007-05-05
> **siralphred said:**
> You can try to reinstall Grub with a Ubuntu Live Cd and see if that helps [http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub]("http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub")

Reinstalling grub did not work. After typing 

find /boot/grub/stage1

I got

Error 15: File not found

I'll try to install ubuntu again and see what happens.

---

### Post by nikhilk on 2007-05-05
By default GRUB is installed in the MBR. So playing with the Linux partition should not bork GRUB.
> **lyhty said:**
> Today I decided to put my ubuntu experiments aside for a moment and casually destroyed the partition I had reserved for linux in windows
Could you elaborate?
Of course you can try to reinstall GRUB as siralphred said if you are in a real hurry. Good luck.

---

### Post by lyhty on 2007-05-05
> **nikhilk said:**
> By default GRUB is installed in the MBR. So playing with the Linux partition should not bork GRUB.

Could you elaborate?
Of course you can try to reinstall GRUB as siralphred said if you are in a real hurry. Good luck.

I used this program which name escapes me, the like of Partition Magic, where you can partition your harddrive without installing windows again. I figured I could use some more space for windows as I didn't plan to use linux for now so I destroyed my ext3 partitions (including root and everything else) and partitioned some of the free space for extra ntfs space, leaving some 10+ gb free to install ubuntu later back. What I didn't count on was that if I shut the computer before installing ubuntu it would end up like this.

Installing ubuntu again seems to be working somewhat good at the moment. Making partitions as I type.

---

### Post by siralphred on 2007-05-05
hey i found this on the gentoo website i think it could help u ...scroll down to where is says error15 and read [http://www.gentoo.org/doc/en/grub-error-guide.xml?style=printable]("http://www.gentoo.org/doc/en/grub-error-guide.xml?style=printable")

---

### Post by lyhty on 2007-05-05
> **siralphred said:**
> hey i found this on the gentoo website i think it could help u ...scroll down to where is says error15 and read [http://www.gentoo.org/doc/en/grub-error-guide.xml?style=printable]("http://www.gentoo.org/doc/en/grub-error-guide.xml?style=printable")

Sounds complicated but doable. I'll definately try that if reinstalling ubuntu does not work.

---

### Post by lyhty on 2007-05-05
Seems like I managed to restore order to my laptop with reinstalling ubuntu. No idea what happened there at first with not allowing to boot from cd, though.

Thanks all for fast answers and moral support. :)

---

### Post by rygar on 2007-05-05
what exactly do you mean when you say you destroyed the partition?

if your linux partition is being displayed as unallocated space, you should rebuild your partition tables.
try downloading partition table doctor--simple and effective software that allows you to rebuild partition tables, master boot records, boot sectors, and more.  even comes with a bootable image.

if the partition exists but is not being read as linux, you need to fix the boot sector.  PTD can do that too.

i had a problem where my linux partition (ext3) was accidentally being read as ntfs.  the e2fsck command fixes this.  (ie sudo e2fsck -f /dev/sda#)  do it from the ubuntu live cd.

hope this helps.

---

