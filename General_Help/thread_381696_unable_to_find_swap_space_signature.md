---
title: "unable to find swap space signature"
date: 2007-03-11
forum: General Help
---

### Post by addisor on 2007-03-11
Good morning, just booted up this morning a have found "unable to find swap space signature" and my hibernate/suspend does not work, just tried it and found that out. I've looked at a few posts and am a bit worried about my ability to rectify the problem. Anyone feel like talking me through the problem and solution?

Here's 

rob@rob-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           884        366        518          0         10        193
-/+ buffers/cache:        162        722
Swap:            0          0          0

rob@rob-desktop:~$ sudo swapon -va
swapon on /dev/disk/by-uuid/268ab357-397d-4a79-a99a-280db07b8d18
swapon: /dev/disk/by-uuid/268ab357-397d-4a79-a99a-280db07b8d18: Invalid argument

---

### Post by Kateikyoushi on 2007-03-11
Please post the output of this command.

```
fdisk -l
```

---

### Post by addisor on 2007-03-11
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9375    75304656   83  Linux
/dev/hda2            9376        9729     2843505    5  Extended
/dev/hda5            9376        9729     2843473+  82  Linux swap / Solaris

---

### Post by Kateikyoushi on 2007-03-11
One more thing, list your fstab.

```
cat /etc/fstab
```

Or if you know how can change the /dev/dha5 entry from uuid to the old /dev/hda5 line.

---

### Post by addisor on 2007-03-11
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=565540eb-bdaf-4de8-b3c1-991117c5d964 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=268ab357-397d-4a79-a99a-280db07b8d18 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by addisor on 2007-03-12
bump

---

### Post by strabes on 2007-03-12
Perhaps it has something to do with your upgrade from dapper to edgy? I'm sure if you install feisty it will fix your problem. I'd wait to see if someone else can fix your problem though.

---

### Post by jc15 on 2007-03-12
I'm having same problem.
Is there any ideas on how to fix this?
I tried to search through /var/logs and found nothing about this error messages. I even can't read what is going on.

---

### Post by addisor on 2007-03-12
I just ran

 sudo mkswap /dev/hda5 then

 sudo swapon /dev/hda5

This seems to have worked, not sure how, fingers crossed!!!

---

### Post by vadriaan on 2007-03-12
Having (sorry, had) the same problem. Thanks Addisor, your advice worked. the trick seems to be the mkswap since making a swap partition in any other way does not work.

evidence: (used to get no reply)
cat /proc/swaps
Filename                                Type            Size    Used    Priority
/dev/hda3                               partition       635032  0       -1

---

### Post by flostre on 2007-03-20
I am having trouble here too. It is not so easy to fix however.

```
mkswap /dev/hda6
```

didn't work, only

```
mkswap -cv /dev/hda6
```

Only then could I

```
swapon /dev/hda6
```

and swapon -s listed /dev/hda6. Then I tried suspend to disk (though I now realize that it is probably unrelated), which hadn't worked before, and: It still didn't work. Moreover, after reboot I again had the same problem: No swap device, and vanilla mkswap didn't work.

I, too, think that this is related to my upgrade to edgy.


Edit: I partially solved the problem!
I did the above mentioned mkswap -cv, then I replaced the UUID identification (UUID=123...xyz) of the swap device in /etc/fstab by the good ol' /dev/hda6.

Suspend to disk still doesn't work, though. :(

flostre

---

### Post by weemikey on 2007-08-28
Thanks Addisor, that <mkswap> wrinkle worked like a charm.
I'd been having a lot of hang-ups and slow - slow responses.  Let's hope things go a llittle faster now.
weemikey

---

