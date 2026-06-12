---
title: "Install ubuntu 14.04.5 as 3rd OS alongside with windows 7 On Raid 0"
date: 2016-11-21
forum: General Help
---

### Post by JDS_Kolkata on 2016-11-21
Hi,
I am an old ubuntu user since 10.04. Lets cut out the long story short. Presently having a system of core 2 quad 9650 with asus p5q deluxe mobo with gskill 2x2 gb of ram. I'm already familiar of ubuntu installation on non raid systems. But this time my problem is not getting solved even after 3 weeks. Presently having 2x500gb Western Digital RE hdd setup as Raid 0 from bios with windows 7 installed as dual boot on 2 partitions (Total partition 8 including OS drives). Make space of another 100 gb in my existing partition table for ubuntu 14.04 installation. Tried installing ubuntu from both desktop and server disc. Desktop version giving ??? ??? dialogue box just after partitioning process. Server edition installed successfully atleast but failed to write grub even after several retrying. My partition scheme which i used for ubuntu are Boot=1 GB, Swap=8 GB and Root=94 GB. At the time of installing from server disc image it given a prompt to enable MDADM Raid & Serial ATA Raid. I had no idea about wht to enable and what to not, so i enabled them both. But due to the non written failure of grub, even after installation of ubuntu still my old 2 windows oses are booting. is there any way to restore ubuntu boot loader alongside with windows? Any assistance is highly appreciated. If step by step guidance available, i am ready to reinstall ubuntu another time....

---

### Post by oldfred on 2016-11-21
The desktop installer has never worked with RAID. It actually now installs, but grub does not.
Back with 12.04 you had to use the alternative(text) installer for RAID or LVM with desktop. Then they obsoleted the alternative with 12.10 and said they would eventually add LVM & RAID to the desktop. In meantime they suggested installing 12.04 & upgrading or install server version and then install desktop of choice.
 Elimination of Alternative installer for 12.10 and no RAID support directly for Desktop.
[http://ubuntuforums.org/showthread.php?t=2049021](http://ubuntuforums.org/showthread.php?t=2049021) 


But they took several years to add LVM as desktop install option, and RAID is not yet fully supported in desktop installer.

You should be able to manually install grub. But with RAID it depends on the type of RAID you have where grub gets installed. Most RAID use sda as correct place. But BIOS RAID or "fakeRAID" you have to install the the root of the RAID or something like /mapper/....

       Does not recommend "fakeRAID"
[http://aryklein.wordpress.com/2013/10/28/a-quick-guide-to-linux-software-raid/](http://aryklein.wordpress.com/2013/10/28/a-quick-guide-to-linux-software-raid/)
[https://raid.wiki.kernel.org/index.php/DDF_Fake_RAID](https://raid.wiki.kernel.org/index.php/DDF_Fake_RAID)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
"fakeRaid" with nVidia, note p1 is partition, without p1 is root of RAID volume
sudo mount /dev/mapper/isw_cdjacjeebj_VOLUME_0p1 /mnt
sudo grub-install --root-directory=/mnt /dev/mapper/isw_cdjacjeebj_VOLUME_0
Hardware RAID drivers
[https://wiki.debian.org/LinuxRaidForAdmins](https://wiki.debian.org/LinuxRaidForAdmins)

       
 Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

---

### Post by JDS_Kolkata on 2016-11-22
Cheers mate. Your suggestion worked. Downloaded and tried to install 12.04.5 from alternate edition disc. At the time of installation it asked only to activate Serial ATA Raid and i did it (No MDADM prompt this time). But grub loader failed to installed in its self detected path (i.e /dev/mapper). Manually pointed to /dev/sda, still failed. Not i have manually pointed the path to "/dev/mapper/isw_bafghabfhf_Volume0" (as suggested by u) (as i want to install on the root of RAID) and it worked. i am able to boot ubuntu alongside with 2 windows 7. Thanks a lot for all your proactive support.

---

### Post by oldfred on 2016-11-22
Glad you got it working.

I think 12.04 expires April 2017.

What little I know about RAID:
 dmraid was replaced by mdadm for handling FakeRAID in Ubuntu 14.04.
15.04 or later now uses mdadm to support intel fakeraids 
User who installed fakeRAID
How to install Ubuntu 14.04 in software fakeraid RAID 1 with Intel Z87 chipset mobo controller
[http://ubuntuforums.org/showthread.php?t=2229126](http://ubuntuforums.org/showthread.php?t=2229126)

---

