---
title: "How can I obtain a path to HDD's device file?"
date: 2013-10-10
forum: General Help
---

### Post by Artif on 2013-10-10
There is a usual name for HHD's device file: 
**    /dev/vda** 

The is a usual name for a partition: 
**    /dev/vdaX** 
where X is a number. 

How can I obtain reliably all these names in a script or in any other way? What is a proper way to do it via Shell commands, via Perl code? Or, may be, there are other good and reliable ways? May be using another programming language? 

I may do: 

```
sudo parted --list --machine /dev/sda
``` 

It will display machine parseable output. Moreover, Parted supports GPT (Guided Partition Table, not MBR only), which is good for me. This is quite a good way for me. But I'm not shure, if there are another better and reliable ways.

---

### Post by theDaveTheRave on 2013-10-10
Have a look at the comunity wiki docs for [fstab]("https://help.ubuntu.com/community/Fstab"). it should give you some usefull info, and things to search for.

what are you hoping to acheive ?

David

---

### Post by Artif on 2013-10-10
> **theDaveTheRave said:**
> what are you hoping to acheive ?
David

Thank you for the link, it is useful.

I'm working on automated Linux OS installer. I'm searching for a way to organise complex partitions layout wiping and creation, and flexible code structure/architecture.

I need a graceful way to remove all data structures from a storage and, then, create my own layout. It seems to me, knowlege, about if a path exist, what is it, may be useful for me.

---

### Post by varunendra on 2013-10-10
> **Artif said:**
> There is a usual name for HHD's device file: 
**    /dev/vda** 

The is a usual name for a partition: 
**    /dev/vdaX** 
where X is a number. 

How can I obtain reliably all these names in a script or in any other way?

You can directly read the device files in the /dev directory, then trim the output as required. For example, the HDD device files in my /dev directory -
```
**~$ ls -1 /dev/sd??**
/dev/sda1
/dev/sda2
/dev/sda3
/dev/sda4
/dev/sda5
/dev/sda6
/dev/sda7
/dev/sda8
```

To get the device name (in case there are also sdb, sdc... etc. are present with valid partitions on them) -
```
**~$ ls -1 /dev/sd?? | cut -c 6-8 | sort -u**
sda
```
You can also use "**ls -1 /dev/sd? | cut -c 6-**", but it will also list the devices which doesn't have a valid partition on it (e.g. - a modem's card reader with no card in it)

To parse the partition numbers -
```
**$ ls -1 /dev/sd?? | cut -c 8-**
a1
a2
a3
a4
a5
a6
a7
a8
```

Or,
```
**$ ls -1 /dev/sd?? | cut -c 9**
1
2
3
4
5
6
7
8
```
..if only the last number is required. But that may be confusing if more than one device is present.

But anyway, I hope it gives you an idea to parse the parts of interest, then use them as they are or further strip them as you wish.

---

### Post by Artif on 2013-10-11
In practice the names can be different. They may include subdirectories, they may include several letters and several separated numbers in a single "word". The letters and numbers depends on underlying storage's physical and logical structure. It can be complex.

There is a part of kernel API:

[B]/proc/devices
/proc/partitions
[/B]
Full path can not be obtained from the files.

Also, there is the link [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

It seems there are two ways:
1) See sources. And do the job from scrutch.
2) Parse output from a tools and files (sfdisk, blkid, /dev/disk/*).

I'm wondering, are there any tools to enumerate all partitons on a device and have _reliable_ full path for each one? Reliable path - is a path, which is not generated using my own approximations. It must be obtained from a kernel API, from a reliable utility, as a ready for use item. It must not be constructed using my admissions.

---

### Post by steeldriver on 2013-10-11
I still don't really understand what you want or why, but there's also lshw e.g.

```
sudo lshw -C volume -short
```

---

### Post by Artif on 2013-10-17
Thank you for the help, it is useful.

There is one more way: **[FONT=courier new]sudo blockdev --report[/FONT]**

This will give a list with full path for each block device mentioned in [FONT=courier new]**/proc/partitions** file[/FONT]. The output can be parsed before and after partition creation. It is possible to use the difference between two outputs as a wanted full path to a partition. It is convenient to use a programming language with hash object support. It can be Perl, for example.

---

### Post by oldfred on 2013-10-17
This also lists lots of info, but mine shows both ata (includes DVD), scsi (4 drives but not DVD) & wwn(only 2 of 4 drives?) as same drives?

sudo ls /dev/disk/by-id

---

### Post by Artif on 2013-10-17
Some ways are more convenient, another ones less convenient, if one want them to be used by a program.

It's simple task, as a human to have a look on single (or two) command's output and decide what is what. Lots of a tools may present acceptable output. It's much harder to gain a [COLOR=#0000cd]reliable[/COLOR] tool, which can be used in a [COLOR=#0000cd]simple[/COLOR] way by an "artificial intelligence".

P.S. There is also **[FONT=courier new]lsblk[/FONT]** utility.

---

