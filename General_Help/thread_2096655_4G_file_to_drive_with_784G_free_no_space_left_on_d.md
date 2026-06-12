---
title: "4G file to drive with 784G free: no space left on device"
date: 2012-12-20
forum: General Help
---

### Post by Statia on 2012-12-20
Hi,

I am trying to copy a 4.3G video file from my home directory to a samba backup/mediaserver share. Free space on that drive is 748G. Despite that I am getting a "drive full" error:

```
statia@quokka:~/Videos/Decay_2012$ cp Decay_2012_720p.mp4 /mnt/samba/statia/Films/Decay_2012/
cp: writing `/mnt/samba/statia/Films/Decay_2012/Decay_2012_720p.mp4': No space left on device
cp: failed to extend `/mnt/samba/statia/Films/Decay_2012/Decay_2012_720p.mp4': No space left on device
cp: closing `/mnt/samba/statia/Films/Decay_2012/Decay_2012_720p.mp4': No space left on device
statia@quokka:~/Videos/Decay_2012$ df -h
Filesystem                            Size  Used Avail Use% Mounted on
/dev/sda5                              29G   14G   14G  49% /
/dev/sdb1                             450G  226G  201G  53% /home
tmpfs                                 3.9G   72K  3.9G   1% /tmp
//192.168.178.1/WD-10EADSExternal-01  932G  184G  748G  20% /mnt/samba

(snipped out irrelevant sections of output)

statia@quokka:~/Videos/Decay_2012$ ls -l
total 4525804
-rw-rw-r-- 1 statia statia 4634399046 Dec 11 23:03 Decay_2012_720p.mp4

```Anyone have an idea what's going on and how to fix it?
I wonder if it is because the size of the file is larger then my /tmp partition, which lives in RAM and is 3.9G. Is there a time to temporarily increase /tmp? I have 8G RAM in total.

---

### Post by steeldriver on 2012-12-20
or possibly because the remote filesystem is FAT32... ?

---

### Post by Statia on 2012-12-20
Good one! I had not thought of that. That is entirely likely, the disk is not mine but my gf's, she has a MacBook and a laptop with XP (and Linux Mint, recently), so it is quite likely that it has been formatted FAT32.
I made her other external disk an NFS share for my home brewn NAS (EEE-PC 701 with Lubuntu 12.10), I copied the same file over there without a problem, but I guess that disk is NTFS formatted.

(BTW: the size of /tmp is not related, I tried the cp again while watching /tmp, it did not change while the cp process was running)

---

