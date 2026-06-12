---
title: "[SOLVED] Manual partitioning of dual booting linux machine"
date: 2008-06-23
forum: General Help
---

### Post by geo909 on 2008-06-23
Hello everybody,

 In case I want to manually partition a disk to carry a dual boot system what should I be careful of?

 Let's say I use gparted. I make 3 partitions, the first will be a primary partition, formatted to ntfs (to hold xp) right?

 Then I make 2 partitions, a swap one and a ext3 for linux.
Those two should be "primary" or "logical"? What about the "flags"?
I know nothing about them. Should I set any particular flags to any of my three partitions?

    Thank you very much

---

### Post by rraj.be on 2008-06-23
I think there is no need for any flag modification and all.

All you need is to set your Ext partition mount point to  
```

 /
```

And regarding your swap it should be about 1.5 GiB.

If you are installing windows xp after installing ubuntu you should reinstall your GRUB as it will be overwrite by your window's.

to reinstall GRUB 

```
boot into live cd.
```

open terminal

type

```
sudo grub

find /boot/grub/stage1
```

if it returns like ```
(hdX,Y)
```

type

```
root (hdX,Y)

setup (hdX)

quit 

sudo reboot
```

---

### Post by danwood76 on 2008-06-23
A windows partition should always be your first primary partition, otherwise it gets upset.

swap should be the size of your RAM or 1GB if you have less than that.

I always create my linux partitions all on the extended partitions, I normally alocate 2GB to swap, 10GB to / and the rest to /home.
The /home is really useful if you ever need to reinstall having it on the same partition as / makes it harder to reinstall/upgrade IMO.

---

### Post by bodhi.zazen on 2008-06-23
First, at least one partition must be flagged as "boot".

Second, windows must be on a primary partition, does not matter if it is first, second, third, or fourth.

Ubuntu and swap and home can go into primary or extended (logical) partitions.

[http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

Last, in general:

swap = RAM X 2 , max 1 Gb unless you are using hibernate or suspend in which case you will want swap = RAM.

---

### Post by geo909 on 2008-06-23
EDIT:Hadn't see bodhi.zazen's reply. Think I understood what I wanted to now.


Thank you for your answers.

@rraj.be No, I will install Windows first, so no need to reinstall grub.


So I make a primary partition and then two more.
They will be of what kind? Primary or Logical?

 I have 256MB of ram and 20GB of HD space. I will give windows something like 7GBs. I'll just have them sit there in case I need something that isn't compatible with linux, so 7GB is too much already. 
 I have low ram. Is 1 GB of swap ok or should I dedicate more?

 The /home partition issue is quite interesting, Ive never thought about it. So I just make the partition (primary?Logical?) and during the setup I choose to put my home folder in /home partition, right?

---

