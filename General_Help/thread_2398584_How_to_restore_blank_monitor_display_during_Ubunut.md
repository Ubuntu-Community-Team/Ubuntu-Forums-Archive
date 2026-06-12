---
title: "How to restore blank monitor display during Ubunut 16.04 Login"
date: 2018-08-14
forum: General Help
---

### Post by sunbear-c22 on 2018-08-14
While testing a custom Vulkan tutorial program, my display became very laggy and froze intermittently, keyboard and mouse became unresponsive.... As a last resort, I had to manually power off the system and restart it that way. However, after restarting, I now have a blank/black screen after the Grub screen (no issue with Grub screen), i.e. during Ubuntu Login. I can restart my system using keyboard Ctrl+Alt+Del. System appears running just that there is no display on my monitor. How do I recover from this?

I tried switching to tty by <Ctrl><Alt><F1> and F2, 3, 4, 5, 6, but nothing happens.

---

### Post by QIII on 2018-08-14
Hello!

Some further information would be helpful.

Please provide your hardware specifications, in particular the model of your GPU.  What driver do you have installed?  Did you install any other packages recently? 

Not knowing the nature of your application, it might be difficult for us to guess what it might have done to change your system.

---

### Post by dragonfly41 on 2018-08-14
Long shot. Try SuperKey+P .. hitting that key combination up to three times to cycle through different monitor modes.

SuperKey is the one with the Windows icon bottom left of keyboard.

I have to use this routine at login since I don't know how my monitor got into this state of showing a blank screen.
Probably when I was using an external monitor.

---

### Post by sunbear-c22 on 2018-08-14
@Qlll I have a Nvidia Gefore GTX Titan GPU, i7 cpu. Graphics driver by [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa), i think it was at 384.130.

@dragonfly41, the Super+P did not work. :(

I had an older Ubuntu version installed on another HDD partition and was able to login there and use my monitor. However, after a `sudo apt upgrade` command, and it failed to complete at 89%, my other system now get a purple screen on that HDD partition.

I have tried a Ubuntu installation disk and the monitor worked. I suspect some graphic/display settings relating to my original install must have altered/corrupted after I did the manual shutdown...

Using the Ubuntu installation disk, ran a `lsblk` and saw 
sdb is a disk with mountpoint cdrom, 
loop0 is a loop with mountpoint /rof, 
sda is a disk with no mountpoint, and 
nvme0n1 is a disk with no mountpoint.

The Ubuntu 16.04 system affected by my Vulkan program is a filesystem located in nvme0n1. 

When I run df -k, I think do not see any reference to nvme0n1 and sda.

---

### Post by sunbear-c22 on 2018-08-15
I found there that /dev/nvme0n1p3 reported this issue: fsck exit status code 4. 

I tried a sudo e2fsck -fp /dev/nvme01p3
got:
>  /dev/nvme01p3: Inodes that were part of a corrupted orphan linked list found.

 /dev/nvme01p3: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY
    (i.e., without -a or -p options)

What should I do?

---

### Post by sunbear-c22 on 2018-08-15
I ran either [COLOR=#000000]sudo e2fsck -y /dev/nvme01p3 or [/COLOR][COLOR=#000000]fsck -y /dev/nvme01p3 (pardon me for not being clear here) [/COLOR][COLOR=#000000]and all inode issues were reported to be fixed. [/COLOR][COLOR=#000000] /dev/nvme01p3 was the partition where Ubuntu 16.04 was installed in. 

[/COLOR][COLOR=#000000]During the first restart, the black/blank screen issue was no more, I got back my Ubuntu login screen. My issue was resolved.

Hopes the above can help another. [/COLOR]

---

