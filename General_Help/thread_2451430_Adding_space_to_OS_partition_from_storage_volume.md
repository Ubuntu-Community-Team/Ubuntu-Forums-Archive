---
title: "Adding space to OS partition from storage volume"
date: 2020-10-04
forum: General Help
---

### Post by physics-penguin-99 on 2020-10-04
So i first installed ubuntu on my dell windows by making 3 partitions: OS, swap and storage. Now, I don't use a large amount of space of the storage volume but I need space on the OS partition. I'm trying to resize the storage volume to add it to the OS part, but I get an error as the volume is being used.
I tried unmounting it using sudo umount -l /dev/... but still I get an error message popping up: 

Error repairing filesystem on /dev/...: Process reported exit code 8: e2fsck 1.45.5 (07-Jan-2020)
e2fsck: Unable to continue, process will be interrupted.
(udisks-error-quark, 0)

I've tried the fsck command to repair the volume, but it tells me that it is being used (even after the umount command).

I don't know what else to do.

Also, when I boot Windows to fix it that way, the partitions where I have ubuntu are impossible to change, I can only eliminate them.

Any help is welcome, thank you

---

### Post by CelticWarrior on 2020-10-04
Welcome.

We cannot manage partition that are in use. We boot a live session for that.
Windows doesn't recognize EXT4 or other typical file systems used in Linux. We NEVER even try to manage those partitions from Windows.

---

### Post by TheFu on 2020-10-04
+1 to what CelticWarrior said.

Use Windows to deal with Windows file systems.
Use Linux to deal with Linux file systems.
Danger exist in crossing those boundaries.

At the partition level, Linux can only modify inactive partitions.  That means they cannot be mounted. There is no method to un-mount an actively running OS partition under Linux, so the technique is to boot from an Ubuntu Install flash drive, choose "Try Ubuntu" and modify the HDD/SSD partitions while running Linux from the alternate boot media.

However, if Windows has file systems that weren't properly closed, which is the default for Windows8, and later versions, then you must boot into Windows, change the defaults to disable hibernation and "fast startup" under Windows, then boot back into the "Try Ubuntu" environment and use **gparted** to modify the partitions as you like.  There are risks in doing this, so be 100% certain you have any data/files that cannot be lost backed up and disconnected from the system BEFORE attempting it.  Also, expect to need a Windows Recovery Disk, so ensure you have one of those available BEFORE you start.  On Linux, the "recovery disk" is just that "Try Ubuntu" environment. From there, we can fix almost anything - almost - assuming it isn't hardware at fault.

It is extremely common for people new to partitioning to make 1 tiny mistake and accidentally wipe entire partitions, so please be very careful. I say this since pretty much everyone does that at least once.  I did back in the 1990s, but all of us have.  When resizing partitions, it may happen that the UUID (an identifier used to mount storage by the fstab) changes. If a UUID for the boot or OS partition changes, then the Linux OS may not boot.  The *Try Ubuntu* environment can be used to correct that after the change happened.

You can always use the Try Ubuntu environment to connect to the internet, come back here and get more answers.  If that becomes necessary.  There are also the help.ubuntu.com pages.

---

