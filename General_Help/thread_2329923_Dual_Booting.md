---
title: "Dual Booting?"
date: 2016-07-06
forum: General Help
---

### Post by xiremy on 2016-07-06
I chose to install ubuntu 16.04 alongside Windows 7. Windows 7 is not listed in GNU Grub when i boot. I need linux to compile a project but i also need Windows for just about everything else.

I did the OS probe thing:
```

remy@remy-ubuntu:~$ sudo os-prober
/dev/sda1:Windows 7 (loader):Windows:chain

```

Does this mean i no longer have Windows 7 installed? I still seem to have all my files on the Hard Drive.
How can i get both Ubuntu and Windows 7 from here?

---

### Post by howefield on 2016-07-06
Thread moved to the "*General Help*" forum.

---

### Post by Impavidus on 2016-07-06
It seems to detect Windows. Sometimes, for some unclear reason, things don't work correctly during install. Try to get the Windows entry into the grub menu by running```
sudo update-grub
```update-grub will run os-prober and put an entry into the menu.

You do see the grub menu, right? In a default install, the menu is hidden when only one OS is detected.

---

### Post by ajgreeny on 2016-07-06
Run the Boot-info-script from Boot-Repair in my signature below and copy the pastebin link back here so we can see what is going on. Do not at this stage accept the default repair; just run the boot-info-script.

---

### Post by Bucky Ball on 2016-07-06
> **Impavidus said:**
> [/code]update-grub will run os-prober and put an entry into the menu.


If the quick and easy way above doesn't work, go on to ajgreeny's suggestions in post #4.

---

### Post by xiremy on 2016-07-06
**EDIT: So the quick and easy method posted above worked. Once i updated grub i can now boot into Windows. In the event My external hard drive fails or grub fails is there a way to restore my original booting method? Might it be better just to make an Ubuntu Partition on my main Hard drive? Thanks for the help guys i really appreciate it. Wouldn't have figured it out myself xD**

Yes the Grub menu does indeed show up.
Okay so i have an idea of whats going on but i think it makes things worse ><
So it appears i have installed Ubuntu on my external hard drive. (I noticed when boot-info asked me if it was removable)
If i remove everything and reboot my PC it still tries to boot through grub (even if i select my hard drive as boot device) SO still cant boot into windows.
Also here is my boot-info log you requested:
[http://paste2.org/Ntgm6FW8](http://paste2.org/Ntgm6FW8)

---

### Post by yancek on 2016-07-06
There is no entry for windows in the grub.cfg file you posted so you can't boot windows.  You need to run:  sudo update-grub and watch the output for a windows entry.  If one shows, try to reboot and select it to test that it works. 

You have 'grldr' on the windows partition which is not a Grub file.  Were you using something like Grub4Dos at one time?

You have a FAT32 partition on sdb (sdb1).  What's that all about?  Not needed or useful for any Linux install which is what you have on that drive.  

If you want Ubuntu booting from the second drive, you need to install the Grub boot loader to the MBR of that drive (sdb).  Do this before you try to change the MBR of sda which currently has Grub code.  Use your windows installation DVD to do this but do it after you have installed Grub to the MBR of sdb or the machine will be unbootable.  Make sure you test this first by setting the second drive to first in boot priority in the BIOS.

Just re-read your last post and if I am reading it correctly now, you are able to boot both windows and Ubuntu, right.  So install Grub to the MBR of the drive it is on (sdb) and then install windows code to the MBR of it's drive with the installation DVD.  If you don't have one, there might be some software available to use for this, I don't use windows so I'm not sure.

---

### Post by oldfred on 2016-07-06
Boot-Repair's advanced mode lets you choose an install and the drive to install a boot loader into.
So you should be able to choose Ubuntu and sdb.
And choose Windows and sda.
 Due to license issues, it cannot install the Windows boot loader but will install syslinux which works just like the Windows boot loader (or better). 
If you want the Windows boot loader you need your Windows repair flash drive and run fixMBR from repair console.

Then set BIOS to boot external first, then internal. If external not found it will boot Windows. Or if external plugged in, grub will let you boot either system.

But grub may have a setting on which drive it originally installed into. And on a major update will reinstall to your sda or internal drive.
 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see similar drive info
sudo lshw -C Disk -short  

 #to get grub2 to remember where to reinstall on major updates
sudo dpkg-reconfigure grub-pc 
#Enter thru first pages,tab to ok, spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

---

### Post by xiremy on 2016-07-06
> **oldfred said:**
> Boot-Repair's advanced mode lets you choose an install and the drive to install a boot loader into.
So you should be able to choose Ubuntu and sdb.
And choose Windows and sda.
 Due to license issues, it cannot install the Windows boot loader but will install syslinux which works just like the Windows boot loader (or better). 
If you want the Windows boot loader you need your Windows repair flash drive and run fixMBR from repair console.

Then set BIOS to boot external first, then internal. If external not found it will boot Windows. Or if external plugged in, grub will let you boot either system.

But grub may have a setting on which drive it originally installed into. And on a major update will reinstall to your sda or internal drive.
 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see similar drive info
sudo lshw -C Disk -short  

 #to get grub2 to remember where to reinstall on major updates
sudo dpkg-reconfigure grub-pc 
#Enter thru first pages,tab to ok, spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

Great information! Thanks for all the help!
I've decided it would probably be best to install Ubuntu on a partition on my Main Hard (That has windows on it as well).
To go back to Ubuntu installation would i need to repair my Windows MBR and then unplug my external during Ubuntu Install?

---

### Post by oldfred on 2016-07-07
A new install on same drive as Windows will just install a new copy of grub to MBR. If you have external connected and run sudo update-grub it will then let you boot both Ubuntu & Windows. 

But since you have a full install on external, I would still install grub to the MBR of the external drive. Then that drive can be booted if main drive ever fails or from another BIOS system. Or even a newer UEFI system, but in CSM/BIOS boot mode, but then better to be UEFI boot mode.

But if Windows issues, still be to have Windows repair disk available. Grub only boots working Windows and only some Windows repairs can be done from Linux. Windows often needs chkdsk and that is only available with Windows, not Linux.

---

### Post by xiremy on 2016-07-07
Right, i no longer have full use of my external because of Ubuntu is installed on it. What im saying is i want to launch Ubuntu installer and install on a partition on my main Hard Drive so i can reformat my external and have full use of it again. To do that will i need to restore my Windows MBR first?

---

### Post by oldfred on 2016-07-07
Only if you want to boot Windows without external's grub and before you do the new install into internal drive.
New install will also create a grub for dual booting.

Be sure to only use Windows 7's own tools to shrink the NTFS partition and reboot immediately so it can run chkdsk.  But you can boot Windows with grub and external.

       Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[URL="https://help.ubuntu.com/community/Grub2/Installing"]https://help.ubuntu.com/community/Grub2/Installing
[/URL]
 [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) 

But I like to have at least a small bootable install of Ubuntu on all drives, even those that are only data drives. My 64GB flash drive has about 20GB for Ubuntu and rest for data. And since not a main working install with lots of programs and data, my / could have been a lot smaller.

[URL="https://help.ubuntu.com/community/Grub2/Installing"]
[/URL]

---

