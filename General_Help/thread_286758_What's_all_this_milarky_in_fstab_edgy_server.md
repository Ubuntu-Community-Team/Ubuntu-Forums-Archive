---
title: "What's all this milarky in fstab edgy server"
date: 2006-10-28
forum: General Help
---

### Post by hairshirt on 2006-10-28
went into ftab on my new Edgy Server install.  Needed to add second drive: hdb1 and setup quora. What's all this cobblers? (marked with the red sq brackets...

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
[COLOR="red"][[/COLOR]UUID=e356c333-6f0d-4a83-b916-70679547190e[COLOR="red"]][/COLOR] /               ext3    defaults,errors=remount-ro,usrquota,grpquota 0       1
# /dev/hda5
[COLOR="red"][[/COLOR]UUID=d58fe4dc-aae4-4683-8b23-9942d64b9016[COLOR="Red"]][/COLOR] none            swap    sw              0       0
/dev/hdb1       /media/shared                             ext3    defaults,errors=remount-ro 0       1
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by Fass on 2006-10-28
Instead of giving the device explicitly (as in dev/hdX)), Edgy's fstab uses UUIDs instead. UUIDs are unique identifiers generated when the file system is created. If you change how the hd is connected to your system (for example primary/secondary master/slave for IDE) the UUID doesn't change, whereas the device node can change. Using UUIDs makes the association between mount point and partition more robust.

