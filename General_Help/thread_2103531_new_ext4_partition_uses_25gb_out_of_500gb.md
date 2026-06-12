---
title: "new ext4 partition uses 25gb out of 500gb?"
date: 2013-01-10
forum: General Help
---

### Post by sdowney717 on 2013-01-10
the ntfs partition using only 80mb
Huge difference, hust installed a new 1tb drive and split it in half with gparted.

Is that normal?
I dont like idea of losing 25gb.

---

### Post by LewisTM on 2013-01-10
This space is called [root reserve]("http://www.unixtutorial.org/commands/tune2fs/"). It's space reserved for the root user (superuser). By default, it's 5% of your drive. That's way too much for today's large drives.
You can execute this command on a mounted filesystem to bring it down to 1% (or less).
```
sudo tune2fs -m 1 /dev/sda1
```
Change sda1 for your device.

Cheers!

---

### Post by sdowney717 on 2013-01-10
Thanks mucho, that brings it down to 5gb

```
scott@scott-P5QC:~$ sudo tune2fs -m 1 /dev/sda2
tune2fs 1.42 (29-Nov-2011)
Setting reserved blocks percentage to 1% (1220935 blocks)
scott@scott-P5QC:~$ 

```

---

### Post by sdowney717 on 2013-01-10
Is even 5gb too much space?
If so, then what to set it at.

---

### Post by oldfred on 2013-01-10
Did you do a default install with just / (root) and swap? I normally suggest smaller root and larger /home. Then the reserved in / does not matter so much and you can make the reserved small if you want in /home or your data partitions.

I use 25GB but keep /home inside / and use data partitions. My actual use is about 9GB, so even 25 is generous, but I am aggressive in moving any data including some hidden folders like Firefox & Thunderbird to my data partitions.

You do have to manage space. Windows NTFS partitions really work best with 30% free and at 10% free you may take days to run a defrag on a larger partition and system will be noticeably slower. Often the real reason users complain about Windows being slow.

---

