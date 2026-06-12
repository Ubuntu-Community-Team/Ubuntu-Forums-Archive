---
title: "Installation fatal error (GRUB)"
date: 2014-06-01
forum: General Help
---

### Post by raider2 on 2014-06-01
Ok, what i have is new haswell pc with:
sda as ssd with boot partition and windows
sdb as standard drive
sdc? as 2-hard drives with RAID 0

what i want to do is install ubuntu on sdb specially prepared space and the end of the drive
what i get is this:

[IMG]http://i.imgur.com/8L7VRtZ.jpg[/IMG]as u can see this is alternative ubuntu cd as recommended by someone for software raid 0
just to be sure this is standard cd: [IMG]http://i.imgur.com/6WgzYWH.jpg[/IMG]

No bios protection or anything

---

### Post by oldfred on 2014-06-01
Post this:
sudo parted -l

Is Windows in UEFI or BIOS boot mode.
Are drives gpt or MBR(msdos). 
Both questions should be answered with command above.

Desktop installer does not have the RAID drivers but if not installing with RAID, then you can easily add drivers afterwards and mount RAID data partitions.

---

### Post by raider2 on 2014-06-02
boot drive is GPT windows is in UEFI

---

### Post by oldfred on 2014-06-02
Is sdb gpt?

If Windows is UEFI, you really want Ubuntu installed in UEFI mode on a gpt partitioned drive. You can install in BIOS boot mode if you have a tiny 1 or 2MB unformatted partition with the bios_grub flag. You can use gparted to create that.

Your error on installing grub is that it is trying to install grub to sda, but since sda is gpt, you need the bios_grub partition for it to install correctly in BIOS boot mode on sda. It would not give an error if you were installing in UEFI mode as then it would install to sda, but use the same efi partition as Windows on sda.

Better to have either or both an efi partition and a bios_grub partition with gpt partitioning on sdb and install grub to sdb when installing. Only with the Something Else option do you get a choice on where to install grub2's boot loader. See combo box at bottom of partitioning screen.

My screen shots still show sda for boot loader install, as I am still assigning partitions.

       Install to external drive. Also any second drive.
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):

      
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

The desktop installer does not have RAID drivers, so you will have to install those afterwards for it to be able to mount your RAID. Not sure which version of RAID you have or which driver is more correct.
      
 sudo apt-get install mdadm
sudo apt-get install dmraid

---

### Post by Papas228 on 2014-06-02
Hello,

I was running into a similiar problem myself when install Ubuntu. The issue for me was where grub was trying to install. On my setup it kept trying to install on the RAID setup. So when I switch the grub installer to the correct drive it installed successfully. Let me know if that suggestion works for you.

Best,

---

