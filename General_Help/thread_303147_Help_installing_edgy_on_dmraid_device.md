---
title: "Help: installing edgy on dmraid device"
date: 2006-11-19
forum: General Help
---

### Post by aoberoi on 2006-11-19
I need some help on how to get Edgy installed so ill describe my system:

I have 2 300GB Seagate drives in a VIA VT8237 sata raid controller set up in raid0. i already have an 85GB partition set up for windows that is active and boots. I have a 232gb NTFS partition which is for documents and settings in windows (that i will be trying to share in linux using ntfs-3g). As there is an extended partition that is 6GB that has 2 logical partitions in it. The first is 5GB and i wish to mount that as /home in Ubuntu. The second is 1GB and i wish to use that as swap space. then i have another 6GB partition which i would like to use as root. The rest of the hard disk is unallocated.

In the end I may be adding more OSs to the machine. Specifically Vista. I have read some triple boot setup procedures and it seems that the best way to have one bootloader menu that you can use to choose from any OS is to first boot with windows xp NTLDR and when Vista installs it will import the contents of boot.ini from NTLDR. Keeping this in mind, I will be keeping my windows partition active so that i can do a chain load into ubuntu using the procedure described in [this page]("http://www.thinkwiki.org/wiki/How_to_setup_boot_loaders#Using_the_NT_Boot_Loader_to_boot_Linux").

To clarify what position Im in right now, I tried using this [HowTo]("https://help.ubuntu.com/community/FakeRaidHowto") and got as far as making my partitions and formatting them to the filesystems i want. After this, I tried using Ubiquity and the initially i was given the option to use my /dev/mapper/pdc******** device but then when it got to the partition manager (looks like gparted) the device is not listed in the drop down in the upper right corner. instead all i see is 2 300GB disks sda and sdb. The instructions from there confuse me because I dont have a /boot partition and once again, I will be only installing the bootloader to my root partition because I will be booting with NTLDR.

From my understanding, using mdadm means that any partitions on the raid will not be usable form other OSs. In my case, i need to use Windows on the machine as well so this will not work for me.

As for installing using the alternate install CD; i tried doing this as ive seem some people suggest, (selecting text setup) and there was really no difference in which partitions were seen by the installer.

Any help would be greattttttly appreciated as i have spend many days on this problem.

---

