---
title: "Always have to run sudo update-grub before USB HDD will boot"
date: 2016-04-29
forum: General Help
---

### Post by stepheny on 2016-04-29
With help from oldfred I got grub to boot my old HDD connected via a SATA/USB cable to a USB port [http://ubuntuforums.org/showthread.php?t=2322254](http://ubuntuforums.org/showthread.php?t=2322254). I marked the issue solved but have since noticed that unless I run sudo update-grub directly before rebooting the laptop, booting a partition on the USB drive results in failure to boot and the following warnings:

```
Error: No such device
Error: hd1 cannot get C/H/S values
Error: first load the kernel.
```

If I run sudo update-grub before rebooting and then select a partition on the USB HDD it boots fine (except a disk check is always started which can be stopped by CRL-C). 

Running blkid when the USB drive is connected always gives the same UUID's for the partitions.

What is preventing the boot without having to run sudo update-grub every time?

---

### Post by sudodus on 2016-04-29
I think it is a kind of confusion because the two systems are so similar, and the system looks for partitions and files in one drive, but they are actually located in the other drive. I hope to see what causes your problem, if you provide the following information.

With both drives connected, please post the output of the following terminal windows commands in a wide window (for example maximized)

1. Boot into your current main drive (the internal drive).

2. Run these commands

```
df   # show mounted devices
sudo lsblk -fm   # ... space minus eff emm
sudo parted -ls   # ... space minus ell ess
cat /boot/grub/grub.cfg   # for comparison with the grub configuration after update-grub
```

3. Post the output of each of the commands within 'its own' [noparse]```
tags
```[/noparse] to a reply

4. Run

```
sudo update-grub
```

5. Run these commands (again)

```
df
sudo lsblk -fm
sudo parted -ls
cat /boot/grub/grub.cfg
```

6. Post the output of each of the commands within 'its own' [noparse]```
tags
```[/noparse] to a new reply

---

### Post by stepheny on 2016-04-29
Removed outputs

---

### Post by stepheny on 2016-04-29
Removed outputs

---

### Post by sudodus on 2016-04-29
The only difference I found was a slight difference in disk usage in the latter case. **/boot/grub/grub.cfg** was not changed at all by update-grub.

That should mean that the computer *should* boot in the same way.

But if you have updated/upgraded your system (including a new kernel) without having the external drive connected, that drive would not be seen during the automatic 'update-grub'. And in that case you would have seen a difference in **/boot/grub/grub.cfg** with menuentries for the external drive.

If you get differences in booting also without any difference in that grub configuration file, maybe it depends on some hardware. Maybe it makes a difference if it is a cold boot or a reboot.

---

### Post by stepheny on 2016-04-29
I have upgraded to 16.04 and the USB-HDD no longer boots even after a sudo upgrade-grub :-(

---

### Post by sudodus on 2016-04-29
Did you upgrade the version in the internal drive?

Maybe there is a problem with the 'SATA/USB cable', that it is not 100% compatible with the USB standard. Does it work to boot a USB pendrive in that USB port.

Maybe another USB port works better.

What about the power supply for the external drive and the 'SATA/USB cable'?

Maybe it works better with an older version. Try 14.04.1 LTS.

---

### Post by stepheny on 2016-04-29
The 14.10 and 15.04 partitions are old drives. My new 16.04 (was 15.10) is the system I want to use. I just want to boot up the old systems occasionally if and when I need to. I certainly don't want to keep upgrading them. 

I'll try another SATA/USB cable.

---

