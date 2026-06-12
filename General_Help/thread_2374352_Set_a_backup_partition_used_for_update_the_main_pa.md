---
title: "Set a backup partition used for update the main partition"
date: 2017-10-15
forum: General Help
---

### Post by heureux2 on 2017-10-15
Hello guys,

Is it possibile that I set my harddisk to 2 partition, main partition and backup partition.
The ubuntu system is installed in the main partition, while a backup image made by dd command is put in the backup partition.
The ubuntu system will check if there is a backup image in the backup partition every time when system started. 
If yes, execute dd command to update the main partition vie backup image.

Could anyone give me some tips for solution?

Thanks.

---

### Post by oldfred on 2017-10-15
Often the reason for a backup is for when (not if) hard drive fails. Having backup on same drive then is not a backup.

       Best practice for Backups - theFu
[URL="https://ubuntuforums.org/showthread.php?t=2368992"]https://ubuntuforums.org/showthread.php?t=2368992
[/URL]
 If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup) 

With and dd and continuous mounted drive/partition you have to be careful not not have same UUID. Some users who have made that mistake have system randomly mount one or the other partition depending on which it saw.

And if drive is newer gpt, you should not use dd on a partition. May work on entire drive, but dd not recommended as a way to backup. GUID/gpt drives have unique data in partition table, backup partition table and each partition that must match. A dd partition copy gets that data out of sync and causes issues.

[URL="https://ubuntuforums.org/showthread.php?t=2368992"]
[/URL]

---

