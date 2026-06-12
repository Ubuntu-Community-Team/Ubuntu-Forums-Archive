---
title: "How to safely remove mdadm raid 1"
date: 2016-04-11
forum: General Help
---

### Post by Chris_Shelton on 2016-04-11
Hi,

My situation: I have the Ubuntu OS running in raid 1 on two identical disks and I am wanting to break the raid array, and just have the OS on one normal disk.

Has anyone got any experience with this?

I have searched around and seen a few forum posts, most notably this one: 

[http://ubuntuforums.org/showthread.php?t=1693950](http://ubuntuforums.org/showthread.php?t=1693950)

which looks good, but still does not seem to offer a concrete solution to this. I need to know whether this is something that can actually be done and is relatively safe to do.

My thoughts at the moment are to:

```
[COLOR=#000000][FONT=Verdana]boot from a livecd and then apt-get install mdadm. 
[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]sudo mdadm --zero-superblock /dev/sda1[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]sudo mdadm --zero-superblock /dev/sdb1[/FONT][/COLOR]
[FONT=Verdana][COLOR=#000000]etc...
[/COLOR][/FONT]
[COLOR=#000000][FONT=Verdana]remove /etc/mdadm/mdadm.conf from the remaining drive, and update /etc/fstab to mount the remaining drive by UUID, and finally update grub to reflect booting from the individual disk partition rather than the RAID array.[/FONT][/COLOR]
```

Does anyone notice any problems in doing this?

Thanks

---

### Post by Chris_Shelton on 2016-04-18
So nobody's ever come across this before and is willing to help?

---

### Post by howefield on 2016-04-18
> **Chris_Shelton said:**
> So nobody's ever come across this before and is willing to help?

The 3 people who have viewed your thread may not have come across your issue, but it won't be true that nobody has. Give your thread a better chance of being seen by giving it a daily bump. :)

---

