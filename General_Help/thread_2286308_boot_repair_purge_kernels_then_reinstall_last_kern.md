---
title: "boot repair purge kernels then reinstall last kernel sda1(ins) message seems to hang"
date: 2015-07-11
forum: General Help
---

### Post by jdlaustin on 2015-07-11
After updates froze and I rebooted my computer, it had problems rebooting so I followed the instructions on [https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition)

However, the very last step of the boot repair seemed to hang with the message: purge kernels then reinstall last kernel sda1(ins). This may take several minutes.

This message had been displaying for over an hour when I left work on Friday.

If this message is still up on Monday when I return to work, what steps should I take?

---

### Post by Vladlenin5000 on 2015-07-11
Hi and welcome.

> **jdlaustin said:**
> After updates froze and I rebooted my computer, it had problems rebooting so I followed the instructions on [https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition)
May I ask why?

---

### Post by oldfred on 2015-07-11
Generally desktop installs are better without a separate /boot partition.

It used to be standard with the old systems, but now just about only required with full drive encryption and LVM. Grub2 can boot UEFI or RAID or just about anything.

The exceptions are very old BIOS with 137GB limit. Boot files have to be inside the first 137GB. Similar issues may be on some full drive installs to a USB drive. But if you have a smaller / (root) of 25GB fully inside the first 100GB and rest of drive as /home even then you do not need a /boot partition.

---

### Post by jdlaustin on 2015-07-13
I'm a newbie to partitions and boot-repair and my system won't boot. It's running 14.04. I am not using dual boot with windows, I only work in ubuntu. I have 2 hard drives, sda and sdb, but only sda is bootable. When Ubuntu installed automatic updates,the updates froze. My system could not reboot via the menu and when I turned it off and then on, it won't boot. Thus, I followed the instructions on [https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition)

One complication is that the live CD I had was for ubuntu 12.04 but my system is using ubuntu 14.04. I don't know if this caused the problem that after using gparted (step 6 of the BootPartition instructions), the new bootable partition wasn't in the list. Since then, I've tried running boot-repair again from ANOTHER live CD with the correct, 14.04, ubuntu version but it just hangs on the "Purge kernels then reinstall last kernel sda1 (ins)..." step.

Here's the pastebin from this morning but my system still could not boot after the boot-repair completed. [http://paste.ubuntu.com/11872919/](http://paste.ubuntu.com/11872919/)

Thus I tried running it again but it just hangs.

---

### Post by oldfred on 2015-07-13
Boot-Repair commented out /boot in your fstab. So it is not used.

Since you only have Ubuntu installed, is it perhaps booting, but another driver issue.
Try holding shift key from BIOS and see if menu appears.
With one install grub menu is not normally shown.
Then try recovery mode or booting to see what is happening.

Is this an older system with newer large 1TB drive?

Your sdb drive is not shown at all. Is it not partitioned & formatted?

---

### Post by jdlaustin on 2015-07-13
Thank you so much for your reply! It did finally boot but it has lots of errors and it can't detect my second monitor.

> **oldfred said:**
> Boot-Repair commented out /boot in your fstab. So it is not used.

Since you only have Ubuntu installed, is it perhaps booting, but another driver issue.

Try holding shift key from BIOS and see if menu appears.
With one install grub menu is not normally shown.
Then try recovery mode or booting to see what is happening.

Is this an older system with newer large 1TB drive?

No, it's about 2 years old.

Your sdb drive is not shown at all. Is it not partitioned & formatted?

We set it up 2 years ago so I don't remember all of the details. It's formatted for ubuntu and it contained a mirror of sda (or some of the data on sda). When I try to mount it I get an error "can't read superblock"

I rebooted and there were lots of errors. One error I saw last week was that the /boot folder wasn't at the beginning of the hard drive (or something like that) so that's why I tried following the instructions on [https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition) so I could have the new small /dev/sda2 be the bootable partition at the beginning of the drive. 

dmesg contains errors such as: failed command: READ DMA

Before the automatic updates, ubuntu detected both Dell monitors without any problem. Is there something I can run to fix the issue? 

>> Boot-Repair commented out /boot in your fstab. So it is not used.

Is this ok?

Thanks,

Jade

---

### Post by jdlaustin on 2015-07-13
I forgot to mention that when I boot to a live CD, both of my monitors are detected. 

However, when I boot from my hard-drive, which I click on Detect Displays, nothing happens.

---

### Post by oldfred on 2015-07-13
You have AMD, which I do not know about. Best just to start another thread with dual monitors & AMD in title and those that may know more about that should offer to help.

I do not recommend separate /boot partitions, but do recommend smaller / (root) partitions of 25GB and either /mnt/data which I use or for newer users /home as separate partition which is a bit easier to set up and easier later to upgrade/reinstall with.

If second drive is not now showing partitions that is a major issue also. Perhap should be a separate thread also, but try testdisk to see if it sees partitions? 

Are you getting abnormal shutdowns or forcing power off? That can cause major issues.

---

### Post by jdlaustin on 2015-07-13
Thanks for the info. I forced a power off after the update hung and shutdown from the menu didn't work. I had no idea that ubuntu wouldn't be able to recover. I wasn't sure of what else to do since it was semi-broken after the update.

---

### Post by oldfred on 2015-07-13
Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

Often after a forced shutdown, you have to run fsck to repair file system.

---

### Post by jdlaustin on 2015-07-14
Thanks very much. I'll do that in the future. I ran fsck but the file system didn't need to be repaired. 

Jade

---

### Post by andreas-bartels on 2016-02-26
As I got the same fault by choosing to install the latest kernel as well, I think it is a problem because there might be not the knowledge which is this kernel or something like it and so the kernel gets purged and the insertion is never being completed. So I helped me out with only a [COLOR=#008000]***chroot "<File-system-tree>" apt-get install kernel***[/COLOR] and a restart of the disk-repair tool. Don't know precise where there is a loop in the script that not returns or that not quits by trying to install a new kernel, but it must be a bug that exist a long time and that isn't solved at all. Only people doesn't check the upgrade kernel in the advanced menu and so most won't recognise this fault. Did take me about 2h because I had a raid out of 6 drives a boot on each drive and an efi on each drive to be really independent from any of the drives. My boot is at the end of the disks as the time for booting is very unimportant but the drive speed for swap and data more efficent

---

