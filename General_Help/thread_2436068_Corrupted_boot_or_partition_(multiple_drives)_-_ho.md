---
title: "Corrupted boot or partition (multiple drives) - how to recover"
date: 2020-01-30
forum: General Help
---

### Post by linux-wannabe on 2020-01-30
I had a perfectly functional dual boot, with ubuntu+windows 10 but somehow on that drive dban ran for .02% before i realized my mistake.  Now i can't boot - so what I did was I took another internal drive I had and installed lubuntu and login there to fix things.
First I ran testdisk to see if my data on dual boot was intact and it was not - the linux distro was not readable. However windows was. I went ahead and wrote MBR on the 1st sector of the original drive. and had boot repair reinstall grub to launch windows as default os. 
[http://paste.ubuntu.com/p/b52FX8TZNS/](http://paste.ubuntu.com/p/b52FX8TZNS/)

Now the issue is that I get the grub menu to select, but when I select windows, i get error winload.exe can't be found. 

Thanks in advance.

---

### Post by oldfred on 2020-01-30
Looks like you have a testdisk boot loader in MBR of sda.
Does that directly boot Windows?

Is issue on sda1, becuase of  your dban?

Your sdb says it is a 6GB drive but MBR partitioned?
All drives over 2.2TiB must be gpt or else you convert them back to the MBR maximum of 2TiB.

If you want to install a BIOS boot of grub to a gpt drive, you must have a 1 or 2MB unformatted partition with the bios_grub flag inside the first 2TB of the drive.

GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)

---

### Post by linux-wannabe on 2020-01-30
Replies inline. 

> **oldfred said:**
> Looks like you have a testdisk boot loader in MBR of sda.  <-yes cuz I used testdisk to install MBR on 0 sector. 
> **oldfred said:**
>  Does that directly boot Windows?  <--windows OS is on sda2 but how it was booting prior to the mess i had no clue - i guess linux was on sda1 and it had grub. 

> **oldfred said:**
>   Is issue on sda1, becuase of  your dban?   <---yes, and now i suspect some windows/system32 may be impacted too). 


> **oldfred said:**
>  Your sdb says it is a 6GB drive but MBR partitioned?  
All drives over 2.2TiB must be gpt or else you convert them back to the MBR maximum of 2TiB.
If you want to install a BIOS boot of grub to a gpt drive, you must have a 1 or 2MB unformatted partition with the bios_grub flag inside the first 2TB of the drive.    (this is not my worry right now but look into gpt later - goal is to understand how to get the sda2 windows running).

---

### Post by yancek on 2020-01-31
You will not be able to fix or repair or replace windows files such as winload.exe from Ubuntu or any Linux system.  You will need a windows installation disk or repair disk you created immediately after install or first boot.  If you don't have it, you should be able to download the needed software from the microsoft site or a reliable windows site.  What happens when you follow the suggestion of boot repair and boot from sdb, the 5.5TB disk on which you have LXLE?  You indicate that you installed Lubuntu on another drive to try to repair the system(s) but I don't see any sign of Lubuntu in your boot repair.

---

### Post by linux-wannabe on 2020-02-01
Yes I have windows 10 on usb as installation drive. I tried using this to fix my windows installation, but it doesn't quite work - complains that the volume is not on a recognized file system. Pls make sure the required file system drivers are loaded and that volume is not corrupted. Lubuntu is only the 5.5TB disk and i used this OS to successfully see that windows installation on dev/sda2 is broken. I dont have issue with booting either from dev/sda nor dev/sdb. Issue is that windows wont' start and i dont think ms offers any way to repair the existing installation on dev/sda2/.

So what I am finally ending up doing is, logging into dev/sdb1. see the files of windows installation, copy all the relevant data I need. 
Then overwrite windows with a new windows installation - re do all application software and driver installation on it. shucks. but hey for a corrupted file system be it windows, or linux both not a nice problem to have :(

---

### Post by oldfred on 2020-02-02
Have you run chkdsk from your Windows repair flash drive on all your NTFS partitions?

Windows is particular about NTFS partitions and if the PBR, partition boot sector is not correct Windows will not boot. Chkdsk normally repair that also.

---