You can find out a partition's UUID by doing ```
sudo vol_id -u <partition>
```

---

### Post by pinoyskull on 2006-10-28
i was wondering about this UUID thing earlier, now i know :)

---

### Post by hairshirt on 2006-10-28
Thanks for clearing that up for me...

---

### Post by megadyptes on 2006-10-28
Okay, maybe someone could clarify this for me...

I'm adding a second hard drive to my edgy PC. Ordinarily, I'd have added a line similar to that shown below to fstab.

> 
# /dev/hdb1
/dev/hdb1 /media/disc2 ext3 defaults,errors=remount-ro 0 1


Can I still do this, or do I have to use this UUID instead and add something like this

> 
# / dev/hdb1
UUID=Random123Sequence456 /media/disc2 ext3 defaults,errors=remount-ro 0 1


Thanks in advance

---

### Post by bsussman on 2006-10-28
You can still use the old form.

at a command prompt, try typing:

```
man 5 fstab
```then you too can read the documentation on how fstab is formatted.

---

### Post by megadyptes on 2006-10-28
When the PC's back in one piece I'll do that! Just out of curiosity though, would to the two versions above be treated as equivalents, or would it barf if I just went for the UUID version?

---

### Post by bsussman on 2006-10-28
> **megadyptes said:**
> When the PC's back in one piece I'll do that! Just out of curiosity though, would to the two versions above be treated as equivalents, or would it barf if I just went for the UUID version?

I do not understand your question.  

The variants are different ways of identifying the hardware device.  The UUID variant is not necessarily a random string and it does need to be assigned to the disk in question.

More homework :mrgreen::
```
man uuidgen
man tune2fs
```There may be a more humanistic discussion of this stuff but I have not looked enough to find it.

Using UUID is more reliable as it does not change if you change hardware connections (moving a disk).

---

### Post by megadyptes on 2006-10-28
> I do not understand your question.

What I was trying to say was: If I have an fstab file where I have the line that successfully mounts the new hard drive

> 
# /dev/hdb1
/dev/hdb1 /media/disc2 ext3 defaults,errors=remount-ro 0 1


Would it be treated identically to one where I had the lines, when I'd determined the UUID using *[COLOR="Blue"]vol_id -u /dev/hdb1[/COLOR]*

> 
# /dev/hda1
UUID=e356c333-6f0d-4a83-b916-70679547190e ext3 defaults,errors=remount-ro 0 1


Or is one version prefereable to the other?

I'll try it out in a minute and see what happens....:confused:

---

### Post by bsussman on 2006-10-28
> **megadyptes said:**
> 
Or is one version prefereable to the other?


They both work reliably, provided you do not move hardware around.

UUID is preferred in dynamically reconfigured environments.

Being in unix a long time and not prone to a lot of moving disks around, I prefer the old way ( /dev/xxxx ) notation.

UUID ensures that you can copy the line to anywhere, and know that that filesystem will mount where you want it.

---

### Post by drpaul on 2006-10-28
If you have a uuid how do you determine where it is connected? [I can't look at man because I don't have Edgy installed.]

Thanks

Paul

---

### Post by EmmEff on 2006-10-28
# ls -l /dev/disk/by-uuid/

shows the mapping between UUID and old-style /dev/[s|h]daxx

---

### Post by nardis_Miles1 on 2006-10-31
The new UUID format seems pretty opaque. I built the disk with a partition called /scratch, knowing that I wanted to change its name to /home. In the past, this was a simple edit of /etc/fstab. Now it's a big WTF?? Is there a straight forward (meaning vi, ten keystrokes and reboot) way of doing this?

---

### Post by nardis_Miles1 on 2006-10-31
Never mind!! I think I get it.

---

### Post by relix on 2006-11-08
It's nice. There's a downside to it too though: if you format one of your partitions, you need to change the UUID in fstab.

So basically it's just a question of what happens more often for you: changing the physical location of the disks, or formatting the partitions.

If the first is the case, you're better off using UUID's. If the latter aplies more to you, then use /dev/*

---

### Post by amiga_os on 2006-11-18
> **relix said:**
> It's nice. There's a downside to it too though: if you format one of your partitions, you need to change the UUID in fstab.

So basically it's just a question of what happens more often for you: changing the physical location of the disks, or formatting the partitions.

If the first is the case, you're better off using UUID's. If the latter aplies more to you, then use /dev/*

Yup... the latter applies to me.  If you try and dual boot... and so you're installing another operating system AFTER you've installed Edgy... then this can result in a slew of fsck errors - and ubuntu actually stalling boot.

One of the easiest ways for me is to back up my /boot partition... let the installer reformat it, and reformat it's own partition, then copy back /boot (I often have /boot/ubuntu and /boot/fedora, and bind those directories to /boot for each distro... allowing the distros to keep their own kernels updated).

Of course... it's taken me a couple of weeks to find this thread... I've been reformatting and reinstalling for ages now!  Thinking there was a filesystem error that fsck couldn't purge!

An 'Advanced' tab in the Ubuntu installer, with a checkbox stating:

"Dual boot compatible - I intend to install other operating systems, please configure my system accordingly."

Would be really helpful.  Then the installer could use UUIDs or /dev in fstab accordingly.  Now I understand why Edgy cried when I tried installing two versions of Ubuntu!

Here's a question... when I copy a partition using GParted (which used to work if you wanted to dual boot [K]Ubuntu), will the UUIDs be the same?

---

### Post by wgscott on 2006-12-03
I think I just got bit by the new format.  I am not absolutely certain of this.  I have not moved or reformatted any disks in a couple of years.  

For whatever reason, ubuntu began to treat one, and then both slave drives as read-only.  This behavior spread to my /home partition on my main drive, and then to my root partition.

I was essentially locked out of my computer until I figured out that I could boot from a demo disk, use the terminal to manually mount the root partition at a temporary mount point, and replace the new edgy-formatted UUID fstab with the old one that used the device names.

Now I am back to a functional computer, but that is five hours of my life I will never get back.

I think the switch, without giving the user the choice (or at least I missed it), is a bit heavy-handed.  

The part I don't get is the problem only appeared a month after the upgrade.

](*,)

---

### Post by maestrobwh1 on 2006-12-17
Just what I was looking for... a way to find a partition's UUID to add it back into fstab!

---

### Post by steve.horsley on 2006-12-18
Where is the UUID hidden? If it's before or outside of the filesystem then I don't see how reformatting would change it. But if it's inside the filesystem, doesn't that mean that the UUID reading code has to understand every possible filesystem format?

---

### Post by tormod on 2006-12-19
> **steve.horsley said:**
> Where is the UUID hidden? If it's before or outside of the filesystem then I don't see how reformatting would change it. But if it's inside the filesystem, doesn't that mean that the UUID reading code has to understand every possible filesystem format?
Yes, the UUID reading code (libvolume_id) has to understand every possible filesystem. BTW, as an alternative to UUID=, you can use LABEL= in /etc/fstab.

---

### Post by steve.horsley on 2006-12-20
Interesting. Thanks.

---

### Post by dvarsam on 2006-12-20
Hello!

[QUOTE=bsussman]UUID is preferred in dynamically reconfigured environments.

Being in unix a long time and not prone to a lot of moving disks around, I prefer the old way ( /dev/xxxx ) notation.

UUID ensures that you can copy the line to anywhere, and know that that filesystem will mount where you want it.[/QUOTE]

Sorry, but I can't seem to understand what are the "gains" involved in using UUID in Fstab...
Is is used for security reasons?
(e.g. so that the mounted Partition is not available for other Networked Users?)
Can you provide an example/user case?

Thanks.

---

### Post by mannheim on 2006-12-21
> **dvarsam said:**
> 
Sorry, but I can't seem to understand what are the "gains" involved in using UUID in Fstab...
Is is used for security reasons?
(e.g. so that the mounted Partition is not available for other Networked Users?)
Can you provide an example/user case?


I think it is supposed to deal with the following problem:

User joe has an external usb hard-drive connected to his pc, which is used for backup. This drive generally apppears as /dev/sda. His old-style fstab file contains a line to mount /dev/sda at /mnt/backup. One morning, joe boots his computer, with a thumb drive still connected to another usb port. On boot-up, the operating system decides the thumb-drive is /dev/sda and the external hard-drive is /dev/sdb. Following the old-style fstab file, the operating system mounts the thumb drive at /mnt/backup. That evening, joes backup script fails, because it tries to backup to the thumb drive instead of the external hard drive.

There are no good rules about which drive is going to be identified as /dev/sda etcetera. These days, the configuration of drives attached to a pc is a much more dynamic thing than it was when the the "/dev/sdx /dev/hdx" labeling was first designed.

---

### Post by azziman on 2006-12-25
what is the difference of having the very last part of the UUID statement with a 

0 1 

or

0 0

and i suppose i would have to put in the fstab this for it to work:

# / dev/hdc1
UUID=[UUID#] /media/hdd3 ext3 defaults,errors=remount-ro 0 1

---

### Post by tormod on 2007-01-06
> **azziman said:**
> what is the difference of having the very last part of the UUID statement with a 0 1 or 0 0

man fstab
  ```
       The sixth field, (fs_passno), is used by the fsck(8) program to  deter-
       mine the order in which filesystem checks are done at reboot time.  The
       root filesystem should be specified with a fs_passno of  1,  and  other
       filesystems  should  have a fs_passno of 2.  Filesystems within a drive
       will be checked sequentially, but filesystems on different drives  will
       be  checked  at  the  same time to utilize parallelism available in the
       hardware.  If the sixth field is not present or zero, a value  of  zero
       is  returned  and fsck will assume that the filesystem does not need to
       be checked.
```

---

