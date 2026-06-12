---
title: "Boot loop error msg"
date: 2019-09-09
forum: General Help
---

### Post by Godspell on 2019-09-09
I honestly don't know what happened. Randomly, I see this msg when I switched on the laptop and it seems to be in a boot loop now.

```
UBUNTU clean, 328311/30883840 files, 13460401/123516160
```

I'm on Ubuntu 18.04 and it's a laptop with 16GB RAM and an SSD. I'm not sure what else to say, frankly I'm completely dumb struck..

What can I do to fix this??

Thanks in advanced.

---

### Post by oldfred on 2019-09-09
Ubuntu used to run fsck on every 40 or 60 reboots. 
I believe with ext4 and its journal, it says whether it needs fsck.
So it just is saying you do not need fsck (which usually is ok, but sometimes, you may still need it.).

What brand/model system?
What video card/chip?
Can you boot recovery mode, second entry in grub menu. 
If only Ubuntu and no grub menu by default, use Escape key right after UEFI/BIOS screen if UEFI. And if BIOS install press & hold shift key until grub menu appears.

       May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by Godspell on 2019-09-09
Thanks for the reply. It's Dell XPS 13 and it's quite new. No external GPU, just Intel UHD 620.
Ubuntu is the only OS on it so no recovery option but I can press ESC and that takes me to a blank screen with just ```
grub:
``` 

The OS copy is Dell OEM Ubuntu image. I believe I can get it from their website. Haven't been on Ubuntu for a while so I don't know off the top of my head how to do recovery...
I'll have a read at the links you provided.

It's just extremely frustrating this has happened...I wasn't messing about with anything. I was just using it for generic day-to-day tasks.

---

### Post by oldfred on 2019-09-09
I know Dell has some unique settings in grub to reload system.
Seen one or two users who had 16.04 and did an upgrade to 18.04 and had issues. Not sure if resolved or not.

You should be able to download (if you have access to another system) the standard Ubuntu ISO and create a live installer and run Boot-Repair from that.
       Also link on how to create a  bootable DVD or USB flash drive, using Windows or Ubuntu, Min hardware requirements
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) 
    

Not sure if any of this will help or not.
       Dell XPS 13 What to fix with the fresh factory Ubuntu 16.04 April 2017 Updated to 18.04
