---
title: "basic update trouble, out of free space"
date: 2015-12-03
forum: General Help
---

### Post by stephen58 on 2015-12-03
I tried to accept the automatic update(s) for my Ubuntu 15.10 computer today and it failed due to lack of space. Searching the internet suggested that boot/root ran out of space and removing linux-image packages using Synaptic package manager should fix it. I tried to install Synaptic (using the Ubuntu Software Center, not terminal apt-get) and it said it failed due to lack of space, but then showed as installed anyway and it opened fine and I was able to delete the 2 least recent images (which told me it freed a tad over 400MB). I needed to move on with my day at the time, but am now trying to learn **what happened, why, and how to prevent it in the future**.

The "Disks" program displays 1 physical disk with 3 volumes/partitions:

[LIST]
[*]Filesystem Partition 1 255MB Ext 2
[LIST]
[*]96MB free 63.3% used
[*]/dev/sda1 (LINUX bootable)
[/LIST]

[*]Extended Partition Partition 2 250GB
[LIST]
[*]/dev/sda2 (extended)
[/LIST]

[*]Partition 5 250GB LVM2 PV
[LIST]
[*]/dev/sda5 (logical)
[/LIST]
[/LIST]

The "Disks" program also displays 2 "Block Device" (logical disks):

[LIST]
[*]/dev/ubuntu-vg/root 233GB (220GB free, 5.3% used)
[*]/dev/ubuntu-vg/swap_1 17GB
[/LIST]

Terminal `sudo parted -l` shows 3 partitions matching what "Disks" displays.

The "Disk Usage Analyzer" program displays 1 disk  and 2 folders:

[LIST]
[*]/ (disk: 8.6GB used out of 229.0GB)
[*]/home/master (folder)
[*]/boot (folder: 148.3MB used)
[/LIST]

Using "Files", right clicking on "computer" and selecting "properties" displays 9.3GB used and 208.0GB free with a total capacity of 229.0GB.

-----


[LIST=1]
[*]What ran out of space? I thought it said "root" (though I may be remembering incorrectly), but how could it be root when it has 220GB unused? If it was sda1 ("boot"), then how did 400-some MB get freed from removing 2 linux-image packages when the partition is only 255MB?
[*]Why does Ubuntu save so many old kernel images, why is the boot (sda1) partition so small, and is there a way to fix either of these in such a way as to avoid this out-of-space problem in the future?
[*]The above byte size numbers (Disks vs. Files vs. Disk Usage Analyzer) don't match up. Which is the correct tool for identifying the out-of-space culprit/source?
[*]Are there any other questions I should be asking?
[/LIST]

---

### Post by blm-ubunet on 2015-12-03
AFAIU your /dev/sda1 is being mounted into the filesystem at mount-point "/boot".

So the folder "/boot" is not the same partition as root "/" .

The linux-image packages (being install) results in a boot image created in /boot.
The packages are cached in / root filesystem somewhere.

So possible for linux-image package to be 200MB but the boot image component is less.
On my 32bit PC each kernel boot image is about 35MB.

Historically, ubuntu has had a problem clearing out old kernels but lately this has been working here..

If you want/need a clean out:
sudo apt-get update
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get upgrade
sudo apt-get dist-upgrade (moves to latest point release in the same ubuntu release)

---

### Post by stephen58 on 2015-12-03
Okay, thanks. I ran those and it seems to have picked up the updates/upgrades I missed/skipped earlier. The /boot in Disks also is showing less used space.

---

### Post by blm-ubunet on 2015-12-03
Probably the "sudo apt-get dist-upgrade" did that but more likely just update timing..
Ubu 15.10 probably does not have a point release upgrade yet.
It is also not LTS release so has a shorter shelf life.
Some people don't like to upgrade the point release inside the same ubuntu release version.
I always do.

I figured as you were running 15.10 (not LTS) you were not "attached" to some old release point state.

---

### Post by grahammechanical on 2015-12-03
I do not have a boot partition so I do not have this problem because the packages involved in a kernel upgrade are in /boot on my Ubuntu partition. I guess that you got a boot partition as part of the choice to use LVM with the installation. I am not sure about that.

Previous kernels are kept in case we need to load into one when a new kernel proves to break the desktop. Which is why we should always have one working previous kernel that we can load sitting in the Advanced Options for Ubuntu sub-menu.

By the way, in the Advance Options sub-menu we can select to load a kernel in recovery mode. That will take us to a menu and among the options we can select Clean -Try to make free space. That will run both the apt-get clean and the apt-get autoremove commands for us. Selecting Resume will load to a desktop.

And I have no idea why the boot partitions that are automatically created are so small. You could of course try resizing it to make it larger.

Regards.

---

