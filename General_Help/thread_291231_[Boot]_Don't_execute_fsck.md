---
title: "[Boot] Don't execute fsck"
date: 2006-11-02
forum: General Help
---

### Post by Mathiasdm on 2006-11-02
Here's the deal: I have a dual-boot with Edgy Eft and Windows XP. When checking the Windows XP system (FAT32), fsck stops working, so the boot doesn't finish.

Because of this, I can't access Edgy. Until I find a more definite solution, I'd like to make fsck not check the Windows XP partitions (hda1 and hda2).

Is it possible to do this, yet check my Edgy System (hda3, hda4 and hda5)?

Oh, and I'll have to do this from a LiveCD. Any suggestions on config files I need to edit?

---

### Post by JohnLai on 2006-11-02
For FAT32, use "dosfsck -(the command you typed) /dev/(fat32 partition name such as hda1 or hda 2)". As for your ext2 or reiser partition, use "fsck -f /dev/(your linux partition name)". Enter the recovery mode to use the command.

---

### Post by Mathiasdm on 2006-11-02
That's not what I meant (but thanks for the info).

I want, when Edgy boots, no file system check on my windows partitions. How do I turn that file system check off?

---

### Post by katalyst23 on 2006-11-02
Try going into your /etc/fstab file and editing the line for your windows drive.

/dev/sda2	/media/satadata	vfat	auto,user,exec,rw,umask=0000 0	0

For instance this is what my line in my fstab.  See the 6 column, the last one all the way over there on the right? Those are your options for whether or not to fsck the drive on boot up.  If you set it to 0, that filesystem won't be fscked.  

Also, this link might help you understand, in case I was terribly unclear in my explanation. :D


[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by Ramses de Norre on 2006-11-02
Press ctrl-c when the disk checking starts to abort it.

And you might need to wait a while after the scanning, when my edgy install does an fsck on startup it always seems to hang after it for a minute or two.. it's very strange and I have no idea what happens at that point but after this minute or two the booting up continues as normal..

---

