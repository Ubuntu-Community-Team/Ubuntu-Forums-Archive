---
title: "Dual boot Windows 7 and Ubuntu 14.04 LTS Desktop version"
date: 2015-05-10
forum: General Help
---

### Post by tech291083 on 2015-05-10
Hi Friends,

Two days ago, I was teaching a friend of mine how to dual boot Ubuntu 14.04 LTS Desktop distro with Windows 7. Now I tried twice.

Attempt : 1 

Installed Windows 7 Home Basic 64 bit to a perfectly working HDD of size 250 GB.
Did not install any software or any drivers for motherboard etc.
Created a dedicated partition (unallocated space of 100 GB) to install Ubuntu 14.04 LTS Desktop (64 Bit) OS alongside Windows 7.
But when I was installing Ubuntu 14.04 LTS Desktop (64 Bit), it did not recognize the Windows partition and thus did now allow me to install Ubuntu alongside Windows, ultimately forcing me the install only Ubuntu on the entire drive, which did erase Windows partition if any in the end.
============================================
Attempt : 2

Installed Windows 7 Home Basic 64 bit to a perfectly working HDD of size 250 GB.
Did not install any software or any drivers for motherboard etc.
Created a dedicated partition (unallocated space of 100 GB) to install Ubuntu 14.04 LTS Desktop (32 Bit) OS alongside Windows 7.
But  when I was installing Ubuntu 14.04 LTS Desktop (32 Bit), it did recognize the Windows partition and allowed me to install  Ubuntu alongside Windows, so I was able to dual boot Windows with Ubuntu in the  end.

My question, is 32 bit version of Ubuntu more accurate when it comes to recognizing the already existing Windows 7 partition, then 64 bit version? Or am I mistaken here?

Thanks.

---

### Post by efflandt on 2015-05-10
The best way to install Ubuntu when you have Win7 and unallocated space (assuming legacy BIOS and regular msdos partitions, not UEFI) is to select **Other** when it comes to where to install it. There you can select/size/format whatever Linux partitions you want, and where to put grub. I have never had any trouble doing that. I have never used **Alongside Windows** or other methods because I do NOT think that is for installing to unallocated space, and I am not quite sure what they will do or what size partitions I would end up with. If you are working with UEFI or gpt partitions, I have no experience with that yet.

It should not matter if Windows or Linux are 32 or 64-bit. I used to have 32-bit WinXP, 64-bit WinXP beta, and 64-bit SuSE on the same drive. Then I wiped the expired 64-bit WinXP beta and SuSE and installed both 32 and 64-bit Ubuntu (it currently still has both versions of 10.04). That computer used odd LBA geometry (240 heads) and if I let anything change partitions automatically, they change its geometry to 255 heads and nothing boots. When I installed 64-bit WinXP beta, it changed drive geometry, so neither itself nor XP Home could boot, until I fixed the drive geometry by trial and error with Linux fdisk based on a brief glance at fdisk earlier and some math. I caught SuSE before it changed drive geometry when some numbers did not make sense during its install and told it to use partitions, as is. So I always have to manually partition that drive myself, without ever having to reinstall WinXP Home from 2004.

And I sometimes want to put grub somewhere other than the main drive mbr, because some Win7 updates (including a service pack update and other more recent security update) do not work if Windows does not control the 1st mbr and some Win7 programs used to step on grub2 when they stored data in what they "thought" was an unused part of the mbr.

---

### Post by oldfred on 2015-05-10
Did you use Windows to shrink the original NTFS Windows partition and immediately reboot so it can run chkdsk? Windows has to run chkdsk after a resize.
And the Linux NTFS driver will not mount a NTFS partition that needs chkdsk or is hibernated to prevent damage that chkdsk might not then be able to fix.

And did you create an ext4 partition for Ubuntu. Often better to have smaller system partitions and larger data partition(s). A shared NTFS makes it easier to share data without having to write directly into the Windows system partition. Often Windows does not like that, but often a user issue as the Linux NTFS driver exposes all the hidden files & folders that Windows normally hides. And then is more prone to user errors. I used to also change my Windows settings and regularly corrupted Windows.

I often suggest 25GB for / (root) and/or /home or data partition(s). When I still had Windows I had both a NTFS and a Linux data partition.

 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

   Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

### Post by tech291083 on 2015-06-25
> **oldfred said:**
> Did you use Windows to shrink the original NTFS Windows partition and immediately reboot so it can run chkdsk? 


Yes, I did shrink the Windows NTFS partitions and rebooted the pc in order to allow the shrinking of the hard drive.

> 
And did you create an ext4 partition for Ubuntu. 


No, I did not. I normally use the unallocated space created by shrinking the Windows NTFS partition and choose Install alongside Windows option to install Ubuntu.

> 
Often better to have smaller system partitions and larger data partition(s). A shared NTFS makes it easier to share data without having to write directly into the Windows system partition. Often Windows does not like that, but often a user issue as the Linux NTFS driver exposes all the hidden files & folders that Windows normally hides. 


I have never used the Something else option. I have never created any partitions specifically to be shared by both Ubuntu and Windows 7 for keeping data. 

I would love to do that. But do not know how to go about doing that. If I have Windows 7 already installed, which has by default 2 patitions C and System reserve. Now I have a 500 GB hard drive, so what other partitions am I suppsed to create and with what file system type and size in order to dual boot Windows 7 and Ubuntu. I intend to keep 200 GB for Windows 7. And the rest 300 GB for Ubuntu.

I guess I need the following partitions to start with,

Swap
Data (to be shared by both Windows 7 & Ubuntu, but what file system type?)
/root (what size, what file sytem?)
/home (what size, what file sytem?)

Please guide me, thanks.

---

### Post by oldfred on 2015-06-25
I prefer to partition in advance with gparted, but you still have to use Something Else to choose (change button) which partition is used & formatted for which .

 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):

      
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.


[LIST=1]
[*]10-25 GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

