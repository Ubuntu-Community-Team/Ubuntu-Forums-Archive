---
title: "Dual boot Windows 8.1 and Ubuntu issue...."
date: 2013-08-12
forum: General Help
---

### Post by slug712 on 2013-08-12
Hey guys, 

This may have been somewhat discussed before, but I've Googled the heck out of it and can't seem to find a solution.
And sorry if this is in the wrong place...

Little background. I have a Desktop I do all my playing on. It's a P4 system with 3 HDDs. 2 x 120gb and 1 x 300gb. One 120gb drive was originally in my production system but was been moved into here some time ago when I retired that system to build a new one. That drive had WinXP on and had 3 partitions. The other 2 partitions had my games and media on. The other 120gb drive has Win Server 2003, CentOS and Ubuntu Server. The 300gb drive had a bunch of Linux Distributions and some others to fool around with.
The XP install broke a while ago and I no longer had the disk for it, so I installed Windows Pro 2000 over it. Had no issues.

Fast-forward to a couple days ago. Since I never used Win 2000, I figured I'd install the Preview of Win 8.1 over it. Never used Win8, so figured I'd give it a try.
Install Win 8.1, everything goes good. Reboot and Windows 8.1 loads, As expected(taking over the boot-loader).
No prob as I planned to re-install Ubuntu(on the 300gb drive where it was). Noticed this CPU is EM64T "Capable" and wanted to see if Ubuntu 64 would install.
Install goes good and I installed the boot-loader to the 300gb drive(As a precaution).
Reboot and set the Boot Priority to the 300gb drive.
Reboot and Grub2 pops up and Windows 8 (Loader) is there.\
Select Windows 8 and BANG, PC reboots. Do it a couple more times and PC keeps rebooting.
Stick the Plop Boot Loader CD in, Select the HDA entry, And wahla Windows 8.1 loads. 
Change Boot Priority to the Windows 8 drive, Windows loads.
Change it back to the 300gb drive, Boot Ubuntu and run ```
sudo grub-install /dev/sda
```
Reboot, change boot priority to the Windows drive. I get greeted with Grub2 and the Windows 8.1 (loader) entry is there.
Select Windows 8 and Reboot.....:confused:  Again and Again.
Put in the Plop Boot Loader CD, make the selection, and Windows 8 boots....WTH

Grub2 just won't chainload....:confused:
I'm stumped.

SDA = Windows 8 drive.
SDB = 300gb drive.
SDC = 120gb drive with Server installs.

---

### Post by Slug71 on 2013-08-12
So I took a look in the grub.cfg file and this is what it says,

```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 8 (loader) (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-7AF81FE0F81F9A09' {
	insmod part_msdos
	insmod ntfs
	set root='hd0,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  7AF81FE0F81F9A09
	else
	  search --no-floppy --fs-uuid --set=root 7AF81FE0F81F9A09
	fi
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry 'Windows NT/2000/XP (on /dev/sdb1)' --class windows --class os $menuentry_id_option 'osprober-chain-C66036D16036C847' {
	insmod part_msdos
	insmod ntfs
	set root='hd1,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  C66036D16036C847
	else
	  search --no-floppy --fs-uuid --set=root C66036D16036C847
	fi
	drivemap -s (hd0) ${root}
	chainloader +1
}
```

I noticed that the "drivemap -s", both say "hd**0**". They aren't on the same drive.
The "Windows NT/2000/XP" entry is the Server 2003 install. Which boots fine.
Notice "set root" = "hd**1**,msdos1". Should the drivemap not also say, "drivemap -s (hd**1**) ${root}" on that(Server 2003) install?

Eh..will try it and see what happens.

---

### Post by Slug71 on 2013-08-12
SDA = Windows 8 drive.
SDB = 120gb drive with Server installs.**
SDC = 300gb drive.**[/QUOTE]

Fixed. Couldn't edit the first post.

---

### Post by Slug71 on 2013-08-12
> **Slug71 said:**
> So I took a look in the grub.cfg file and this is what it says,

```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 8 (loader) (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-7AF81FE0F81F9A09' {
	insmod part_msdos
	insmod ntfs
	set root='hd0,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  7AF81FE0F81F9A09
	else
	  search --no-floppy --fs-uuid --set=root 7AF81FE0F81F9A09
	fi
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry 'Windows NT/2000/XP (on /dev/sdb1)' --class windows --class os $menuentry_id_option 'osprober-chain-C66036D16036C847' {
	insmod part_msdos
	insmod ntfs
	set root='hd1,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  C66036D16036C847
	else
	  search --no-floppy --fs-uuid --set=root C66036D16036C847
	fi
	drivemap -s (hd0) ${root}
	chainloader +1
}
```

I noticed that the "drivemap -s", both say "hd**0**". They aren't on the same drive.
The "Windows NT/2000/XP" entry is the Server 2003 install. Which boots fine.
Notice "set root" = "hd**1**,msdos1". Should the drivemap not also say, "drivemap -s (hd**1**) ${root}" on that(Server 2003) install?

Eh..will try it and see what happens.

