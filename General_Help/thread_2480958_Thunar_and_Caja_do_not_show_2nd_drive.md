---
title: "Thunar and Caja do not show 2nd drive"
date: 2022-11-15
forum: General Help
---

### Post by raleigh3 on 2022-11-15
Since going to 20.04 I have been seeing some odd behaviors.

Thunar and Caja is not seeing my Maxtor_SDB1 which is my second drive.

I could use help diagnosing this.

```
lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS

sda      8:0    0   1.8T  0 disk 
&#9500;&#9472;sda1   8:1    0     1M  0 part 
&#9500;&#9472;sda2   8:2    0   513M  0 part /boot/efi
&#9492;&#9472;sda3   8:3    0   1.8T  0 part /
sdb      8:16   0 298.1G  0 disk 
&#9500;&#9472;sdb1   8:17   0  98.4G  0 part 
&#9492;&#9472;sdb2   8:18   0 199.7G  0 part /media/andy/MAXTOR_SDB2
sr0     11:0    1  1024M  0 rom
```

---

### Post by TheFu on 2022-11-16
Can you show the fstab entry that mounts it?
BTW, lsblk output can show so much more useful information.  Create an alias:
```
alias lsblkt='lsblk -e 7 -o name,size,type,fstype,mountpoint'

```

UUID and LABEL can be added to the options, if you prefer to mout using those. With LVM, neither is very useful.

---

### Post by raleigh3 on 2022-11-16
I ran Gparted and re-formatted it. The drive showed but I still could not access it.

I noticed that fstab had no entry for /dev/sdb1, so I got the UUID etc and made an entry in fstab for it.

After a reboot, I could not get to my desktop. :-(

I was close to concluding that the drive was bad as it is at least 7 yrs old.

But I did a disk check and it came back okay.

I did a search and found gpart which analyzes and repairs a disk.

[https://www.kali.org/tools/gpart/](https://www.kali.org/tools/gpart/)

I disabled sleep while it ran.

Now I can boot up fine and the drive shows and can be used.

---

### Post by TheFu on 2022-11-16
So this was all over running an fsck?

If solved, please mark it so.

---

