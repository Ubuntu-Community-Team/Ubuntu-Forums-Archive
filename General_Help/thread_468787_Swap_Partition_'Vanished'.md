---
title: "Swap Partition 'Vanished'"
date: 2007-06-09
forum: General Help
---

### Post by haelen on 2007-06-09
Hi,

My system did its 'Hda1 mounted 30 times' check today and the message  '*Activating swap [fail]' appeared followed later by 'Unable to find swap-space signature'

I've never seen that before, and I'm almost certain that I've had a swap partition (would it be created by default at Kubuntu install?).

Thanks,
Tim

---

### Post by Znupi on 2007-06-09
Open up **System Monitor** (**System -> Administration**) and go to the **Resources** tab. What does it say under **Used swap:** ?

---

### Post by haelen on 2007-06-10
0 Bytes of 0 Bytes :(

---

### Post by coffeecat on 2007-06-10
**haelen**, I hope you're still following this thread. I don't know why you're getting that error - never seen it before - but it suggests to me that either the swap partition has disappeared, or is not being mounted, or the partition table has been corrupted somehow.

Three suggestions. From a terminal do:

```
sudo fdisk -l
```and post the output. Then we can see what partitions you have. That's a lower-case L for -l by the way.

Next, from a terminal:

```
cat /etc/fstab
```and post the output again. (Don't forget you can copy and paste from a terminal to the message field when replying. :) ) That way we can see whether the fstab entry corresponds with your partition layout. I'm sure it will, but it's as well to check.

Thirdly, assuming that's Ubuntu/gnome you're running and not Kubuntu (*** see edit below ***), install gparted via Synaptic. Open it from System > Adminstration > Gnome partition editor and tell us what that is saying. If it shows a corrupted or otherwise poorly swap partition, I guess you could simply reformat the partition as swap and then reboot.

**Edit:** Silly me. I saw your reference to Kubuntu as soon as I had posted. OK - instead of Gparted you could get Qtparted. Or try gparted and see how many dependencies it wants to drag in. I prefer Gparted but it's designed for the Gnome desktop whereas Qtparted is for KDE. Oh - and if you're using Kubuntu your package manager is probably the grossly misnamed 'Adept'. :( Can I suggest you install Synaptic while you're about it? It will be a revelation after Adept - in my view at least. :wink:

---

### Post by haelen on 2007-06-10
Hi.

Thanks for the prompt reply:

```
Disk /dev/hda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3497    28089621   83  Linux
/dev/hda2            3498        3649     1220940    5  Extended
/dev/hda5            3498        3649     1220908+  82  Linux swap / Solaris

Disk /dev/sda: 2047 MB, 2047868416 bytes
255 heads, 63 sectors/track, 248 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          10       80293+   0  Empty
/dev/sda2              11         248     1911732    b  W95 FAT32

```

and

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=e9bfaa4b-8d84-45bd-9a50-944d019c4254 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=555f671c-6887-4afe-ab29-383b71e60301 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

/tmp/app/1/image /tmp/app/1 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/2/image /tmp/app/2 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/3/image /tmp/app/3 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/4/image /tmp/app/4 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/5/image /tmp/app/5 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/6/image /tmp/app/6 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/7/image /tmp/app/7 cramfs,iso9660 user,noauto,ro,loop,exec 0 0

```

Gparted says:

[IMG]http://www.timrowe.co.uk/images/partitions.png[/IMG]

---

### Post by tpg on 2007-06-10
Try reformatting your swap partition using GParted (or whatever you feel like using). It should be /dev/hda5, but GParted doesn't know what it is, which makes me think that it's been corrupted somehow.

Then, if you reboot, swap should work again. If it doesn't, it may be to do with the partition UUIDs in fstab... but we'll come to that later if necessary! :)

---

### Post by coffeecat on 2007-06-10
Yes, I agree with tpg. Even though fdisk is reporting hda5 as a swap partition, gparted is having problems with it so, if I was in your situation, I would simply reformat hda5 as swap.

However, there is still one issue to deal with. If you reformat hda5, the UUID for that partition will almost certainly change and when you next boot up Ubuntu will still moan at you about the swap partition. You have two options. For both reformat hda5 first.

1 - open a terminal and run:

```
blkid
```This will give you data for all your partitions including the UUIDs. Now you have to edit /etc/fstab

```
gksudo gedit /etc/fstab
```and change the UUID in this bit:

> # /dev/hda5 -- converted during upgrade to edgy
UUID=555f671c-6887-4afe-ab29-383b71e60301 none swap sw 0 0**OR**

2 - Edit the bit I've quoted with gedit so that it appears as:

```
/dev/hda5      none      swap      sw    0 0
```There are pros and cons for each way.

**Edit:** I've done it again, haven't I? You're using Kubuntu. :lol: Er - rather than 'gksudo gedit /etc/fstab' open whatever text editor you normally use, but with administrative privileges. I'd tell you what to do - I can do it fine in PCLinuxOS or Mepis - but I was using the Kubuntu desktop this afternoon and trying to open a text editor with kdesu wouldn't work. Goodness knows what was wrong. Eventually I gave up, logged out and then back in again to the gnome desktop.

**Edit 2:** Must have been something to do with my laptop installation. I've logged into the Kubuntu desktop on my desktop machine (if that makes sense) and 'kdesu kate /etc/fstab' works OK. Albeit with a few mumbles and grumbles at me.

---

### Post by tpg on 2007-06-10
As a KDE fan, I can assure you the command is kdesu! :D

---

### Post by haelen on 2007-06-10
Ok Thanks.

So I should basically delete this:

```
# /dev/hda5 -- converted during upgrade to edgy
UUID=555f671c-6887-4afe-ab29-383b71e60301 none swap sw 0 0
```

and replace it with this:

```
/dev/hda5      none      swap      sw    0 0
```
?

Or have I misunderstood.

Reformatting hda5 to linux-swap worked fine BTW.

Tim

---

### Post by tpg on 2007-06-10
Yes, that's the easiest way to do it. Then reboot, and it should all work ... :)

---

### Post by haelen on 2007-06-10
Thanks all. Seems fine now!

Best,
Tim

---

