---
title: "Neither Ubuntu nor windows7 boots after ubuntu installed"
date: 2015-03-12
forum: General Help
---

### Post by forty3 on 2015-03-12
So I installed Ubuntu to give it a try, but now computer boots neither OS and just gets stuck on a black screen.

I installed boot-repair and ran it from the live USB and it said to paste this for help

[http://paste.ubuntu.com/10583878/](http://paste.ubuntu.com/10583878/)

---

### Post by TheFu on 2015-03-12
Excellent work so far.  It will really help.

Looks like your system can be either EFI or legacy BIOS boot.  Use the same mode that Windows uses.

Looks like you have 3 different HDDs. Grub needs to be installed on the same HDD that Widows uses .... **OR** you can change the boot HDD in at the BIOS boot screen every time you want to switch OSes. For most people, it is easier to leave BIOS alone and let grub boot Linux or Windows based on a menu.

Looks like you have both MBR and GPT disks.  Windows requires EFI boot to boot off GPT disks. I don't know if this is required for Windows to access GPT disks or not. I'm positive that Linux doesn't care - booting or just access whether a disk is GPT or MBR.

Ok - since you have nothing to loose, boot into a liveCD (or boot repair) and open a terminal. Then run:```

sudo grub-install /dev/sda
sudo update-grub
```

More information about grub than anyone wants to know: 
   [http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html) - it isn't beta anymore either, so don't worry about that statement in the last link.

---

### Post by oldfred on 2015-03-12
With multiple drives I prefer to keep each system on its drive including its boot loader. But then you do have to change BIOS to boot grub/Ubuntu drive as default. Grub will offer to boot Windows on its drive. And then if you have major issues with grub, you can still change BIOS to directly boot Windows drive. Grub also only boots a working Windows, so if Windows issues, you often have to directly boot it, to try to get into repair console or use a Windows repairCD or flash drive.

Windows can read/write gpt partitioned drives since XP. But all Windows versions only boot from gpt partitioned drives with UEFI. 

Boot-Repair does try to install grub to every MBR with its auto fix. With multiple drives, you usually do not want grub in every MBR, so advanced mode is better as you can choose install & drive to install its boot loader into. And with a gpt drive grub will not correct install unless you also have a tiny 1 or 2MB unformatted partition with the bios_grub flag anywhere on drive.

I might reinstall the Windows boot loader into sda, just to make sure you can boot Windows ok. 
It also looks more like you put the installer (which has both BIOS & UEFI boot) on sdc1 and then also installed Ubuntu to sdc5. 
If you set sdc as boot drive in BIOS can you boot? Does grub menu show. Can you boot Windows. 

Black screen with Ubuntu is often a video driver or possibly another driver issue.
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by forty3 on 2015-03-12
No matter which drive I attempt to boot on it shows a cursor scroll for a second then remains on a black screen, so no grub menu unfortunately.
While on the black screen the only way to reboot is power off and power on.


attempted first reply but didn't work out, gave me a new pastebin  [http://paste.ubuntu.com/10588534/](http://paste.ubuntu.com/10588534/)

attempting second reply info now.

also having this issue with updating grub
/usr/sbin/grub-probe: error: failed to get canonical path of `/cow'.

---

### Post by forty3 on 2015-03-12
No luck, but I noticed when running lsblk
there is no boot mountpoint, not sure if thats normal


NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 698.7G  0 disk 
|-sda1   8:1    0   100M  0 part 
`-sda2   8:2    0 698.5G  0 part 
sdb      8:16   0 931.5G  0 disk 
`-sdb2   8:18   0 931.4G  0 part 
sdc      8:32   0 149.1G  0 disk 
|-sdc1   8:33   0   121G  0 part /media/ubuntu-gnome/SEA_DISC
|-sdc2   8:34   0     1K  0 part 
|-sdc5   8:37   0  24.2G  0 part /media/ubuntu-gnome/c492ccce-1c8f-4afb-989f-161
`-sdc6   8:38   0   3.8G  0 part [SWAP]
sdd      8:48   1   3.7G  0 disk 
`-sdd1   8:49   1   3.7G  0 part /cdrom
loop0    7:0    0 978.8M  1 loop /rofs

---

### Post by oldfred on 2015-03-13
If you try installing grub without mounting the drive then it tries reinstalling grub to CD or flash drive and gives the /cow error as that is the live installer.

Grub does not use boot flag. And most desktops do not need a /boot nor should have one. Server type installs or LVM, RAID may need a /boot and a few very old or possibly installs to large external drives thru USB port may need /boot or preferred a smaller / at beginning of drive. 

Did you use Boot-Repair's advanced mode to reinstall grub and Windows boot loader to sda?
Also now script is not showing Windows boot files in sda1 & sda2? Is that something with script or did you delete them?

---

### Post by forty3 on 2015-03-13
I didn't delete them, not sure what happened there.  I am going to try to run boot-repair advanced and place it on window drive

attempting reboot now, this is new pastebin it had if it doesn't work  [http://paste.ubuntu.com/10594400/](http://paste.ubuntu.com/10594400/)

still booting to black screen, it freezes on black screen just after a beep.

---

### Post by oldfred on 2015-03-14
You did not install a Windows boot loader to sda? That is an option in Boot-Repair.

Is it BIOS or grub that is giving black screen? And in BIOS which drive are you selecting to boot from. You should also be able to select alternative drives with a one time boot key often f10 or f12 but varies by vendor.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

