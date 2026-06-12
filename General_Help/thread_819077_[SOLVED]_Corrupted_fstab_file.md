---
title: "[SOLVED] Corrupted fstab file?"
date: 2008-06-05
forum: General Help
---

### Post by BobSongs on 2008-06-05
**problem**
My **/home** folder is on a separate partition for sanity reasons. My current Hardy Heron installation has suddenly stopped seeing my **/home** folder.

To get my **/home** folders back into the file system, I run the following command as su:

```
mount /dev/sdb1 /home
```and it works like it always did. However, upon rebooting the PC **/home** returns to its empty state again, requiring the same command to be repeated. So, I suspect there's something wrong with my **/etc/fstab** file. Here is my copy:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=eacdd4a8-993f-4aa7-af02-725ba1b8fadb /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb1
UUID=157045c4-0dd2-480a-b934-9dbc0d03afa9 /home           ext3    relatime        0       2
# /dev/sda1
UUID=E6C42FA6C42F7847 /windows        ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=1fd45975-344e-dbaf-82ee-b5ac6575a77d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


Andy ideas? The UUID thingies baffle me somewhat.

---

### Post by iaculallad on 2008-06-05
Try changing "relatime" to "defaults" in your /etc/fstab file. (in your /home line)

---

### Post by Rocket2DMn on 2008-06-05
Can you please post
```
sudo fdisk -l
sudo blkid
```
(just drop sudo if you are in a su/root session).

---

### Post by BobSongs on 2008-06-05
> **Rocket2DMn said:**
> Can you please post
```
sudo fdisk -l
sudo blkid
```(just drop sudo if you are in a su/root session).
Sure thing.

**sudo fdisk -l **gives:
> [FONT=Fixedsys][SIZE=2]Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00030836

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2571    20651526    7  HPFS/NTFS
/dev/sda2            2572        9593    56404215   83  Linux
/dev/sda3            9594        9729     1092420   82  Linux swap / Solaris

Disk /dev/sdb: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9d999d99

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1[/SIZE]    [/FONT]OK. And **sudo blkid** gives:

> [FONT=Fixedsys][SIZE=2]/dev/sda1: UUID="E6C42FA6C42F7847" TYPE="ntfs" 
/dev/sda2: UUID="eacdd4a8-993f-4aa7-af02-725ba1b8fadb" TYPE="ext3" 
/dev/sda3: TYPE="swap" UUID="1fd45975-344e-dbaf-82ee-b5ac6575a77d" 
/dev/sdb1: UUID="157045c4-0dd2-480a-b934-9dbc0d03afa9" TYPE="ext2"[/SIZE][/FONT]Ahh. Now, isn't **that** interesting, eh? **blkid** says [FONT=Fixedsys][SIZE=2]/dev/sdb1[/SIZE][/FONT] is **ext2**, whereas my [FONT=Fixedsys][SIZE=2]/etc/fstab[/SIZE][/FONT] says it's **ext3**. Mhmm. Let's say I correct [FONT=Fixedsys][SIZE=2]/etc/fstab[/SIZE][/FONT] and post what results?

You see: I noticed on my own originally when posting the contents of my **fstab** file that it said: >  [FONT=Fixedsys][SIZE=2]# /dev/sdb1
UUID=157045c4-0dd2-480a-b934-9dbc0d03afa9 /home           ext3    relatime        0       2[/SIZE][/FONT]And even as I posted it I wasn't exactly sure this was true.

OK. I'll change it.

**Note: "defaults" **instead of **"relatime"** did not help. In fact it made mounting /dev/sdb1 into /home impossible.

---

### Post by Rocket2DMn on 2008-06-05
Yeah, go ahead and change it to ext2 in fstab, not sure why it said ext3 to begin with, unless you reformatted sdb1 after install.  Also, you cut off the output of the fdisk command, but I think we have what we need.

You may want to run fsck on the partition.  It must be unmounted, which you seemed to have already mastered :)  This can also be achieved from the recovery mode terminal or the LiveCD.

UUIDs are used in place of /dev locations because they (basically) never change unless the partition itself is fiddled with (like resized or moved).  Some people have problems with /dev locations changing on every boot, so UUIDs are extremely uesful in that case.

Let us know how changing to ext2, running fsck, and reboot works out.

---

### Post by BobSongs on 2008-06-05
My [FONT=Fixedsys][SIZE=2]/etc/fstab[/SIZE][/FONT] file was corrupted by one digit. [FONT=Fixedsys][SIZE=2]/dev/sdb1[/SIZE][/FONT] is not set to **ext3,** but **ext2.**

Odd, that. I don't know how that happened. But it did.

Thanks all! :-) Problem solved

:popcorn:

Oh, no! Now you all know my dirty secrets! I use ext2!!!

:shock:

---

### Post by Rocket2DMn on 2008-06-05
That's so 90s.  Old school!
Glad you got it working.

---

### Post by BobSongs on 2008-06-05
> **Rocket2DMn said:**
> Yeah, go ahead and change it to ext2 in fstab, not sure why it said ext3 to begin with, unless you reformatted sdb1 after install.Odd that, eh? Everything was working fine. Then I logged out, logged back in and: **poof.** /home was gone. Somewhat disturbing thought.
> **Rocket2DMn said:**
> Also, you cut off the output of the fdisk command, but I think we have what we need.Odd. I just opened another terminal... and I got the exact same results. :confused:

> **Rocket2DMn said:**
>  You may want to run fsck on the partition.  It must be unmounted, which you seemed to have already mastered :)  This can also be achieved from the recovery mode terminal or the LiveCD.lol. Yeah; I've got mounting down. I'll do that immediately. ;-)

> **Rocket2DMn said:**
>  UUIDs are used in place of /dev locations because they (basically) never change unless the partition itself is fiddled with (like resized or moved).  Some people have problems with /dev locations changing on every boot, so UUIDs are extremely uesful in that case.

Let us know how changing to ext2, running fsck, and reboot works out.Yep! The system's back to normal.

I keep a copy of **Slax 5.1.8.x **around for such emergencies, as well as for helping out Windows XP users who's systems have gone beyond repair. So I managed to see that /home was alright and all files were safe. I just needed that **blkid** tip!

Much obliged.

---

