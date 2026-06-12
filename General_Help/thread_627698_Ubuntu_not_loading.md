---
title: "Ubuntu not loading"
date: 2007-11-30
forum: General Help
---

### Post by akashexe on 2007-11-30
Hi All

I had recently installed ubuntu 7.04 on my computer (pentium4 ). It was working well untill last morning when i deleted some files with .rec extension  on my c: system drive of win xp . Dont really know whether that is the real problem with the booting..

it loads all the drives and then when it comes to sda2 it stops all of a sudden .This were the diagonistics that were generated when booted up.
[FONT="Courier New"]
/dev/sdb6:3 files,3/1599189 cluster
dosfsck 2.11 ,12 Mar 2205 Fat32 LCN

/dev/sdb7:3 files,1/1276669 cluster
dosfsck 2.11 ,12 Mar 2205 Fat32 LCN

/dev/sdb9:3 files,3/1918827 cluster
dosfsck 2.11 ,12 Mar 2205 Fat32 LCN[/FONT]

and then i get this........

[FONT="Courier New"]there are differences between boot sector and its backup
Differences:(offset:orginal/backup)
430:4e/52
[/FONT]

and many comma seperated variables...

[FONT="Courier New"]Not automatically fixing this.


/dev/sda1:19941 files,938361/1278924 cluster
dosfsck 2.11 ,12 Mar 2205 Fat32 LCN

/dev/sda2:26902 files,1092864/1163574 cluster[/FONT]

it hangs after this point..

Seeing this problem i found it fit to reinstall ubuntu and i did that ..
Well there seems to be no end to this problem..
Please help
Thanks in advance
-Sam

---

### Post by navaburo on 2007-12-01
Try booting up with a liveCD (like the ubuntu one or Knoppix), mount your linux partition and edit your /etc/fstab file. Comment out (with a # sign at the begining of the line) each line involving a fat or ntfs partition, just leave the swap and ext3 (the linux partitions).

After rebooting linux should ignore everything on the windows drives.


(perhaps i misunderstand your situation, if so please clarify).

---

