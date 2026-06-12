---
title: "Advise on Creating New OS on Different HD"
date: 2019-03-25
forum: General Help
---

### Post by Quarkrad on 2019-03-25
I currently dual boot win10 and Ubuntu 18.04 on a SSD (sda).  I also have three other (sata) HDs in my PC that I use for storage - I need to install an instance on Gnome 3 and for numerous reasons do not/cannot use my SSD.  There is enough room on my sata discs so I'm thinking of using one of them.  It is simply a case of creating a new partition (using gparted), installing Gnome 3, booting to my (SSD) Ubuntu 18.04 environment and run **update-grub**?  Will grub pickup my Gnome3 partition and add it to the list of boot options?

---

### Post by Dennis N on 2019-03-25
> **Quarkrad said:**
> I currently dual boot win10 and Ubuntu 18.04 on a SSD (sda).  I also have three other (sata) HDs in my PC that I use for storage - I need to install an instance on Gnome 3 and for numerous reasons do not/cannot use my SSD.  There is enough room on my sata discs so I'm thinking of using one of them.  It is simply a case of creating a new partition (using gparted), installing Gnome 3, booting to my (SSD) Ubuntu 18.04 environment and run **update-grub**?  Will grub pickup my Gnome3 partition and add it to the list of boot options?

Not quite. In UEFI, the new Ubuntu will install grub bootloader files to EFI system partition (ESP) on sda (overwriting the original ubuntu bootloader files). Even though there is an option to install to sdb, it's not functional. So after installing, when you reboot it will boot into the new install. A solution is to copy the grub.cfg file from the ubuntu folder* on the ESP (/boot/efi/EFI/ubuntu/grub.cfg) to a safe place before starting the install, and then after install, copy it back to restore the original boot target. 

A second option is to edit the new grub.cfg that the new OS created to point to the original 18.04 on the SSD.  This avoids the need to copy and restore the original grub.cfg. For an experienced user that knows what to fix, this is requires fewer steps.

After either option, you will then reboot into the old 18.04, and then run sudo update-grub to add the new OS to grub menu.

*the way Ubuntu has set up permissions, getting to that folder is not easy. Ask for help if needed.

---

### Post by Quarkrad on 2019-03-25
Thank you Dennis.  This is the contents of my grub.cfg:

```
search.fs_uuid dd8cb5d2-8f60-4611-a48b-0eec7d443e11 root hd0,gpt5 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg
```

Not very exiting!  Are these contents normal/OK?  I intend to copy this file, via sudo, to a usb stick; install ubuntu 18.04 into a new partition on my new HD and then, using live CD, copy grub.cfg from the usb stick to **/boot/efi/EFI/ubuntu/grub.cfg** on my SSD.  Which I believe is your suggestion above.

---

### Post by yancek on 2019-03-25
The actual Grub file with the menu you see on boot is in the boot directory of your Ubuntu 18.04 system partition.  THat is what this grub.cfg file is pointing to which you can see:  hd0,gpt5 which would be sda5 and the series of characters just prior to it is the UUID so if you do as suggested above, it should work if you don't change the Ubuntu partition.

---

### Post by Dennis N on 2019-03-25
> **Quarkrad said:**
> Thank you Dennis.  This is the contents of my grub.cfg:

```
search.fs_uuid dd8cb5d2-8f60-4611-a48b-0eec7d443e11 root hd0,gpt5 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg
```

Not very exiting!  Are these contents normal/OK?  I intend to copy this file, via sudo, to a usb stick; install ubuntu 18.04 into a new partition on my new HD and then, using live CD, copy grub.cfg from the usb stick to **/boot/efi/EFI/ubuntu/grub.cfg** on my SSD.  Which I believe is your suggestion above.

Yes, this is the right file, and you have the right procedure.

---

### Post by Quarkrad on 2019-03-25
Hmm... interesting.  I went ahead and installed a new version of ubuntu 18.04 on /dev/sdd3 - rebooted to live CD and navigated to my ssd (inorder to copy grub.cfg).  Strange but the /boot/efi folder had nothing in it(?) - on boot I got the grub> prompt on a blank screen. So, rather than bother you I thought of doing a grub reinstall.  All is well (sort of) in that I have a grub screen and can boot into my original Ubuntu Mate and Win10.  The attached shows my grub menu - when I click on either of the entries the arrows point to I get the following message:

[B]error: no such device: de0706.....5c1af
error: disk 'hd3, msdos3' not found
error: you need to load the kernel first

Press any key to continue[/B]

