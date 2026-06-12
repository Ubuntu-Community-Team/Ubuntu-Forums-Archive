---
title: "XFS - filesystem checking needed like with EXT3?"
date: 2007-08-27
forum: General Help
---

### Post by kahrn on 2007-08-27
I just started using the XFS filesystem on my Pentium III system and I just wondered if it had any need for filesystem checking every x amount of boots like with EXT3. If so, do I need to enable it?

---

### Post by kidders on 2007-08-28
Hi there,

XFS (and almost all other) filesystems are checked at *every* boot. Ext3 checks are exceptionally slow though, which is the main reason most Linux systems tend to skip them the majority of the time. If you really wanted to, you could probably configure your XFS filesystems to behave similarly (eg skip boot-up checks 19 times out of 20), but you wouldn't gain anything out of it.

---

### Post by s_g_robertson on 2007-12-05
> **kidders said:**
> Hi there,

XFS (and almost all other) filesystems are checked at *every* boot. Ext3 checks are exceptionally slow though, which is the main reason most Linux systems tend to skip them the majority of the time. If you really wanted to, you could probably configure your XFS filesystems to behave similarly (eg skip boot-up checks 19 times out of 20), but you wouldn't gain anything out of it.

I have a disk with an XFS filesystem mounted soley for storing largish(1Gb+ mythtv recordings)  My system runs continuously, unless I break something.  Very,very occasionally I have had a problem with that seems to have been resolved by running xfs_check.  To be honest I'm not certain what has caused and I don't seem to have suffered nay data loss though I can't be certain.

Is there anything that I can/should be running periodically to check the health of this disk.

Thanks

Stephen.

---

### Post by Denis on 2007-12-05
> **s_g_robertson said:**
> I have a disk with an XFS filesystem mounted soley for storing largish(1Gb+ mythtv recordings)  My system runs continuously, unless I break something.  Very,very occasionally I have had a problem with that seems to have been resolved by running xfs_check.  To be honest I'm not certain what has caused and I don't seem to have suffered nay data loss though I can't be certain.

Is there anything that I can/should be running periodically to check the health of this disk.

Thanks

Stephen.

You can take a look at the SMART information of that disk. (if your disk has SMART, most new disks have). 

Install the smartmontools package and check out what smartctl has to say. There's a good explanation on this website: [http://www.captain.at/howto-linux-smartmontools-smartctl.php](http://www.captain.at/howto-linux-smartmontools-smartctl.php)

It's a good idea to monitor that info, when you're unsure about the status of the harddisk.

---

### Post by atlfalcons866 on 2007-12-05
all journaling file systems are checked at everyboot. fsck is not doing a full fs check it is just replaying the journal to see if the journal is clean.

---

### Post by s_g_robertson on 2007-12-05
> **Denis said:**
> You can take a look at the SMART information of that disk. (if your disk has SMART, most new disks have). 

Install the smartmontools package and check out what smartctl has to say. There's a good explanation on this website: [http://www.captain.at/howto-linux-smartmontools-smartctl.php](http://www.captain.at/howto-linux-smartmontools-smartctl.php)

It's a good idea to monitor that info, when you're unsure about the status of the harddisk.

Thanks very much for that.  I've set that up to do some scheduled monitoring.  At first look the short test didn't report any problems so fingers crossed the disk is not on its way out just yet.

Thanks

Stephen.

---

### Post by s_g_robertson on 2007-12-06
> **atlfalcons866 said:**
> all journaling file systems are checked at everyboot. fsck is not doing a full fs check it is just replaying the journal to see if the journal is clean.

Sorry i don't quite follow.  Do you mean by that the the checking done at each boot if not a full fs check?  

I found that fsck run from the command line didn't do anything for the XFS system but xfs_check fixed the problem.

Stephen.

---

### Post by atlfalcons866 on 2007-12-06
here is my fsck log at start up
Log of fsck -C -R -A -a 
Thu Dec  6 09:31:01 2007

fsck 1.40.2 (12-Jul-2007)
/dev/sda2: clean, 9087/17465344 files, 2442038/34911253 blocks

Thu Dec  6 09:31:01 2007
----------------

it didnt do  a full fsck it did a replay of the journal to see if the file system is consistent.

---

### Post by s_g_robertson on 2007-12-06
Thanks for that.  That makes some sense.  Should the SMART monitoring pick up any impending problems or should I also be doing something to keep an eye on filesystem problems.

Thanks

Stephen.

---

### Post by atlfalcons866 on 2007-12-06
smart has nothing to do with the filesystem. it just monitors the health of the hard disk like bad sectors

---

