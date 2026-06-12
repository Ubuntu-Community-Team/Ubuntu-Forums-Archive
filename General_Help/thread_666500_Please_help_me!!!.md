---
title: "Please help me!!!"
date: 2008-01-13
forum: General Help
---

### Post by Kube2007 on 2008-01-13
Hi all,

I am after some advice please, I have recently switched operating systems from Vista to Ubuntu 7.10, I am very impressed with it so far but I am a Novice when it comes to Linux & im finding my self struggling with this new way of computing. 

I've being trying to install Vista again but no matter what i do i can not get Vista to install! I've configured my P.C's BIOS to boot from CD, it loads up Vista but when I get to the option of selecting which Hard drive i want to use it says it cant install Vista as the hard drive is not labelled 'NTSC' or something similar.

I've tried using my Windows 98 start up disk so I can run the command prompt but when i go to format my hard drive it says 'format not supported on drive C' i have one hard drive for the record.

Can some one please help me!?

Thanks!

Neil

---

### Post by overdrank on 2008-01-13
> **Kube2007 said:**
> Hi all,

I am after some advice please, I have recently switched operating systems from Vista to Ubuntu 7.10, I am very impressed with it so far but I am a Novice when it comes to Linux & im finding my self struggling with this new way of computing. 

I've being trying to install Vista again but no matter what i do i can not get Vista to install! I've configured my P.C's BIOS to boot from CD, it loads up Vista but when I get to the option of selecting which Hard drive i want to use it says it cant install Vista as the hard drive is not labelled 'NTSC' or something similar.

I've tried using my Windows 98 start up disk so I can run the command prompt but when i go to format my hard drive it says 'format not supported on drive C' i have one hard drive for the record.

Can some one please help me!?

Thanks!

Neil

HI and you can use the live cd and gparted to resize you ubuntu partition and create a fat partition for the windows installation.

---

### Post by Kube2007 on 2008-01-13
Thanks for the swift reply, could you please explain how i would do that?

thanks again!

Neil

---

### Post by bwhite82 on 2008-01-13
You need to format it as NTFS. Pop in the LiveCD, boot into Ubuntu. Then goto (menu) System>Administration>Partition Editor. You should see your Harddisk in the list. Right click on it and click "Format To>NTFS". Click the 'Apply' button at the top. After its finished, reboot with Vista disk in and proceed with installation.

Edit: Better yet, create 3 partitions. One for Ubuntu, one for swap and one for Vista. All can be accomplished in Partition Editor: After you 'Delete' the partition, simply create a new partition half the size of your disk minus 1gb. For instance if your HD is 100gb, create a new partition formatted as EXT3 that is 49gb in size. Create another partition formatted as NTFS that is 50gb in size. Finally the 3rd partition, 1gb in size for swap. Be sure to install Vista first on the 50gb partition. After complete, pop in the Ubuntu disk, install it on the 49gb partition (set as bootable and mount point to /). Set the 1gb partition as 'swap' and install! I know it sounds involved but its really not, GParted makes it easy. You can mess around in it as much as  you want, it won't make changes until  you click 'Apply'.

Edit:Edit: Disregard possible remarks about making your swap twice the size of your RAM, this is a common misconception. Assuming your RAM amount is anywhere between 512mb-2gb, a 1gb swap partition size is fine.

---

### Post by Kube2007 on 2008-01-13
Thanks very much! It's really appreciated, I'll give it a try.

Neil

---

