---
title: "Stuck in grub rescue&gt;"
date: 2013-04-17
forum: General Help
---

### Post by jmsorensen on 2013-04-17
Hi there, I am completely new to Linux and Ubuntu, so feel free to talk to me like I'm stupid. First of all, I partitioned 20GB of my HDD to install Ubuntu on. It was working great, until I re-partitioned that 20GB, in hopes of installing a different distro. As you already know, this is now causing my laptop to always boot to the "grub rescue>" screen. I've read extensively online, and on this forum on how to fix this, and nothing seems to solve the particular issue. I will explain a few variables, first of all, it's an Ultrabook so I have no disc drive. Secondly, every command that the internet says to try, yields an "unknown command". The only command that works is "ls" and then it lists my HDD partitions. I am currently downloading Ubuntu onto a a USB drive, in hopes that I can boot to that and fix it that way. My OS is Windows 7, and I had Ubuntu 12.10, and it was installed via a borrowed external disc drive that is no longer accessible. I thank you for any assistance in advanced.

---

### Post by oldfred on 2013-04-18
UltraBooks have Intel SRT which has RAID and causes issues.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

You may have to turn Intel SRT off, remove RAID meta-data and then you can install boot loader. Then you should be able to turn Intel SRT back on.

      
  Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

 Ubuntu on hard drive, re-enable SRT post #19 details
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
> Disable the RAID, it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

---