Ughh....no go. :confused:

---

### Post by Slug71 on 2013-08-12
If anyone else has this issue, I found an old Bug filed on Launchpad.

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/475881](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/475881)

---

### Post by oldfred on 2013-08-13
I do not know if it is BIOS, grub or Windows or even Windows hibernation. (for BIOS versions not UEFI)

A Windows boot loader just jumps to the Windows partition with the boot flag (active partition) and it says to load bootmgr. All grub does is chainload to the Windows partition just like the MBR did. The one thing that is different is that the drive you boot from is always hd0, and Windows expects to be on hd0. Hence the drivemap command to change the drive to boot from to the Windows drive so it is seen as hd0. Perhaps drivemap is not working.

The only work around I have seen is just to install grub to the MBR of the Window drive and boot from it. Then it is hd0. I prefer not to have to do this as I like each drive to have that install's boot loader. But installing grub to the Windows drive or using your one time boot key (f12) to use BIOS to boot Windows are the only other choices that I know of.

---

### Post by Slug71 on 2013-08-13
> **oldfred said:**
> I do not know if it is BIOS, grub or Windows or even Windows hibernation. (for BIOS versions not UEFI)

A Windows boot loader just jumps to the Windows partition with the boot flag (active partition) and it says to load bootmgr. All grub does is chainload to the Windows partition just like the MBR did. The one thing that is different is that the drive you boot from is always hd0, and Windows expects to be on hd0. Hence the drivemap command to change the drive to boot from to the Windows drive so it is seen as hd0. Perhaps drivemap is not working.

The only work around I have seen is just to install grub to the MBR of the Window drive and boot from it. Then it is hd0. I prefer not to have to do this as I like each drive to have that install's boot loader. But installing grub to the Windows drive or using your one time boot key (f12) to use BIOS to boot Windows are the only other choices that I know of.

Thanks for the response oldfred.

The drive order in my first post is wrong. Its actually SDA(120gb - Win8.1) = HD0, SDB = HD1(120 - Servers) and then SDC = HD2(300gb).
So Windows 8.1 is on HD0. While I installed Ubuntu to SDC(HD2) and installed the bootloader(Grub2) to that drive, I did also install it to the MBR of HD0 later as you see in my first post.

So I'm not sure what the hell is up with it.

It could well be a Windows change. Both Windows Server and Windows 2000 Pro were not on HD0 at the time of install and I never I had any issues with those. A Google search doesn't bring up many similar issues, but there are a few. Seems it all started with Windows 7.

---

### Post by oldfred on 2013-08-13
I have seen one or two others with similar issue in the forums. Not sure if resolved or not, or if booting with grub in the MBR of the Windows drive worked or not.
Some change to use EasyBCD, or just using one time boot key. It may depend on how often you reboot or need either Windows or Ubuntu.

---

### Post by Slug71 on 2013-08-13
> **oldfred said:**
> I have seen one or two others with similar issue in the forums. Not sure if resolved or not, or if booting with grub in the MBR of the Windows drive worked or not.
Some change to use EasyBCD, or just using one time boot key. It may depend on how often you reboot or need either Windows or Ubuntu.

Yeh most of the people that ran into this issue chose to go the EasyBCD route it seems. I thought about it...but don't think we should have to do that work around. 
I earlier today, just ran ```
bootrec /fixmbr
``` from Command Prompt to restore the Windows loader. So i just have to go in and change the boot device in BIOS to access either 8.1 or any of the others. Beats having to stick a CD in everytime to chainload Win8.1. Which I'll probably hardly use. 

Thanks again.

---

### Post by oldfred on 2013-08-13
You should have a one time boot key that lets you choose which device to boot. I have 4 hard drives and do have different grubs installed in each. While I can boot everything from a grub menu, I let the very new install just default to install to sda and directly boot it with f12. My default and main working install is the sdd drive.

---

### Post by Slug71 on 2013-08-14
> **oldfred said:**
> You should have a one time boot key that lets you choose which device to boot. I have 4 hard drives and do have different grubs installed in each. While I can boot everything from a grub menu, I let the very new install just default to install to sda and directly boot it with f12. My default and main working install is the sdd drive.

Thanks again oldfred,
Will press some buttons and have a look. :D

---

### Post by emsmith18 on 2013-10-24
I am having this very same issue. Booting Windows 8.1 from GRUB causes the computer to simply restart and GRUB to load again. Win 8.1 will boot fine if you change the boot priority in BIOS however I don't want to do this every time I need to boot into Win 8.1. Has anyone solved this problem. I am a newbie to Linux/Ubuntu but I do have a moderate knowledge/skill with computers. Any help would be greatly appreciated...

---

### Post by oldfred on 2013-10-25
If you have fastboot still turned on that can be an issue. For whatever reason grub cannot chainload to Windows when hibernated. 

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
Force removal of hiberfil from Ubuntu
[http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/](http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/)
[http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx](http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx)
User who fixed Windows 8
[http://ubuntuforums.org/showthread.php?t=2171156s](http://ubuntuforums.org/showthread.php?t=2171156s)

---

