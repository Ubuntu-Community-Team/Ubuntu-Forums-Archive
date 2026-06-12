---
title: "Ubuntu Boot Crash Problem Help Needed 6.10 Edgy Eft"
date: 2007-03-21
forum: General Help
---

### Post by SFHasan on 2007-03-21
Hello All,

I am relatively a new but pretty amazed and convinced user of Ubuntu 6.10 Edgy Eft, after trying various flavours (distributions). This is by far the most user friedly release I have seen for mainstream desktop users, yet when it comes to boot crash and system errors, very little can be resolved by just a simple re-installation over the previous messed up copy on the hard disk. 

My hardware configuration is as follows ;

HP Pavillion Laptop Dv1000, Celeron 1.7 Ghz, 512MB RAM, 80GB HardDisk and the usual peripherals which are always a part of the package.

I created around 10GB of unpartitioned space and installed Ubuntu with its own automatic partitioning option of defining the root and the swap partition. Now my system was a Dual Boot with Windows XP SP2 and Ubuntu 6.10 with a GRUB selection at startup working just flawlessly. I was able to install a good bunch of all working softwares for multimedia, browsing, CD/DVD playing and burning, fonts, bluetooth and some good amount of Eye-Candy too using AIGLX and BERYL. Everything was working fine and both OS were living in peace and harmony.

And then the bad day has dawned today, as I tried to access Linux partitions from within windows. For this purpose I used the EX2IFS driver/software from [http://www.fs-driver.org]("http://www.fs-driver.org"). It was installed and working amazingly seemless with my linux partitions (which is Ext3 and the software mainly for Ext2 claims to be perfect for it too). 

But after installation of EX2IFS, when I rebooted into GRUB to get into UBUNTU, the boot process always crashes and shows the strange following message ( I have attached the screenshot as well).

```

init: Unable to execute "/bin/sh" for rcS: No such file or directory
init: rcS process (1880) terminated with status 1
init: Unable to execute "/bin/sh" for rc-default: No such file or directory
init: rc-default process (1881) terminated with status 1
```

I tried searching around for a similiar problem with a remedy, but in vain. I am not sure that whether this problem is caused by EX2IFS access driver in Windows, since its websites says it works just great without any harm to the linux partititions. The troubleshooting section on the website has nothing much too, since I never renamed my linux partitions under windows.

I hope some help is out there, I have tried booting in the recovery mode and it freezes at the same location where the normal bootup does. I tried booting using the Live-CD, but not much of recovery options are known to me by using it.

Any help would be highly appreciated, since RE-INSTALLATION is certainly the last option I am thinking of, cause of all the nice desired customization of the system would be lost and to be done again, which is a time intensive task. :( 

Thanks in advance.

Best Regards,
S.F.Hasan

---

