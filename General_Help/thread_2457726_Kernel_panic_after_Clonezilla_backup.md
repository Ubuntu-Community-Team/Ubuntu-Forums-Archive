---
title: "Kernel panic after Clonezilla backup"
date: 2021-02-07
forum: General Help
---

### Post by keijo-kukka on 2021-02-07
Hi gurus!
I consider myself as a Linux beginner and I'm running Kubuntu 20.04 as my daily driver distro with recent updates. I recently wanted to try to backup my whole hard drive and tried Clonezilla live USB distro for that.
I made a Clonezilla live USB stick with Etcher, backed up my hard drive into external USB HDD and whole backup process went seemingly fine, but after it was over and I wanted to boot back to my Kubuntu I ran into problems.

After the Clonezilla backup, I powered off and rebooted normally from my PC hard drive, but immediately I noticed that reboot took longer than normally and finally booting process froze in black screen.
I hard booted via power button and after reboot, I was rebooted into Grub bootloader. If I chose normal "Ubuntu", then I ran into kernel panic. See picture 1 attached.

So I hard booted yet again and this time I tried various kernel versions (and recovery versions) from the Grub boot loader and I finally found kernel version with which I was able to boot normally (kernel version 5.4.0-59-generic). See picture 2 attached.
Right after booting from working kernel version 5.4.0-59-generic, an error message was quickly displayed but otherwise boot process continued normally. See picture 3 attached.

I was able to boot normally with kernel version 5.4.0-59-generic and now everything seems to work fine, but obviously something is wrong. Every time I reboot I'm in the same situation and I'm now only able to boot if I choose kernel version 5.4.0-59-generic. I'm too beginner in Linux environment to know what kernel panic actually means and how to fix it permanently (not by choosing older kernel version every time during boot).

Any help please would be greatly appreciated ...I'm starting to panic myself too... &#128547;&#128547; Thank you very much!!

---

### Post by TheFu on 2021-02-07
Ensure there is plenty of disk storage available and reinstall the newer kernels.

---

### Post by keijo-kukka on 2021-02-09
> **TheFu said:**
> Ensure there is plenty of disk storage available and reinstall the newer kernels.

Thank you for answering TheFu! I have 90GB of storage free in my  256GB SSD, so storage shouldn't be the problem in this case, huh?

I tried re-installing few of the newest kernels, but received the following error message:

[FONT=monospace]...[/FONT]
[FONT=monospace][COLOR=#000000]Errors were encountered while processing: [/COLOR]
 linux-firmware 
 linux-image-5.4.0-60-generic 
 initramfs-tools 
 linux-image-5.4.0-65-generic 
 linux-image-5.4.0-64-generic 
 linux-image-5.4.0-62-generic 
E: Sub-process /usr/bin/dpkg returned an error code (1)

[FONT=arial]I also tried to delete the newer kernels from [FONT=monospace]linux-image-5.4.0-60-generic to [FONT=monospace]linux-image-5.4.0-65-generic[/FONT][/FONT][/FONT][/FONT] with the following commands:

sudo apt remove linux-headers-5.4.0-65-generic
sudo apt remove linux-image-5.4.0-65-generic
sudo apt remove linux-modules-5.4.0-65-generic

But I'm still able to see them with command:

[FONT=monospace][COLOR=#000000]dpkg -l | grep linux-image-.*-generic[/COLOR]

[FONT=arial]Should[/FONT][/FONT] I perhaps try to force the GRUB boot loader to boot from the [FONT=arial]kernel  linux-image-5.4.0-60-generic which seems to be the newest working  kernel? How do I do that? Or what else would you recommend? Thanks a  lot!![/FONT]

---

### Post by TheFu on 2021-02-10
90GB of storage in the wrong place doesn't help. If /boot/ is full, you are screwed even if there is 4TB of storage free.

Why didn't you delete linux-image-5.4.0-6[245]-generic? Appears you've had whatever the issue is for a while. BTW, do not reboot the system until you have a clean kernel install - hopefully, both .64 and .65 versions. 

**dpkg -l** shows previously installed packages unless you filter on the first 2 columns too.
**uname -r** shows the currently used kernel. Never delete that.

It really would be easier to help if you showed 
a) the exact commands run with
b) the exact output and 
c) put all that into the post wrapped in forum code tags.  I.e. don't mess with any fonts here, just use code tags. [https://ubuntuforums.org/misc.php?do=bbcode#code](https://ubuntuforums.org/misc.php?do=bbcode#code) explains.

Please.

As for reasons - it could be a bad cable, bad SSD/HDD, some power issue with a GPU or the PSU.

If it is really bad, you could boot into a *Try Ubuntu* live environment, setup some chroot stuff, then use the live environment to install kernels and modules onto the correct storage. This isn't fun, but it is possible. I've used it.  Would have been easier to avoid the problem or fix it when the first issue happened.  Once in a while, even the chroot method fails and I've reinstalled the OS, then put my backup-restore methods into play.  45min later and my system is back to the way it was earlier.  With a clone, possibly corrupted, I have no idea how to get selected access to the stuff to be restored. I don't use cloning for backups.

---

