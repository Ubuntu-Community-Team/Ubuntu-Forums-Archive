---
title: "A system freeze and hard reset broke my HDD"
date: 2014-04-03
forum: General Help
---

### Post by iammtxd on 2014-04-03
I have ubuntu(13.04) dual boot with windows 7 IN THE SAME DRIVE by wubi.
Suddenly ubuntu freezed, I didn't press hard reset but it restarted itself.
Then my HDD r/w light keep constantly on and loading Windows or Ubuntu extremely slow (At last not even booting)
Sometimes BIOS says SMART status bad, sometimes says HDD error

I tried:
 chkdsk /r <--file sys is RAW, failed
bootrec /fixboot /fixmdr <--Not working
safe mode<-- Loads extremely slow
Install an os on another drive, extremely slow access to the "broken" HDD(Can't even navigate to my stuffs)
TestDisk<-- Read error
Replace CMOS battery <--Nothing changed

I just want my data back....
Any idea how? I have been searching for solution for 3 days...
I don't care how the HDD is broken, I just want my data:(

---

### Post by sudodus on 2014-04-03
Welcome to the Ubuntu Forums :-)

Do not use the drive at all until you start the rescue operation!

I suggest that you try ***ddrescue***.

Install and run it from a separate drive, the boot drive (for example a persistent USB pendrive made from an Ubuntu desktop iso file).
```

sudo apt-get install ddrescue
```

Read carefully the instructions at the info page

```
info ddrescue
```

***Example 1***: is probably the best starting point, but you must change the device names to fit correctly your case. Use what you find from

```

sudo parted -l
sudo blkid

```

Check and double check! If you get it wrong you might overwrite and destroy your data instead of saving them.

> Example 1: Rescue a whole disc with two ext2 partitions in /dev/hda to
/dev/hdb.
Note: you do not need to partition /dev/hdb beforehand, but if the
partition table on /dev/hda is damaged, you'll need to recreate it
somehow on /dev/hdb.

     ```
ddrescue -f -n /dev/hda /dev/hdb logfile
     ddrescue -d -f -r3 /dev/hda /dev/hdb logfile
     fdisk /dev/hdb
     e2fsck -v -f /dev/hdb1
     e2fsck -v -f /dev/hdb2

```

Consider the present drive as the source. And get another drive of at least the same size an use it as the target drive. Then use the method to clone the source drive to the target drive.

---

### Post by iammtxd on 2014-04-03
> **sudodus said:**
> Welcome to the Ubuntu Forums :-)

Do not use the drive at all until you start the rescue operation!

I suggest that you try ***ddrescue***.

Install and run it from a separate drive, the boot drive (for example a persistent USB pendrive made from an Ubuntu desktop iso file).
```

sudo apt-get install ddrescue
```

Read carefully the instructions at the info page

```
info ddrescue
```

***Example 1***: is probably the best starting point, but you must change the device names to fit correctly your case. Use what you find from

```

sudo parted -l
sudo blkid

```

Check and double check! If you get it wrong you might overwrite and destroy your data instead of saving them.



Consider the present drive as the source. And get another drive of at least the same size an use it as the target drive. Then use the method to clone the source drive to the target drive.

Thank you for your information but I have decided to format the whole disk.
It has been too frustrating for me to fix this HDD for such a long time.

---

### Post by iammtxd on 2014-04-03
OK, the HDD is broken, windows can't format the HDD.

---

### Post by sudodus on 2014-04-03
If your personal data are backup up, you can just get a new drive. But if you need to rescue data from the failed drive, one way is ddrescue. Probably the safest way. After cloning the drive, you can use various tool on the copy to try to recover files. But if the failure has gone too far, ddrescue won't recognize the drive and cannot do it's job.

---