[https://ubuntuforums.org/showthread.php?t=2357424](https://ubuntuforums.org/showthread.php?t=2357424)
Dell update UEFI/BIOS from Linux
[https://www.dell.com/support/article/us/en/19/sln171755/updating-the-dell-bios-in-linux-and-ubuntu-environments?lang=en](https://www.dell.com/support/article/us/en/19/sln171755/updating-the-dell-bios-in-linux-and-ubuntu-environments?lang=en)
Dell support - Update on XPS 13/15 2016 Developer Edition availability
[http://en.community.dell.com/techcenter/os-applications/f/4613/t/19670562?pi22229=9](http://en.community.dell.com/techcenter/os-applications/f/4613/t/19670562?pi22229=9)
[http://www.dell.com/support/article/ca/en/cabsdt1/SLN301754/en](http://www.dell.com/support/article/ca/en/cabsdt1/SLN301754/en)

---

### Post by Godspell on 2019-09-10
> **oldfred said:**
> I know Dell has some unique settings in grub to reload system.
Seen one or two users who had 16.04 and did an upgrade to 18.04 and had issues. Not sure if resolved or not.

You should be able to download (if you have access to another system) the standard Ubuntu ISO and create a live installer and run Boot-Repair from that.
       Also link on how to create a  bootable DVD or USB flash drive, using Windows or Ubuntu, Min hardware requirements
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) 
    

Not sure if any of this will help or not.
       Dell XPS 13 What to fix with the fresh factory Ubuntu 16.04 April 2017 Updated to 18.04
[https://ubuntuforums.org/showthread.php?t=2357424](https://ubuntuforums.org/showthread.php?t=2357424)
Dell update UEFI/BIOS from Linux
[https://www.dell.com/support/article/us/en/19/sln171755/updating-the-dell-bios-in-linux-and-ubuntu-environments?lang=en](https://www.dell.com/support/article/us/en/19/sln171755/updating-the-dell-bios-in-linux-and-ubuntu-environments?lang=en)
Dell support - Update on XPS 13/15 2016 Developer Edition availability
[http://en.community.dell.com/techcenter/os-applications/f/4613/t/19670562?pi22229=9](http://en.community.dell.com/techcenter/os-applications/f/4613/t/19670562?pi22229=9)
[http://www.dell.com/support/article/ca/en/cabsdt1/SLN301754/en](http://www.dell.com/support/article/ca/en/cabsdt1/SLN301754/en)

Thank you. I've managed to restore it to factory setting through Dell's own recovery system (on factory-created recovery partition). Very sensitive though, had to press Esc exactly twice after seeing the Dell logo at bootup. The lettering is extremely small on a 4k screen but I was able to pick out the recovery option from the Grub menu and follow it through. Then, I restored the backup from GDrive and that seems to have done the trick.

**Question:** is there anyway I can create a backup image of my current setup? The idea behind this is if this sort of thing happens again, I can just dump the whole image (snapshot?) on the SSD and thus, effetively restoring it to the last working condition..if that makes sensee. I think this'll be a sensible approach.

---

### Post by oldfred on 2019-09-10
I am more of a fan of the way you restored system. Reinstall & restore all settings from backups.

Image backups are old as soon as you start using system.

       discussion of alternatives/strategy backups
[https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224](https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224)
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery)
[http://ubuntuforums.org/showthread.php?t=2236636](http://ubuntuforums.org/showthread.php?t=2236636)
[URL="http://askubuntu.com/questions/2596/comparison-of-backup-tools"]http://askubuntu.com/questions/2596/comparison-of-backup-tools

      [/URL]
 **Full image backups**
[http://clonezilla.org/](http://clonezilla.org/)
[https://www.ostechnix.com/systemback-restore-ubuntu-desktop-and-server-to-previous-state/](https://www.ostechnix.com/systemback-restore-ubuntu-desktop-and-server-to-previous-state/)
fsarchiver
[http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page) 
[http://www.fsarchiver.org/QuickStart](http://www.fsarchiver.org/QuickStart)
Free Imaging software - CloneZilla & PartImage - Tutorial 
[http://www.dedoimedo.com/computers/free_imaging_software.html](http://www.dedoimedo.com/computers/free_imaging_software.html)
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/) 
    [URL="http://askubuntu.com/questions/2596/comparison-of-backup-tools"]
[/URL]

---

### Post by Godspell on 2019-10-17
I actually meant to ask you but completely forgot...

Suppose all things went kaput, I will be able to restore everything with this method _except_ for the boot partition, right? 

So, what's the best way to back up and restore it?

Thank you.

---

### Post by oldfred on 2019-10-17
Grub is easy to install from live installer or using Boot-Repair.
With UEFI and new drive, you just about have to reinstall grub or use efibootmgr to add UEFI boot entry.

With UEFI I do also backup ESP - efi system partition, but never have needed it. I have reinstalled grub.
I also have two drives and multiple installs of Ubuntu on each drive. And an ESP on each drive as well as a few full installs on flash drives.
My main working install is 18.04, but I still have my 16.04, and on one system my 14.04 install.  And typically install each new version when it comes out, just to see differences. But that also gives me multiple ways to boot.

---

### Post by Godspell on 2019-10-18
Thanks for the reply.

Okay, my current situation is this;
I need to have the full disk encryption enabled for my device i.e. XPS 13 Ubuntu (no other OS) and from what I've read, it has to be done during the setup or else it's virtually impossible to implement.

So I need to reinstall the OS (using Dell Ubuntu image) and restore all config, apps, personalisations, etc. Hence why I was asking about the image backup before :)
But from what we've discussed, I don't think there'll be any complications -- the drive will be wiped, partitioned, encryption set and OS installed. Then, restore apps and configs..I think that about covers it.

---

