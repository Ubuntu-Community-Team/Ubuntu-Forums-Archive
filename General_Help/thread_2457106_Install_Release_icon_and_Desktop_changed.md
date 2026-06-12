---
title: "Install Release icon and Desktop changed"
date: 2021-01-26
forum: General Help
---

### Post by zeekstern on 2021-01-26
My system froze up so I could not shut down cleanly. I was mainly using Opera and had about 10 tabs open. I had to reset my pc. When it came back up, I now have an icon on the desktop that says Install Release. My desktop has changed. It looks like the default one you get after the initial installation. All of my files in the Downloads folder are gone, but at least the Documents folder is still there. Is there any way to find out what happened? I'm running Ubuntu 20.04.1 LTS. It's almost like Ubuntu tried to install itself.

Thanks,
Zeek

---

### Post by ActionParsnip on 2021-01-26
What file system are you using for your home?
Is it on a separate file system?
Can you see the files if you use the terminal?

---

### Post by zeekstern on 2021-01-26
I have everything under an ext4 root partition. There are no files under Downloads or a Samba share I set up. In fact, the Samba share directory was even missing. 

Here is fdisk output:

/dev/sdb1  *           63 310602776 310602714 148.1G  7 HPFS/NTFS/exFAT
/dev/sdb2       466929225 488392064  21462840  10.2G 49 unknown
/dev/sdb3       310603776 311654399   1050624   513M  b W95 FAT32
/dev/sdb4       311656446 466927615 155271170    74G  5 Extended
/dev/sdb5       311656448 397728829  86072382    41G 83 Linux
/dev/sdb6       397729792 398780415   1050624   513M  b W95 FAT32
/dev/sdb7       398782464 466927615  68145152  32.5G 83 Linux

Note the 2 Linux partitions. I had trouble installing the first time so I installed on a different partition and everything was good. I did the initial install in June, and have been running just fine since then.
It is odd that just the Downloads and Samba dirs were messed up, and all of a sudden that Install Release icon showed up.
Everything else seems to be working just fine.

---

