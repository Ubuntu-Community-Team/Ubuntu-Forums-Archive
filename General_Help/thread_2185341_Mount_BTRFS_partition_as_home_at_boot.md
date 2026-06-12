---
title: "Mount BTRFS partition as /home at boot"
date: 2013-11-02
forum: General Help
---

### Post by soumyas.sarkar on 2013-11-02
Hi,

I recently switched from openSuSE to ubuntu 12.04 LTS. Since I had a two partition setup, one for / (EXT4) and another for /home (BTRFS), I formatted the / partition but forgot to have /home on my other partition during setup. So now, I have the root and the home folders on the same partition, but my previous larger home partiton from opensuse also shows up and I am able to use that.

I would like my original home partition to be booted as /home during boot. I tried a few /etc/fstab solutions from various forums but the mounting failed. Can someone help me?

Soumya

---

### Post by grahammechanical on 2013-11-02
The really simple solution is to re-install Ubuntu 12.04 LTS using the Something Else option and this time give that home (BTRFS) partition the mount point of /home.

Regards.

---

### Post by soumyas.sarkar on 2013-11-02
@grahammechanical: Yes I am aware of that, but I would not like to re-install the Os gain and I am sure there is some other option. Thanks for your suggestion though

---

### Post by zitch on 2013-11-02
You are probably going to have to boot from a liveCD to do the move to prevent potential issues with having the system being used while messing with mounts.  The basic idea is to move the files from the home directory of / into the root of the new /home partition, setup your fstab (while still in the liveCD), then reboot to the drive, hoping your changes worked. Unfortunately, the devil is in the details, as there is no possible way anybody can give you step-by-step instructions for this without knowing details of your system as a start (device locations and block ids (use "blkid" command) for your root and home partitions).

As with any kind of filesystem operation, be sure you have backups of anything important, and be ready to have to reinstall if you screw up.

I successfully did something similar fairly recently, though it was a migration of having everything installed on harddrive on my laptop, to adding an SSD to it and moving /usr and /var to it, to moving the entire root system to the SSD except for certain directories (like the Music, Videos, and virtualbox directories) being left on the original harddrive, all without reinstalling. It took a while because I had to be sure of each step so that I didn't accidentally delete anything (even if I had a full backup on a USB harddrive available).

---

### Post by oldfred on 2013-11-05
You will need to install btrfs-tools also. I see that uninstalled at the end of my installs. 

synaptic has this warning:
> WARNING: Btrfs is under heavy development, and is not suitable for any uses
other than benchmarking and review.

       10-Way Linux File-System Comparison On Linux 3.10
[http://www.phoronix.com/scan.php?page=article&item=linux_310_10fs&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_310_10fs&num=1)
BTRFS, not ready for prime time
[http://ubuntuforums.org/showthread.php?t=2111487](http://ubuntuforums.org/showthread.php?t=2111487)


 To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

But I have no idea of the correct mount parameters for /home when btrfs. Perhaps you have the OpenSuse parameters as a starting point?

---

