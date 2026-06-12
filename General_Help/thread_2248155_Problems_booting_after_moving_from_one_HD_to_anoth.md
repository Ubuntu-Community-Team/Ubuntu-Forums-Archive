---
title: "Problems booting after moving from one HD to another"
date: 2014-10-12
forum: General Help
---

### Post by j81148 on 2014-10-12
I recently tried to move my Ubuntu 12.04 OS from a smaller hard drive to a newer one by following, for the most part, the instructions described [here]("http://www.ubuntuhowtos.com/howtos/move_system_partition_to_new_hard_drive_larger_partition").

What I have done differs in that I didn't create an image with partimage and place that file in the mounted new filesystem since gparted allowed me to copy over the logical partitions I had previously. I have also a quite different partition table structure to that outlined in the link above.

On my old HD the partition table was along these lines:

[TABLE="width: 200"]
[TR]
[TD]/dev/sda1[/TD]
[TD]*boot[/TD]
[TD]extended partition[/TD]
[/TR]
[TR]
[TD]/dev/sda5[/TD]
[TD][/TD]
[TD]ext4[/TD]
[/TR]
[TR]
[TD]/dev/sda6[/TD]
[TD][/TD]
[TD]ext4[/TD]
[/TR]
[TR]
[TD]/dev/sda3[/TD]
[TD][/TD]
[TD]linux-swap[/TD]
[/TR]
[/TABLE]

where /dev/sda5 was mounted on / and /dev/sda6 was mounted on /home

The new partition table is in ```
sudo fdisk -l
``` of the boot_info_beforeMounting.txt file attached.

However, having followed these instructions, I am now finding that I can't boot with this new HD, and I get taken straight to a grub prompt from which I have followed numerous instructions to try to fix the boot problem but to no avail. I have tried:

```
find /boot/grub/stage1 
root (hd0,4)  # based on the output from find above
setup (hd0)
```

and it gives no errors but I still can't boot.

I have attached the details of relevant boot files before mounting /dev/sda5 on a live USB (boot_info_beforeMounting.txt), and after mounting (boot_info_afterMounting.txt: it's compressed since it exceeded the file size limit). The details follow a similar vein to that posted by the OP on [this thread]("http://ubuntuforums.org/showthread.php?t=1697133").

How can I boot from this new HD?

[ATTACH]257154[/ATTACH]

[ATTACH]257155[/ATTACH]

---

### Post by yancek on 2014-10-12
The link you used is for using Grub Legacy which Ubuntu has not used for five years.  The commands below won't do anything with Grub2 which is the default for Ubuntu 12.04.

```
root (hd0,4)  # based on the output from find above setup (hd0)
```

You can install Grub2 with sudo grub-install /dev/sd?, replace the ? mark with the correct letter of the drive.  The link below explains installing Grub2, different methods.

[https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2](https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2)

---

### Post by oldfred on 2014-10-13
Are you planning on keeping old hard drive plugged in? 
If so you will have major issues of duplicate UUIDs which are not allowed. In fact when booting, one time it may boot to old drive and next to new drive and updates get out of sync.
You must then immediately change UUID on one drive or the other, update fstab and totally uninstall and reinstall grub2.

Generally easier to just do a new install to new drive, and copy /home over to new install. If lots of apps installed, export a list from old install first and reinstall.

---

