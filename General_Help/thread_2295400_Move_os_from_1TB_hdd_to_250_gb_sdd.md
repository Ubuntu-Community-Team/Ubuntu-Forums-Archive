---
title: "Move os from 1TB hdd to 250 gb sdd"
date: 2015-09-18
forum: General Help
---

### Post by AADAS on 2015-09-18
I have ssd and hdd ot my laptop and I want to move the os form the hdd to the os.But I want to keep all installed programs and configuration.

---

### Post by sotiris2 on 2015-09-18
How much the used space in the hd partition? How much is it if you subtract the size of your home folder from it?

---

### Post by AADAS on 2015-09-18
How much the used space in the hd partition? 
About 750GB
How much is it if you subtract the size of your home folder from it?
about 400gb

---

### Post by oldfred on 2015-09-18
That does not sound right.
My SSD has a 25GB / (root) partition for my main working install. And I have all data & other test installs on HDD.

I prefer a new clean install. 
Is system UEFI with gpt partitions or BIOS with MBR(msdos) partitions?

With a new install you avoid issues of duplicate UUIDs and conflicts. 
You can export a list of installed applications and easily reinstall. You should be normally backing up /home and the list of applications so when (not if) system fails you can easily restore it. Hard drives have become more reliable, but still fail or get totally corrupted and new install and restore from backups is often the quickest & easiest way.

       discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery)
[http://ubuntuforums.org/showthread.php?t=2236636](http://ubuntuforums.org/showthread.php?t=2236636)
[http://askubuntu.com/questions/2596/comparison-of-backup-tools](http://askubuntu.com/questions/2596/comparison-of-backup-tools)
If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)

Many that image system use clonezilla, but it is more for restore to same drive. You do have to make sure system is smaller than SSD.

---

