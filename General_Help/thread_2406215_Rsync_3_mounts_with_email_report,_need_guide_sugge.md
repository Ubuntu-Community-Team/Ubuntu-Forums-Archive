---
title: "Rsync 3 mounts with email report, need guide suggestions"
date: 2018-11-17
forum: General Help
---

### Post by maxburn on 2018-11-17
I would like to have a Ubuntu 18.04 headless VM do an rsync between mounted shares. My problem is mainly there are too many search results and I'm not sure how to choose. I'm still fairly new to linux but I find I can generally get things done if I'm following a GOOD guide; please give me suggestions to follow, thank you!

Project goals
-Two backup jobs with two different schedules
-Want detailed email results of what happened

Main mount is SMB share on FreeNAS
Backup mount is SMB share also on a FreeNAS, send the contents of Main to this every week.
Remote mount is SMB share over a VPN to remote Synolgoy, send the contents of Main to this nightly.

---

### Post by TheFu on 2018-11-19
Using SMB for backups is problematic.  It will drop user, group and important file permissions - SMB just doesn't support those well. Those are necessary to have any hope of a restore that actually works.

SMB is commonly attacked by crypto-malware. If the storage is mounted, the crypto-malware will encrypt all the backed up data, making those backups useless.

Using straight rsync for backups is also problematic assuming you backup to Unix file systems without SMB/CIFS getting in the middle.  File ownership, groups, and permissions changes are lost over time.  To capture those changes as part of the backup requires using a real backup tool or manually capturing that data with the data part of the backups.

I would be worried about having primary and backup on the same physical system too.  But if you can ensure separate physical disks are used and you've proven the restore from them is possible should FreeNAS OS be unavailable, great.  I wouldn't assume that to be true, especially for someone new to Unix systems.  Is your FreeNAS backup disk(s) using UFS or ZFS?

Using a non-mounted backup storage tool can address those issues easily.  Most Unix backup tools are based on librsync, so performing backups without actually having a mount is trivial.  Just setup ssh connectivity between the systems and it will work.  Actually, I'd strongly recommend using "pull" backups, not "push" backups.  This way, the client being backed up cannot access the backup storage at all directly, so any crypto-malware a client might have cannot corrupt the backups.

As for backup tools, I use **rdiff-backup**, but many people like to use **duplicity** because it checks all the backup "best practice" lists.  When picking a backup tool, it is recommended to do a few tiny tests using the /etc/ directory.  /etc/ needs to be included in any system-level backups and it is both tiny and has some special types of files that are owned by different userids, so if those are handled correctly, versioned, then the backup of any other locations on the system will almost always work perfectly too.  In your testing, modify a few files between each test, so you see the different backup versions capture those changes as expected.

As for schedules - that is trivial using cron. Output created by any cron job is automatically emailed to the local userid under which the cronjob ran.  You can forward that output using the /etc/aliases file which is honored by all MTA programs.

As for detailed emailed results, that is dependent on you setting up your MTA on the backup system and capturing the level of detail as the job runs.  Depending on your SMTP-fu (skills), that might be the harder part of this.  Capturing output for logging of any shell command is trivial.   Use the 'tee' command as an output filter.

