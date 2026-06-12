---
title: "Date stamp not preserved while copying from USB drive?"
date: 2008-02-04
forum: General Help
---

### Post by vav on 2008-02-04
If I copy files from a USB (FAT) drive, the timestamp is set to the copying time/date! Can I preserve the original timestamp from the USB drive? I use the drive between XP/Gutsy computers and use it to sync code files :(

---

### Post by fsamuels on 2008-03-02
What is the file system type of destination location? I am having the same problem when moving or copying files to an NTFS partitions. FAT32 and ext3 both retain the modified date.

---

### Post by vav on 2008-03-02
I transfer between USB (FAT), Ubuntu (ext3) and XP (FAT). This problem still seems to affect me.

---

### Post by fsamuels on 2008-03-02
How are you copying the files? I found that using a command line and the cp command doesn't preserve the file dates either. Copying the files in Natulus does retain the modified date for me when the destination is FAT32 or ext3 but not NTFS.

---

### Post by Oldsoldier2003 on 2008-03-02
> **fsamuels said:**
> How are you copying the files? I found that using a command line and the cp command doesn't preserve the file dates either. Copying the files in Natulus does retain the modified date for me when the destination is FAT32 or ext3 but not NTFS.
have you tried using the -p switch when copying by command line?

---

### Post by julian67 on 2008-03-02
cp -p will do it, so will using rsync with -t or -a.  You could also use a dual pane file manager like emelfm2 and set its gui copy button/action to act as cp -p.  I think if you use Thunar it would be very easy to make a custom action (context menu right click) that copies preserving timestamp.

---

### Post by vav on 2008-03-02
I use nautilus. copying to and from USB (FAT). :(

---

### Post by sonrock3 on 2008-03-13
> **Oldsoldier2003 said:**
> have you tried using the -p switch when copying by command line?

It's a permissions issue.
Re pendrive, try allow others read/write via drive properites permissions tab.

Re NTFS drive, install NTFS-config then enable both options.

It worked for me in Ub Gutsy Gnome.

Good luck from
Stephen

---

### Post by sonrock3 on 2008-03-13
It's a permissions issue.
Re pendrive, try allow others read/write via drive properites permissions tab.

Re NTFS drive, install NTFS-config then enable both options.

It worked for me in Ub Gutsy Gnome.

Good luck from
Stephen

---

### Post by ryke on 2008-05-13
Hi,

I have an external usb disk. The disk is not always on (so, I think I cannot use fstab to solve the problem, because /dev/sdX can change, and I use several pendrives with different partition systems too).

I've already changed owner and group (with chown and chgrp), because the place where partitions are mounted are always the same)

It has 1 NTFS partition and 1 EXT3, and with both happen the same. If I copy a file from Terminal (using cp -a) date stamp is preserved. But if I copy a file using Nautilus, date's file is the one at the moment of the copy.

I'm using Hardy.

Any idea about how to solve it? Maybe using LABEL instead of /dev and noauto option in fstab could be a solution?

Thanx in advance

---

### Post by urshans on 2008-05-20
@sunrock3: Yes it worked fine with 7.04 and 7.10, but it does not work anymore with 8.04.

Will it mean that in the end we will have to go back to 7.04?

I hope not... Urs

---

### Post by ryke on 2008-05-20
Hi,

I've read somewhere this is Nautilus bug... 

Workaround:

Changing owner and group:
1. Type "sudo chown -hR [your username] /media/nameoftheusbdrive". Press enter
2. Type "sudo chgrp -hR [your username] /media/nameoftheusbdrive". Press enter again.

and copying files from Terminal (using -a), Grsync or Gnome Commander preserves date stamps... it works for me in 8.04 with NTFS, EXT3 and FAT32 partitions.

Regards

---