I have checked via Gparted that ubuntu 18.04 is installed on sdd3 and that the partition/UUID is de0706.....5c1af

---

### Post by oldfred on 2019-03-25
Did you install in UEFI or BIOS boot mode?
Grub only installs in UEFI boot mode to ESP on first drive usually sda or first NVMe drive.
And new install then changes the UUID & drive info in the 3 line grub configfile entry that is in /EFI/ubuntu/grub.cfg and is just to load the full grub.cfg in you install. Then that grub can boot other installs if sudo update-grub is run.

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Do not run any auto fix until someone has reviewed your configuration. With multiple drives & multiple installs it does not always make best choice. But you usually can use its advanced mode.

---

### Post by Dennis N on 2019-03-25
>  ...rebooted to live CD and navigated to my ssd (inorder to copy grub.cfg). Strange but the /boot/efi folder had nothing in it(?)
 Since you are working from a live CD, the OS on your SSD is not booted and /boot/efi is not mounted, so it's empty.
 
 Don't use the live CD. I wasn't thinking you would try that. After installing, you reboot to grub of the (new) OS. From there, boot either OS and then copy the grub.cfg you saved back to /boot/efi/EFI/ubuntu/grub.cfg
 
Finally, reboot and the computer will boot to the original Ubuntu 18.04 on the SSD;  then, run sudo update-grub to add the new OS to the grub menu.

Added stuff:

> on boot I got the grub> prompt on a blank screen.
Not clear what happened here.
> All is well (sort of) in that I have a grub screen and can boot into my original Ubuntu Mate and Win10...when I click on either of the entries the arrows point to I get the following message:
```
error: no such device: de0706.....5c1af
error: disk 'hd3, msdos3' not found

```
Not sure what is the cause here - those entries for the new OS would have been created by Ubuntu MATE's OS prober after an update-grub. I'm also not clear about your disks. In the customizer, you have sda then sdd. How many disks are there? 4? 
If you post the requested (by oldfred) boot info summary, it might give some clues.

---

