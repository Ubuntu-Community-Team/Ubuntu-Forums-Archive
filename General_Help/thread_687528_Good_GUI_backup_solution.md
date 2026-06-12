---
title: "Good GUI backup solution?"
date: 2008-02-04
forum: General Help
---

### Post by prana on 2008-02-04
Anyone know of a good backup solution for Ubuntu?

Some features I am looking for:

1) A GUI front end
2) I should be able to get to backed up files without needing the backup software (i.e no binary format)
3) Can backup to a USB drive
4) If the USB drive is not connected, the solution should not freak out and should resume the next backup when the USB drive is connected.
5) Have the ability to do incremental backups
6) Incremental backups of binary files.

Thanks.

---

### Post by weaverryan on 2008-02-04
I use something called simple backup suite. It's actually sbackup in the repos, not simple-backup.

It's got a simple gui - allowing to include and exclude files. It does a few different things to backup files, but the result is a folder, filled with a few files of information, and one big zip file of the files that were actually backed up. So, you can obviously get to your files without the actual binary.

I use this to backup to my networked hard drives. When they're not connected, the backup doesn't happen - but the process has always been 100% transparent - I get no complaints of any kind from the software. It simply backs up if the drive is available, doesn't otherwise.

It also does backups incrementally. I can't confirm that it does with this binaries, but as it's hit on every one of your demands so far, I'd check it out.

sudo apt-get install sbackup

---

### Post by prana on 2008-02-04
Thanks I will check it out.

---

