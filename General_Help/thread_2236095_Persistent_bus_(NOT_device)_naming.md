---
title: "Persistent bus (NOT device) naming"
date: 2014-07-24
forum: General Help
---

### Post by Wolfram_Donat on 2014-07-24
I'm currently running Ubuntu 13.10 on a system with a CFAST card as my boot disk and two SATA hard drives for storage. My application currently saves data to one of the SATA drives until it's 95% full, then saves to the other drive. Here's the rub: one of those drives is in a hot-swap bay (easy to remove) and the other is more internal and hard to get to. I would *really really* love to record to the hot-swap-bay drive first, then the internal. I can't code to write to /sda first, then /sdb, because I know there's no guarantee that the next time I boot they'll have the same numbers. 

I can't use udev rules, or UUID or even anything in the /sys/ tree, because the machine will be released to a client who will be able to insert whatever drives he chooses into the two slots. In short, I need a way to ensure that the hot-swap-bay is always /dev/sda (or whatever) regardless of what disk is placed in there. All of my research points to naming the device, but not naming the bus, since it seems to be a lottery at boot to determine which slot gets which letter.

Is there a way to persistently name a bus?

---

### Post by oldfred on 2014-07-25
You can mount by label instead of device like /dev/sda or UUID. Then create labels to match what you want to do.

```
fred@fred-Precise:~$ ls /dev/disk/by-label -lah
total 0
drwxr-xr-x 2 root root 480 Jul 21 13:55 .
drwxr-xr-x 8 root root 160 Jul 20 12:46 ..
lrwxrwxrwx 1 root root  10 Jul 20 17:46 backup -> ../../sda2
lrwxrwxrwx 1 root root  10 Jul 21 13:55 bios_gpt -> ../../sdc4
lrwxrwxrwx 1 root root  10 Jul 20 17:46 Data -> ../../sdc6
lrwxrwxrwx 1 root root  10 Jul 21 13:55 EFI -> ../../sdd1


```

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

> Alternately syntax to refer to partitions : 


[LIST]
[*]Device : /dev/sdxy 
[*]Label : LABEL=label 
[*]
[/LIST]



---