### Post by Quarkrad on 2019-03-26
Boot summary info:
[https://paste.ubuntu.com/p/JfKHcBdW2x/](https://paste.ubuntu.com/p/JfKHcBdW2x/)

I have 1 x SSD and 4 x sata disks in my pc

SSD
sda 1-3  win10 system partitions
sda4   win10 OS
sda5   ubuntu mate 18.04 /
sda6   ubuntu mate 18.04 /home

HD
sdb1  ext4 storage
sdb2  ntfs storage (I use this for virtualbox images)

HD
sdc1  ext4 used for storage

HD
sdd1  ext4 used for storage
sdd2  ntfs used for storage (media files/music)
sdd3  NEW PARTITION - new install of ubuntu 18.04 (I need gnome3)

HD
sde1  ext4 used for Backup

---

### Post by Dennis N on 2019-03-26
```
Disk /dev/sdd: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
[COLOR="#FF0000"]Disklabel type: dos[/COLOR]

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1          41,969,664 1,748,723,711 1,706,754,048  83 Linux
/dev/sdd2       1,748,723,712 1,953,523,711   204,800,000   7 NTFS / exFAT / HPFS
/dev/sdd3               2,048    41,968,844    41,966,797  83 Linux

```
This is an MS-DOS partitioned disk (Disklabel type: dos). It can only be used with a BIOS type install. You can't boot an OS on here from a UEFI based installation like you have on sda. Notice sda is "Disklabel type: gpt" where the OS is UEFI based. 

You would have to re-do the sdd disk with a GPT partition table:

In gparted, **Device > Create Partition Table > GPT** (save any data you want to keep - this destroys any data on the disk) then create an EFI system partition (format fat32 with boot flag set - 100 mB is enough) just in case you want it later, and an ext4 partition for the new Linux OS. Then redo the installation, booting your installer in UEFI mode and selecting the new partition for use as / through the "something else" option in Installation Type. After installing, reboot and copy the grub.cfg you have saved to the EFI system partition on sda. Reboot again. update grub to add the new os to grub menu.

Then it should work fine.

---

### Post by oldfred on 2019-03-26
You still need good backups of all data on sdd, but this usually works.
       Converting from MBR to gpt:
[http://ubuntuforums.org/showthread.php?t=1454252](http://ubuntuforums.org/showthread.php?t=1454252) 
    
How you boot install media UEFI or BIOS is then how it installs.
Once Windows or main working install is UEFI, then you should use gpt for all drives and UEFI for all installs.

---

### Post by Quarkrad on 2019-03-26
I've converted sdd to gpt but when I choose that option (**Ubuntu 18.04.2 LTS (18.04) on /dev/sdd1**) in the grub menu I get a similar error output as in #6.  My current boot info is: [http://paste.ubuntu.com/p/TkgFQdTf4M/](http://paste.ubuntu.com/p/TkgFQdTf4M/)

---

### Post by oldfred on 2019-03-26
I do not see issue.
UUID's match in grub and your sdd1 partition.

I do not use os-prober anymore, but add my own entries to 40_custom. Grub updates are a whole lot faster as it does not have to scan all the drives & partitions.
I only have two drives or maybe a flash drive.
But back when I had more drives, sometimes grub would just stop searching for a drive as my flash drives & data drives made search too long (maybe?)

If you edit the grub.cfg in your ESP to the install in sdd1 does it work?
What brand motherboard? Some with Asmedia ports have issues if Asmedia port is used. 
Or do you have different settings in UEFI for AHCI for drives. Some allow groups of drives to have different settings.

This is more for a test. You probably will want to uncomment your sda & comment out your sdd.
Change /EFI/ubuntu/grub.cfg

      ```
 #search.fs_uuid dd8cb5d2-8f60-4611-a48b-0eec7d443e11 root hd0,gpt5 
search.fs_uuid f62ab73d-2974-4e72-9d3b-aefb99dba855 root hd3,gpt1
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg 


```

Just in case it does not boot, have live installer handy to edit it back immediately.
I also have an old small flash drive with rEFInd which booted my system when UEFI & grub got confused with too many updates & a grub issue with 19.04.

---

### Post by Quarkrad on 2019-03-27
I added those lines to grub.cfg and it made no difference - but things re the grub menu have changed.  Currently my grub screen on boot looks like:

[B]ubuntu
Advanced options for ubuntu
Windows Boot UEFI fbx64.efi
Windows Boot Manager (on /dev/sda2)
System setup[/B]

All these options are on my /dev/sda SSD

(I do not use Grub Customizer but I do have it installed.  According to GCustomizer the grub entries should look like the attached - there seems to be a mis-match here).

So .... at the moment, on my initial grub screen I do have an option to  boot to my new ubuntu/gnome installation that is on /dev/sdd1

---

### Post by oldfred on 2019-03-27
If you changed your EFI/ubuntu/grub.cfg it would boot into your new install, not your old install.
Since new install, old install would not automatically find it. Run this:
sudo update-grub

---

### Post by Quarkrad on 2019-03-27
I ran sudo update-grub and looked carefully at the terminal.  The process did find the new ubuntu installation on /dev/sdd and I expected to see that option when I next booted.  However, the grub screen presented to me was as per #14.  At this point I'm not sure why the entry is missing when I saw it listed when I ran update-grub.

---

### Post by Quarkrad on 2019-03-27
Something needs sorting out - please do not spend any time on this until I get back.  Thanks

---

### Post by oldfred on 2019-03-27
I do not really know Grub Customizer.
Users that want a gui to edit grub use it, but I think it is better to manually edit grub configurations. But it does require a bit of effort.
Grub Customizer replaces most of the grub configuration scripts in /etc/grub.d with its own scripts which then may be different that standard grub configuration issues.
The only way I know to undo Grub Customizer is a total reinstall of grub so the scripts get totally updated. But that can undo any other changes you have made to grub.

---

### Post by Dennis N on 2019-03-27
> **Quarkrad said:**
> I ran sudo update-grub and looked carefully at the terminal.  The process did find the new ubuntu installation on /dev/sdd and I expected to see that option when I next booted.  However, the grub screen presented to me was as per #14.  At this point I'm not sure why the entry is missing when I saw it listed when I ran update-grub. Very strange indeed. Should be Linux entries with "source: os-prober". What is "Windows Boot UEFI fbx64.efi" (from a custom script)? Just curious.

Your boot summary of post #12 shows the new OS in listing of /boot/grub/grub.cfg; that should be also be on the generated grub menu. But you have done things since that? Could you post a current boot summary reflecting the situation when you don't see the new install on sdd in the grub menu? The contents of the /boot/grub/grub.cfg file is on that summary. It would be helpful to see if the sdd install is included.

---

### Post by Quarkrad on 2019-03-29
oldfred/Dennis - I hate to do this but I have decided to close this activity.  For some reason I also had some very odd happenings with fstab that took a while to sort out. I would love to sort this out to the end but as this is my working machine it is causing me more grief having an inactive machine than the benefit of the additional os - I can use virtualbox to get round my problem but the additional os would have been better. Many thanks.

---

