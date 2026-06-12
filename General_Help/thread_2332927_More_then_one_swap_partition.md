---
title: "More then one swap partition"
date: 2016-08-05
forum: General Help
---

### Post by RobGoss on 2016-08-05
Hello everyone this may be a easy question but I just wanted to make sure what's needed

I have one machine that is already running **Windows 10** and **Ubuntu 16.04,** I wanted to add another distribution of Linux to this machine but wanted to make sure if I need to create another swap partition for the new installation. Ubuntu 16.04 already a swap partition do I add one for every installation I install of Linux

Thanks so much

---

### Post by howefield on 2016-08-05
One swap partition is all you need for multi booting Linux distros.

If a swap partition exists Linux will find and use it.

---

### Post by Dennis N on 2016-08-05
One swap partition shared by all Linux distros is all that's necessary.

---

### Post by QDR06VV9 on 2016-08-05
It is best to create A swap for each OS installed.
Short answer: You can use the same swap partition as the data in swap is not preserved from one boot to the next. It is totally normal to have multiple linux installations on a disk with a single swap.

There is one exception/caveat I know of, however: if you use hibernate (aka, 'suspend to disk'), hibernate uses your swap space for storage. If you then boot another system that also uses hibernate (or perhaps even one that doesn't), you could create some very nasty problems.
See This: [URL="http://unix.stackexchange.com/questions/5656/are-there-any-side-effects-when-two-distros-share-a-swap-partition"]http://unix.stackexchange.com/questions/5656/are-there-any-side-effects-when-two-distros-share-a-swap-partition

[/URL]

---

### Post by RobGoss on 2016-08-05
You know the best thing about Linux is the people that manage this forum, Thanks so much guys for your fast reply

I see some say one and some say more then one It's better to more then one option and I do appreciated it

---

### Post by mook765 on 2016-08-05
You don't need to create another swap-partition, you can use the already existing.
Just mount this existing partition during installation.
If you have separate /home-partition, it would be necessary to create one /home-partition for each distribution which you install, otherwise it would lead to conflicts with configuration files.

---

### Post by RobGoss on 2016-08-05
> **runrickus said:**
> It is best to create A swap for each OS installed.
Short answer: You can use the same swap partition as the data in swap is not preserved from one boot to the next. It is totally normal to have multiple linux installations on a disk with a single swap.

There is one exception/caveat I know of, however: if you use hibernate (aka, 'suspend to disk'), hibernate uses your swap space for storage. If you then boot another system that also uses hibernate (or perhaps even one that doesn't), you could create some very nasty problems.
See This: [URL="http://unix.stackexchange.com/questions/5656/are-there-any-side-effects-when-two-distros-share-a-swap-partition"]http://unix.stackexchange.com/questions/5656/are-there-any-side-effects-when-two-distros-share-a-swap-partition

[/URL]

How are ya Runrickus I don't use [COLOR=#000000]hibernate what so ever on any of my machines I have no need to but I see what you're saying[/COLOR]

---

### Post by QDR06VV9 on 2016-08-05
> **RobGoss said:**
> How are ya Runrickus I don't use [COLOR=#000000]hibernate what so ever on any of my machines I have no need to but I see what you're saying[/COLOR]

I am well thanks...Just wanted you to be aware is all.
Can be a bit tough to trouble shoot..if you lose Data when an OS goes to Hibernation and Booting or Resuming another OS from Hibernation.
That's the only message I wanted you to see.

---

### Post by howefield on 2016-08-05
There is no (easy) hibernate in Ubuntu but you may have in other distributions, so I suppose it could be an issue.

Fwiw, I'd recommend one swap partition and one /Data partition containing Documents, Downloads, Music ect ect for each installation to symlink to and /home in each partition/installation.

---

### Post by RobGoss on 2016-08-05
**Runrickus**, I grateful for you taking the time to point out what's needed for multi OS's, I'm chopping down my Windows partitions and so there will be none :grin: thank you so much

---

### Post by Dennis N on 2016-08-05
If you have more than one swap partition existing during OS installation, then they are all included in your fstab, and mounted thereafter by the OS. Case in point (see fstab below): At the moment, I have two HDs in this computer, and each HD happens to have a swap partition. Both swaps are currently mounted by the OS I am using. Yes, I suppose I could delete one of them from fstab, but I never bothered. 

```
dmn@Roxanne:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda10 during installation
UUID=bd26c257-2b33-4482-a0ad-f5eb3760f5da /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=fcfec85c-fb97-47b6-aaf3-8b5c0db6a168 none            swap    sw              0       0
# swap was on /dev/sdb5 during installation
UUID=0b8757d1-652f-4c31-94fb-02cf00afd7e8 none            swap    sw              0       0
# Label=Common-Files /sdv/sdb11
UUID=c3121154-ee33-418b-8c43-10377841e3c2 /mnt/Common-Files ext4 defaults 0 1

```

---

### Post by RobGoss on 2016-08-05
> **howefield said:**
> There is no (easy) hibernate in Ubuntu but you may have in other distributions, so I suppose it could be an issue.

Fwiw, I'd recommend one swap partition and one /Data partition containing Documents, Downloads, Music ect ect for each installation to symlink to and /home in each partition/installation.


Thank you sir for your expertise and advice it is much appreciated and respected

---

### Post by RobGoss on 2016-08-06
Thank you @**Dennis** for the clarification and point this out I have to decide which way is best for my new installation...

---

