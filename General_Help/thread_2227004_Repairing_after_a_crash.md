---
title: "Repairing after a crash"
date: 2014-05-30
forum: General Help
---

### Post by Nosphky on 2014-05-30
My pc suffered a failure requiring replacement of power supply, motherboard and processor.  I took advantage to upgrade to a more modern mboard and cpu.   My working configuration prior to the crash was a dual booting system with Windows7 and UbuntuStudio using the grub boot manager.  Disks configured :

sda1 : ntfs 100 MiB (presumably containing grub ?)
sda2 : ntfs rest of disk - containing Win7

sdb1 : ext4 /root  392 GiB
sdb2 : swap 8 Gib
sdb3 : ext4 /home  100 Gib
sdb4 : ntfs Windows backup 431 Gib

After rebuild, grub loads and UbuntuStudio starts with no apparent problems but Win7 will not start.  If I persist with F8 after selecting Windows from the grub list, Windows starts its repair mode and after about 5 minutes gives up with the explanation that I must have changed something like a periphery - not ultra helpful.  I can't succeed in getting Windows running even in safe mode.

I expect I shall end up by having to reinstall Windows with all the grief that gives.  The UbuntuStudio installation is protected by being on a separate harddrive, I suppose.

Will a re-installation of Windows eliminate grub ?  If so, how do I put it back without reinstalling Ubuntu ?  I'd like to be a little clearer on the implications before launching into a reinstall of Windows so all comments welcome.  Thanks.

---

### Post by Impavidus on 2014-05-30
I don't think a Windows installation is portable enough to work after you changed these components, so that would mean reinstalling Windows. To fully protect your Ubuntu system, disconnect the hard drive containing Ubuntu during Windows installation. If grub is installed on sda, it will be wiped by the Windows installer. If you set boot priority in the bios to sdb, grub will still work, if it has been installed to sdb. You may have to update grub from your Ubuntu system.

It's best to have grub only installed on sdb. With boot priority to sdb, this gives you a normal dual boot grub menu. Whenever sdb fails, you can change boot priority to sda, and Windows will boot.

---

### Post by Nosphky on 2014-05-30
Thank you for the reassurance and hints.

---

### Post by Nosphky on 2014-06-03
Just to close this story - the only way I could eventually re-install Windows7 on sda was to delete the boot partition and reformat the whole disk.   I re-installed UbuntuStudio on sdb with the boot manager on sdb (changed from sda during the installation procedure when you get to the partitioning options.)
I used a live boot from a USB stick with UbuntuStudio 14.04 to prepare sdb.  Once into the live boot, I used Gparted to remove existing partitions and then created 1 new partition.  Then I installed lvm and used this to create logical partitions following the very clear advice in the illustrated tutorial by Herman :
[http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html](http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html)
Finally, I used the install option on the live boot version to install into these logical partitions.
I'm back in business now.

---

