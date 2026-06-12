---
title: "Boot Question: how to remove older OS"
date: 2012-11-14
forum: General Help
---

### Post by thorn1 on 2012-11-14
Hi, I built a machine that has 2 hard drives, one is a solid state and the other a typical (magnetic? 1 Tb ) SATA HD.  I originally installed 10.04 on the 1 Tb drive and it did not find the solid state drive. So I decided to install  edubuntu 12.04 and it found both drives so I installed it on the solid state drive.  I thought it would wipe out the older version.

What's the best way to remove the older vers from the the magnetic 1 Tb drive with messing up the 12.04? I would like to use the 1 Tb drive for file storage, maybe network share, mythtv etc. Is there anything I need to do other than change permissions so that all users can access the drive? Any links that would be helpful in understanding Linux boot?

I ran update-grub ( I hope I didn't mess anything up!) and got:

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-32-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-32-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-29-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-29-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 10.04.4 LTS (10.04) on /dev/sda1


df shows:

Filesystem     1K-blocks     Used Available Use% Mounted on
/dev/sdb1       57692412 23952124  30809600  44% /
udev             1910740       12   1910728   1% /dev
tmpfs             767208     1392    765816   1% /run
none                5120        0      5120   0% /run/lock
none             1918020      200   1917820   1% /run/shm
cgroup           1918020        0   1918020   0% /sys/fs/cgroup
/dev/sda1      953312140  2597244 902289376   1% /media/f37d4841-92d8-4923-9c57-0467bc17dfd3

Thanks!

---

### Post by tedr108 on 2012-11-14
Assuming your PC is booting into 12.04 normally from your SSD, the simplest thing to do is to run Gparted, erase all partitions on your SATA drive and format it as one big data partition (**ext4** is the format I typically use).  Just make sure you reformat the SATA and not your SSD!

If your PC is actually booting into 10.04, rather than 12.04, this is out of my league ... you will have to get your PC to boot from the SSD first.

Please note that I do not know the ramifications of your grub.cfg no longer having 10.04 in existence.  Hopefully, one of the experts here can comment on that, it's probably just a simple update-grub, but not sure.

Anyway, I'd wait for another couple of comments before moving forward...

---

### Post by thorn1 on 2012-11-14
> **tedr108 said:**
> Assuming your PC is booting into 12.04 normally from your SSD, the simplest thing to do is to run Gparted, erase all partitions on your SATA drive and format it as one big data partition (**ext4** is the format I typically use).  Just make sure you reformat the SATA and not your SSD!

If your PC is actually booting into 10.04, rather than 12.04, this is out of my league ... you will have to get your PC to boot from the SSD first.

Please note that I do not know the ramifications of your grub.cfg no longer having 10.04 in existence.  Hopefully, one of the experts here can comment on that, it's probably just a simple update-grub, but not sure.

Anyway, I'd wait for another couple of comments before moving forward...

It was booting on the 12 version OK, I have not rebooted since I ran the update-grub so I'm not sure now. 

I'll try Gparted to see what it shows.

Thanks

---

### Post by chuck_theobald on 2012-11-14
I concur with tedr108, use gparted to flatten your SATA disk. Old school would use fdisk from the command-line. 

I am not greatly familiar with the grub2 way, but "update-grub is a stub for running grub-mkconfig -o /boot/grub/grub.cfg" (from the man page), so you can run grub-mkconfig with -o to generate a new grub configuration file - **away** from /boot/grub - and compare it with your live /boot/grub/grub.cfg file. Once your SATA disk is flattened, I think grub-mkconfig will not find your 10.04 installation, since it will have been eliminated.

---

### Post by grahammechanical on 2012-11-14
You should understand that the last Ubuntu to be installed puts its Grub into the Master Boot Record (MBR) of that drive.

So, it seems as if the machine is loading the 12.04 Grub menu and it has found two Linux kernels to boot. I recently installed another version of 12.04.1 and after installing I ran updates and it brought in that Linux kernel 3.2.0-32 that you see. I also have the older 3.2.0-29 kernel. Do not worry about that at all.

If you format the 1TB drive the format will remove 10.04. Then when you run sudo update-grub from 12.04 (the only Ubuntu on the SSD) it most definitely not find 10.04.

But you will have at least two partitions on the 1TB drive. You will find a partition that was used for 10.04 swap partition. You will have to delete that and then expend the remaining partition to take up the now unallocated space.

You may course have other partitions on the 1TB that we do not know about.

Regards.

---

### Post by thorn1 on 2012-11-14
> **grahammechanical said:**
> 
But you will have at least two partitions on the 1TB drive. You will find a partition that was used for 10.04 swap partition. You will have to delete that and then expend the remaining partition to take up the now unallocated space.

You may course have other partitions on the 1TB that we do not know about.

Regards.


There are 2 other partitions,  /dev/sda5 linux-swap 7.87GB and /dev/sda2, extended also 7.87 GB.  The main files system is /dev/sda1 923 GB. So wipe them out and combine them?

Thanks!

---

