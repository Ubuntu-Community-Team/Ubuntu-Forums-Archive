---
title: "Scheduled Backup Feature"
date: 2021-05-23
forum: General Help
---

### Post by aw1182 on 2021-05-23
I noticed about a month or so ago that there is a schedule back up  feature on ubuntu.  I recall looking through the OS and this forum on  whether or not there was a back up option within the OS and found that  there was none.  The question I have is that is this a new feature that  was included in a recent update or was it already there and I just  missed it?

---

### Post by deadflowr on 2021-05-23
> I recall looking through the OS and this forum on whether or not there was a back up option within the OS and found that there was none. 

The Backup program deja-dup has been default for a long time on the desktop version of Ubuntu, and scheduled backups have been for probably as long.
Though many users have, or will, forego the default backup program in favor of other options like luckybackup or some scripted variant using rsync.
More options are listed here: [https://help.ubuntu.com/community/BackupYourSystem]("https://help.ubuntu.com/community/BackupYourSystem")

---

### Post by aw1182 on 2021-05-23
Oh ok then I just missed it when I was originally looking for it a few months ago.  Thanks for the link and the reply.

---

### Post by TheFu on 2021-05-23
> **aw1182 said:**
> Oh ok then I just missed it when I was originally looking for it a few months ago.  Thanks for the link and the reply.

There must be 50 backup tools in the repos.  When choosing a backup tool, it is best to research common problems and restore options BEFORE deciding.

Each person has slightly different needs when it comes to backups. There are pros/cons for every tool.
One of the easiest to understand is called "back in time".  It uses rsync + hard links to make versioned backups while still being fast and storage efficient.  The liabilities are that it doesn't support non-Linux file systems for the backup storage and that it doesn't support network-based backups.   That means the backup target storage has to be shared either physically connected or through NFS/sshfs to work.  There is no "pulled" backups as a viable option.  For me, that's a huge liability since malware and crypto-ware can gain access to the backups and encrypt it. 

Duplicity, Deja Dup, Duplicati are all based on Duplicity.  On paper, these are amazing tools but there are issues commonly reported. Do some research about those problems before choosing any of these.

Almost anything can be scheduled on a Unix system. There's little need for that to be listed as a feature.  That way of thinking is from some-other-OS, I suspect.

---

### Post by aw1182 on 2021-05-23
Yes I'm using the backup program that was already installed in ubuntu (I  don't remember installing a backup program).  I'm assuming this is Deja  Dup.  I only use this computer for basic internet and for libreoffice  programs.  I only need to backup my ubuntu settings and my libreoffice  files.  Would Deja Dup be sufficient for this?

---

### Post by TheFu on 2021-05-23
> **aw1182 said:**
> Yes I'm using the backup program that was already installed in ubuntu (I  don't remember installing a backup program).  I'm assuming this is Deja  Dup.  I only use this computer for basic internet and for libreoffice  programs.  I only need to backup my ubuntu settings and my libreoffice  files.  Would Deja Dup be sufficient for this?

Have you tested the restore?  That's the only way to know for certain.

---

