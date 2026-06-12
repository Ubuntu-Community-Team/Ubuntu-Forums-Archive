---
title: "Ubuntu boot to BusyBox"
date: 2019-04-06
forum: General Help
---

### Post by emians on 2019-04-06
Hi all,

I installed ubuntu studio recently, I was working on setting up my printer, and on reboot this morning I got  this screen:

[ATTACH=CONFIG]282974[/ATTACH]

any idea what's on and how to proceed from this without a clean OS installation?

thanks

---

### Post by Rubi1200 on 2019-04-06
Hi,

Boot with a LiveCD/USB and post the results of the boot info summary (link in my signature).

Note, please do not repair just post the summary here so we can advise further.

One point to clarify, you have LVM setup correct?

Thanks.

---

### Post by emians on 2019-04-06
From the screen I get, supposedly not, LVM has no good set up. Can I ask what LVM is?

here screenshots:


[ATTACH=CONFIG]282975[/ATTACH][ATTACH=CONFIG]282976[/ATTACH]

---

### Post by Rubi1200 on 2019-04-06
From the first screenshot it appeared you might have LVM:
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)

Please clarify, is Ubuntu Studio the only operating system or do you have others?

If yes, did you install on the entire drive or do you have other partitions?

From the liveCD/USB please run this command and post the output here:

```
sudo fdisk -l
```

---

### Post by emians on 2019-04-06
Yes, Ubuntu Studio is the only OS on hard drive. No partitions.

sorry for tilted jpg!

[ATTACH=CONFIG]282977[/ATTACH]

---

### Post by Rubi1200 on 2019-04-06
Okay, just so I understand your setup:

1. /dev/sda2 is your Ubuntu boot partition and /dev/sda3 is home and root partition?

2. what is /dev/sdb, an external drive, CD drive?

I just want to make sure we are on the same page before moving ahead.

Thanks.

---

### Post by emians on 2019-04-06
sda2 I don't know.

sda3 should be home and root partition.

/dev/sdb is an SSD, an external USB drive mounted with Ubuntu Studio, supposedly.

---

### Post by Rubi1200 on 2019-04-06
From the liveUSB please run this command:

```
sudo fsck -N /dev/sda
```

I am being cautious, so the -N flag should return an error code indicating what should be done (not what will be done if you run the command).

Post back the output so we can go forward.

---

### Post by Dennis N on 2019-04-06
According to the image in post #5, there is no LVM partition on sda or sdb. As evidence of LVM install in post #1, the system is looking for a volume group (ubuntu-studio-vg) which in turn contains the root logical volume. But, it appears it has been deleted:

fdisk -l would show LVM physical partitions as type: Linux LVM

To illustrate, this is from my system's output of fdisk -l:

```
Device         Start       End   Sectors   Size Type
/dev/sda1       2048    165887    163840    80M EFI System
/dev/sda2     165888 204965887 204800000  97.7G Linux LVM
(more output not shown)

```

You don't show any partitions of this type at all, which is why I suspect it has been deleted. I think the only remedy is to reinstall.

---

### Post by emians on 2019-04-06
Output:

fsck from util-Linux 2.32
[/sbin/fsck.ext2 (1) -- /dev/sda] fsck.ext2 /dev/sda

---

### Post by emians on 2019-04-06
Thanks Dennis N.

I will.

Any idea how the root logical volume could have been deleted?

cheers

---

### Post by Dennis N on 2019-04-06
> **emians said:**
> Thanks Dennis N.

I will.

Any idea how the root logical volume could have been canceled?

Either that, of the LVM partition that was once there has been reformatted as a standard linux filesystem (like ext4) without deleting the partition. If that is what happened, it was probably sda3 since sda2 is too small to have had an OS installed on it. Any partition editor can do this.

---

### Post by emians on 2019-04-06
[COLOR=#000000]Thanks Dennis N.[/COLOR]

[COLOR=#000000]I will.[/COLOR]

[COLOR=#000000]Any idea how the root logical volume could have been canceled?[/COLOR]

---

### Post by emians on 2019-04-06
I reinstalled,

on reboot I get this from BIOS:

Default Boot Device Missing or Boot Failed.
Insert Recovery Media and Hit any key
Then select Boot Manager to choose a new Boot Device or to Boot Recovery Media

once I press ok it gives me a Boot Manager

option one states :

1. Unknown Device: (media_volume_HD_name)

I select it and the system runs on Ubuntu studio working.

It happens every time I restart the system.

In the BIOS boot the boot volume is correct.

What possibly...?

---

### Post by emians on 2019-04-06
Solved Apparently.

I went on the BIOS secure boot settings and selected the grubx64.efi file for the secure but under UEFI.

Now Ubuntu Studio is running again. 

I'll see if I can manage to get that printer to work.

Thank you for your support.

---

### Post by emians on 2019-04-06
Thanks Ruby1200.

Fortunately the system was empty so I preferred to follow the quick way and format and reinstall again. I see if installing printer drivers reissue the same, and in case get back. I'd leave the thread running for the moment!

---

### Post by Rubi1200 on 2019-04-06
If you are back up and running with a bootable system, please post the results of one of the previous commands one more time:

```
sudo fdisk -l
```

I am curious to see what the partitions look like now.

---

### Post by emians on 2019-04-08
Here it go:

Disk /dev/sda: 465,8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes /4096 bytes
Disklabel type: gpt

Device          Start       End         Size     Type
/dev/sda1      2048     1048576  512M    EFI System
/dev/sda2    1050624    "           465,3G   Linux filesystem

---

### Post by Rubi1200 on 2019-04-08
Thanks.

Please mark the thread Solved using Thread Tools at the top.

---

