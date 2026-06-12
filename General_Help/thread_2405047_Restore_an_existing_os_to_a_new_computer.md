---
title: "Restore an existing o/s to a new computer ?"
date: 2018-10-31
forum: General Help
---

### Post by ra7411 on 2018-10-31
This is probably a dumb question, but...

At times of the year, we get a lot of lightening around here, and it's possible that I could get my desktop system fried.

I use qt5fsarchiver to backup my o/s and the size of the backup would be easy to put on a usb thumb drive which would be unaffected unless the whole house burned down and the usb drive was burned up,  instead of just the electrical system damaged, 

A new desktop computer would be a couple years newer with a different mobo, cpu, ram, etc. So, restoring the old computer's o/s to the new one would not work, right?

Thanks

---

### Post by oldfred on 2018-10-31
With Ubuntu maybe, Windows no.

But I believe in backing up user data like /home, maybe some settings in /etc and list of installed apps.
Then I can easily do a new install, and restore my data and applications.

       discussion of alternatives/strategy backups
[https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224](https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224)
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery) 
    
An image backup is obsolete as soon as you start using system again. And users often do not create them regularly.
But using rsync or rdiff  is something you can automate if server or drive is mounted or easily run if you plug in flash drive.
       If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)
Best practice for Backups - theFu
[https://ubuntuforums.org/showthread.php?t=2368992](https://ubuntuforums.org/showthread.php?t=2368992)
[https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986)
More backup info from 1clue
[https://ubuntuforums.org/showthread.php?t=2377810](https://ubuntuforums.org/showthread.php?t=2377810)

---

### Post by Autodave on 2018-10-31
More than likely, it will work.  However, if you have installed a video card driver and the replacement machine has a different GPU manufacturer, you could have a problem.  Could.

I have at least 2 HDs ready to go if needed.  I have installed Ubuntu on them and removed them from the machine. I have often stuck one of them into a machine (Windows) that is inop just to see if something other than Windose is the problem. To date, I have never had an issue booting into any of them and having an operable system instantly. So, your backup will most likely work.

---

### Post by ra7411 on 2018-10-31
Backup /home - absolutely.
That I have that on a 2tb HD in a usb housing which is detached from the machine except when backing up.  /home won't care about a different machine, new or old o/s.

As to o/s, I had previously assumed a new install required on a new machine,  w/ all the associated bother.  It's very useful to know that there's a good chance that a restore might work.

Now I feel like buying a new machine just for the hell of it.

---

### Post by C.S.Cameron on 2018-10-31
If you are happy using the same version of Ubuntu, you can clone the old drive to new or just reuse the old HDD.
Disable any proprietary drivers first, (ie Nvidia graphics).
If you want to upgrade your version of Ubuntu, you can copy your old home directory using rsync or Grsync.
Any downloaded programs will need to be reinstalled.

---

### Post by HermanAB on 2018-11-01
It takes about 20 minutes to install the latest and greatest version of Linux from scratch on a new computer.

So backup your data.  Don't waste your time and storage space by backing up an old and tired system.  When things go south, install afresh and be happy with your new computer running a new OS.

---

### Post by oldfred on 2018-11-01
Also if old computer is BIOS and new computer is UEFI, you probably can still use it, but will not have the newer UEFI with gpt partitioning.

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by ra7411 on 2018-11-02
>It takes about 20 minutes to install the latest and greatest version of Linux from scratch on a new computer.?<

Ub o/s is quick to install.
It's the 20+ apps I use that take time to install and re-preference.

---

### Post by oldfred on 2018-11-02
All your user settings should be in /home.

And you can export list of installed apps and easily reinstall them.

 My backup includes this also. The dpkg list is a very long text list of all applications and the dependencies. 
If upgrading, you may want to edit it to remove obsolete, old kernels or others. It will not re-install anything already installed.
[https://help.ubuntu.com/community/ReinstallingSamePackages](https://help.ubuntu.com/community/ReinstallingSamePackages)
from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade
#IF you get this error:
dpkg: warning: package not in database
sudo apt-get install dselect
sudo dselect 
   -> Update
   -> Install

---

