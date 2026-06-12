---
title: "swap unusable after gparted crash"
date: 2008-05-01
forum: General Help
---

### Post by jabley on 2008-05-01
I recently installed 7.10 on my laptop. The laptop has 2BG RAM and I foolishly only gave it around 1 GB of swap. This has caused me problems when hibernating, since it sometimes complains about not enough swap; the laptop comes back up and I have to shutdown applications to hibernate successfully, which kind of defeats the point of hibernating.

So I booted up the 7.10 live disk, started up sudo gparted and checked the partitions.

I clicked on swapoff for my single swap partition, whereupon gparted seg-faulted. I shutdown and restarted to check the damage.

When I restarted the OS from the harddrive, my swap wasn't being used.

swapon -s showed a priority of -1?

free showed that no swap was being used, and the laptop was running fairly slowly.

swapon -a seemed to have no effect (swapon -s showed that the swap was apparently recognised; free showed that it wasn't being used).

I started gparted (this time in the installed OS), and turned off the swap partition. I was able to resize the swap partition to 2GB, and format it as swap, then turn the swap back on.

swapon -s now showed a priority of -3. Swap wasn't recognised.

Rebooting hasn't fixed the problem - it seems to have made it worse.

swapon -s now shows nothing.

jabley@miq-jabley:/var/crash$ sudo swapon -s
Filename                                Type            Size    Used    Priority

And I can't turn the swap on.

jabley@miq-jabley:/var/crash$ sudo swapon /dev/sda4
swapon: /dev/sda4: Invalid argument

To recap, before rebooting, the swap was recognised, unused and had a strange negative priority value. After rebooting, it's not recognised at all. I tried editing /etc/fstab to use the /dev/sda4 label rather than the UUID, but that doesn't appear to have changed anything.

A new behaviour noted after rebooting as well. The Firefox address bar has now stopped working. I don't see how that's related, but that's what I'm seeing. If I type in a URL and press enter or click Go, nothing happens. I can only get to content using Google Toolbar to search, and click links. Ouch.

jabley@miq-jabley:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda2             19228308   9398556   8853000  52% /
varrun                 1037236       120   1037116   1% /var/run
varlock                1037236         0   1037236   0% /var/lock
udev                   1037236        96   1037140   1% /dev
devshm                 1037236         0   1037236   0% /dev/shm
lrm                    1037236     34696   1002540   4% /lib/modules/2.6.22-14-generic/volatile
/dev/sda1                62193     23173     35809  40% /boot
/dev/sda3             62475392  26254012  33047740  45% /home
/dev/scd0               712508    712508         0 100% /media/cdrom0



jabley@miq-jabley:~$ sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           8       64228+  83  Linux
/dev/sda2               9        2440    19535040   83  Linux
/dev/sda3            2441       10342    63472815   83  Linux
/dev/sda4           10343       10603     2096482+  82  Linux swap / Solaris

jabley@miq-jabley:~$ cat /etc/fstab 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=275d2407-f5a0-49f0-8bcd-3547cd1d78ea /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=aceb35ce-0750-4330-abe3-9bcfe1dc083b /boot           ext3    defaults        0       2
# /dev/sda3
UUID=bfed0285-4ee1-4c51-ba55-98ec58fa0d8d /home           ext3    defaults        0       2
# /dev/sda4
#UUID=398267b1-00c6-42fa-9a38-b9093fe7fe32 none            swap    sw              0       0
/dev/sda4       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

Rebooting with the UUID changed to the result of sudo vol_id -u /dev/sda4 did not improve the situation.

**Update** Firefox address bar is now working after that reboot. Maybe I'm just lucky like that! Still no swap being used though.

---

### Post by jabley on 2008-05-02
$ sudo vol_id /dev/sda4
ID_FS_USAGE=other
ID_FS_TYPE=suspend
ID_FS_VERSION=s1suspend
ID_FS_UUID=162a6843-aa7d-4ffc-a43d-02dabd0449f5
ID_FS_UUID_ENC=162a6843-aa7d-4ffc-a43d-02dabd0449f5
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=

So it thinks the partition is suspend, rather than swap. I'll try mkswap and swapon to see if that fixes the issue.

---

### Post by jabley on 2008-05-02
sudo mkswap /dev/sda4
# format the swap partition
sudo swapon /dev/sda4
# use the partition
sudo swapon -s
#priority was -1 in the output
sudo vol_id /dev/sda4
# discover the new volume uuid
sudo vi /etc/fstab
# update the fstab entry with the new uuid

I rebooted and the swap was detected and apparently available, although the bytes stored was 0 out of the 2GB available. Maybe the negative priority means that the OS will wait until I use up all RAM before using any swap? I'm going to compare with other installs, and see what the swap priority is on my 6.06 and 8.04 machines at home.

I hibernated the laptop, turned it back on and hibernate failed. Plus the swap partition is buggered again.

jabley@miq-jabley:/opt/tomcat/bin$ sudo vol_id /dev/sda4
ID_FS_USAGE=other
ID_FS_TYPE=suspend
ID_FS_VERSION=s1suspend
ID_FS_UUID=d259d981-c34c-496a-8b8e-13fa5cbd521b
ID_FS_UUID_ENC=d259d981-c34c-496a-8b8e-13fa5cbd521b
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=

So my hibernated state is presumably still on that partition, but the partition wasn't used when resuming.

I never had any problems with hibernating and resuming before on this laptop, apart from the lack of swap available for hibernating which led me to start this exercise.

So it looks like my problem has become, why won't it hibernate and resume properly? I'm guessing I can reformat the swap partition again, but I'll still have problems resuming...

---

### Post by jabley on 2008-05-06
Fixed this. 

The swap priority on my other machines, which hasn't been altered since installation, are both set to -1. 

Steps to fix, which is almost a list of steps of how to resize your swap partition. Just run gparted first, to turn your swap off, resize and save. Then just follow the steps to update your system to use the newly UUIDs on the volume. You may be able to do all this without the two reboots that I used, but I'm not sure what daemons would need restarting to pick up the changes that are being made. Obviously, /dev/sda4 is my swap partition. Adjust appropriately.

# format the swap partition
$ sudo mkswap /dev/sda4
# use the partition
$ sudo swapon /dev/sda4
# discover the new volume uuid
$ sudo vol_id /dev/sda4
# update the fstab entry with the new uuid
$ sudo vi /etc/fstab

Reboot.

Swap is being used properly.

$ cd /etc/initramfs-tools/conf.d/
$ sudo bash
$ echo RESUME=UUID=`sudo vol_id -u /dev/sda4` > resume
$ aptitude reinstall initramfs-tools
$ exit

Reboot

Hibernate and resume is working correctly in all cases since then.

I don't yet know enough to understand why this is the case. I just followed the crumbs when looking at the scripts in /etc/acpi; in particular hibernate.sh. I found [this]("http://ubuntuforums.org/showthread.php?t=456992") afterwords as well, which is very similar, about fixing the hibernate issue.

---

