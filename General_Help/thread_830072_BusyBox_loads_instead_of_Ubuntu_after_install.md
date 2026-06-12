---
title: "BusyBox loads instead of Ubuntu after install"
date: 2008-06-15
forum: General Help
---

### Post by Kamaria on 2008-06-15
Hi, I'm a new Ubuntu user...well fairly new, I tried it out about a year ago.

I decided to revisit it, I partitioned both of my drives (I have two), one for Windows later and one for Linux.

I have the swap/page spaces on opposite drives, as a friend told me to do.

I partitioned my second drive (the slave drive) for Linux with three seperate partitions, and mounted them as this in install:

/, /usr/local/, /home/,

Everything seemed to go fine and it installed. These are new partitions, so there is no previous Linux installation on them. So, I restarted the computer, removed CD.

It loads through GRUB and everything and the Ubuntu splash screen comes up, but it doesn't appear to be loading, the bar goes back and forth. My second hard drive seems to do something for a few seconds with the light flashing a little, and then stops. After a few minutes, I get a DOS-like prompt called BusyBox.

Attempts to format and reinstall have led to the same error. I have no other operating systems installed, I formatted my drives completely clean with new partitions. The only thing I can use is LiveCD.

What's more, is my partitions for some reason are listed as /dev/sda# and /dev/sdb#...and LiveCD is reading them as REMOVABLE devices.

I don't claim to be an expert but it seems like for some reason, the bootloader isn't finding Linux? Because my friend told me to check the error logs and not a damn thing is written in them.

Can anyone help me out?

---

### Post by Kamaria on 2008-06-15
Oh yes, and I'm using the latest version of Ubuntu, 64-bit, with a 64-bit AMD processor.

What's worse is now that I came out of the prompt again, all the partitions in GParted on the Linux drive cannot be read or something...

---

### Post by Quantumstate on 2008-06-15
Your install seems to not be succeeding.  Have a usb drive in that could be sdb?

Boot to the HH Desktop cd, and tell it to boot to sda1.

---

### Post by Kamaria on 2008-06-15
I took off my external drive.

I turned off quiet mode, every time I booted, I got messages like these:

Status: { DRDY ERR }
Error: { IIRC ABRT }

Soft Resetting Link

ldm_validate_partition_table: Disk read failed

Unable to read partition table

etc, that's not all of it, that's just what I could write down that seemed like it meaned anything.

I'm guessing there's a problem with the disk? Especially since when I boot with Live CD, looking into GParted shows that all of the partitions have an /!\ next to them...

---

### Post by Kamaria on 2008-06-15
^Bump.

---

