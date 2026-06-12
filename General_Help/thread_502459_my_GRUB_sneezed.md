---
title: "my GRUB sneezed"
date: 2007-07-16
forum: General Help
---

### Post by catnappist on 2007-07-16
I re-installed Feisty because it didn't like that I was messing around with a drive that had nothing to do with it.  I'd been meaning to start over anyway to get my partitions in order and put root and home in the same place (separating them didn't work for me at all).  But when I cranked it up, there were two entries at the bottom of the GRUB menu for WinXP.  One works and the other one crashes.  Here's what's at the bottom of my GRUB:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb3
title		Microsoft Windows XP Home Edition
root		(hd1,2)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

I'm thinking the bottom one is the beast since WinXP is on hda1 and my dumping grounds are at hdb3.  Am I gonna screw anything up if I just wipe the bad boy from the bottom?

---

### Post by geek_Man on 2007-07-16
If you think the bottom one is no good then you can just delete it.

---

### Post by catnappist on 2007-07-16
kee-yah, that was quick.  Not like getting it wrong could mess with ubuntu anyway, right?  I mean... it's just Windoze.

---

### Post by misconfiguration on 2007-07-16
Well does your XP partition still live? If it does is there anything on it?

It seems as if, when you try to boot XP it doesn't see anything in the MBR, when you reinstalled did you overwrite the previous installation and JUST put Feisty on there?

If you don't want XP anymore, delete the bottom entry that won't hurt anything it'll just keep Grub from seeing it at bootstrap. One thing I do recommend is that you get rid of the partition if it still lives, there is no point in wasting the space for an installation you wont use. 

```
sudo fdisk -l
```   # See if you have any NTFS partitions still living. 

```
df -h 
```             # List your file systems with disk usage in human format.

---

### Post by catnappist on 2007-07-16
No, actually WinXP is still at hda1 and working fine.  It's just that there were two entries for it in the GRUB, one works and the other one goes bang.  I've never messed with the GRUB and I'd like to know if it's as sensitive to my meddling as fstab is. :o

---

### Post by catnappist on 2007-07-16
Interesting, df -h.  Don't understand it, but it looks cool.

---

### Post by misconfiguration on 2007-07-16
> **catnappist said:**
> No, actually WinXP is still at hda1 and working fine.  It's just that there were two entries for it in the GRUB, one works and the other one goes bang.  I've never messed with the GRUB and I'd like to know if it's as sensitive to my meddling as fstab is. :o

No, it's kind of odd that it's mapping (hd0,0) --> (hd1,2) then back again. Delete the entry, you don't need it :).

df -h is just a utility that lists your partitions with the disk usage. 



Filesystem            Size  Used Avail Use% Mounted on
/dev/VG00/lvol0      1008M  105M  852M  11% /
/dev/cciss/c0d0p1     124M   17M  101M  14% /boot
/dev/VG00/lvol5        97M  4.1M   88M   5% /home
/dev/VG00/lvol2       3.0G  185M  2.7G   7% /opt
/dev/VG00/lvol6      1008M   33M  925M   4% /oracle
none                 1007M     0 1007M   0% /dev/shm
/dev/VG00/lvol4       2.0G   33M  1.9G   2% /stage
/dev/VG00/lvol7        54G  329M   51G   1% /u
/dev/VG00/lvol1       2.0G  1.1G  816M  58% /usr
/dev/VG00/lvol3       2.0G  147M  1.8G   8% /var

You can see the size of the disk, the available size that you have left and the % of usage then where it's mounted.

---

### Post by catnappist on 2007-07-16
Yeah, I thought it was weird that repartitioning my dump drive would screw ubuntu up, since they aren't related.  I'll write down that little df -h ute, could come in handy.

Well, I deleted the mess from the GRUB.  Here goes...

---

### Post by catnappist on 2007-07-16
Ha!  Nothin's broke.  Thanks geek_Man, misconfiguration!  :)

---

### Post by geek_Man on 2007-07-17
Glad to help.

---