[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is a general knowledge guide for Linux.  At the shell, linux is linux is linux about 98% of the time. It is only the package management and some locations for system configurations that are different between the different major flavors.

BTW, using a 2-stage backup with local --> local ---> remote is a great idea.  The local --> local needs to use a good solid backup tool, but the local --> remote part can easily use rsync, since the local backup will contain the owner/group/permissions inside metadata each backup tool retains, at least for the 2 tools I list.

I've made many assumptions about the sort of data you are backing up.  If it is only data for 1 userid, then the file permissions aren't nearly as critical.  But if it is for multiple userids or for the OS files, then that extra metadata is absolutely critical to restore a system that will actually work.

Clear as mud?

---

### Post by maxburn on 2018-11-19
First off thank you for your response! Starting at the end;

> **TheFu said:**
> I've made many assumptions about the sort of data  you are backing up.  If it is only data for 1 userid, then the file  permissions aren't nearly as critical.  But if it is for multiple  userids or for the OS files, then that extra metadata is absolutely  critical to restore a system that will actually work.

Clear as mud?

This is just a personal file dump for me (and no one else), bunch of video files and things saved that I don't want cluttering up my workstations etc. There is a video player and a couple other misc things accessing the main share but really it's just the one user id that has read/write privileges to everything. Original plan was to have a read only user ID for the video player but I haven't implemented it yet. 

> **TheFu said:**
> I would be worried about having primary and backup on the same physical  system too.  But if you can ensure separate physical disks are used and  you've proven the restore from them is possible should FreeNAS OS be  unavailable, great.  I wouldn't assume that to be true, especially for  someone new to Unix systems.  Is your FreeNAS backup disk(s) using UFS  or ZFS?
~
BTW, using a 2-stage backup with local --> local ---> remote is a  great idea.  The local --> local needs to use a good solid backup  tool, but the local --> remote part can easily use rsync, since the  local backup will contain the owner/group/permissions inside metadata  each backup tool retains, at least for the 2 tools I list.

The primary and one of the three backups would be on the same system, yes. Separate disk arrays etc. There's also the remote site over VPN backup and the offline backup. The offline backup is accomplished via robocopy on a windows workstation to an external drive that sits on a shelf powered off; this is my protection against crypto malware.

> **TheFu said:**
> SMB is commonly attacked by crypto-malware. If the storage is mounted,  the crypto-malware will encrypt all the backed up data, making those  backups useless.

I was NOT happy when I found that the android app foldersync only supported SMB1 with all it's vulnerabilities. I'm going to search for something more up to date as that's the only thing using SMB1, once that's gone I will only have SMB2/SMB3 left. 

> **TheFu said:**
> Using a non-mounted backup storage tool can address those issues easily.  Most Unix backup tools are based on librsync, so performing backups without actually having a mount is trivial.  Just setup ssh connectivity between the systems and it will work.  Actually, I'd strongly recommend using "pull" backups, not "push" backups.  This way, the client being backed up cannot access the backup storage at all directly, so any crypto-malware a client might have cannot corrupt the backups.

That sounds like a good idea too. 

> **TheFu said:**
> As for backup tools, I use **rdiff-backup** but many people like to use **duplicity** because it checks all the backup "best practice" lists. 

Thank you, I will start looking into these. 

> **TheFu said:**
> As for schedules - that is trivial using cron. Output created by any cron job is automatically emailed to the local userid under which the cronjob ran.  You can forward that output using the /etc/aliases file which is honored by all MTA programs.

As for detailed emailed results, that is dependent on you setting up your MTA on the backup system and capturing the level of detail as the job runs.  Depending on your SMTP-fu (skills), that might be the harder part of this.  Capturing output for logging of any shell command is trivial.   Use the 'tee' command as an output filter.

[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is a general knowledge guide for Linux.  At the shell, linux is linux is linux about 98% of the time. It is only the package management and some locations for system configurations that are different between the different major flavors.

This is probably the area I'm least skilled in, never set up a cron job before.

---

### Post by SeijiSensei on 2018-11-19
One alternative is to use the "tar" command to create an archive from the files on the SMB share, then copy that "tarball" to the backup device.

---

### Post by maxburn on 2018-11-21
> **SeijiSensei said:**
> One alternative is to use the "tar" command to create an archive from the files on the SMB share, then copy that "tarball" to the backup device.

I think the trouble with this is I don't have that kind of room available to do a temp file that big anywhere really. I could possibly zip/tar that straight to the backup device though so maybe. I've never really dealt with updating archives with changes though, I assume that can be done.

---

### Post by TheFu on 2018-11-21
tar really shouldn't be used for anything larger than 500MB.  It was designed when 50MB was HUGE!
Tar appends any updates.  It was designed for tapes.  That is both a good and terrible aspect to the tool.

tar is fine for moving project files around, so it does still have many uses. Backups just isn't one of them, IMHO.

---

