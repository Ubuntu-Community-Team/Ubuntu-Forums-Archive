---
title: "Rsync Setup"
date: 2013-03-11
forum: General Help
---

### Post by maddtechwf on 2013-03-11
I've new to Xubuntu and I'm trying to figure out how to write a complex setting of Rsync or Rdiff-Backup.

I need to write a backup that take what's on my remote server and back it up to a specific folder on my computer.  I would also like to run a backup of mysql this way too if possible.  It would be nice to keep like the last 5 backups and no more.

I would like to automate this if possible.

---

### Post by SeijiSensei on 2013-03-11
For MySQL, I posted a [script]("http://ubuntuforums.org/showthread.php?t=1580676&p=9882114&viewfull=1#post9882114") here that does what you ask.

For rsync, a simple beginning would be:

```

cd /path/to/the/backup/folder
rsync -av remote_server:/path/to/something .

```

Take a look at the --include-from and --exclude-from [options for rsync]("http://linux.die.net/man/1/rsync") to specify multiple directories to include or exclude from the transfer.

---

### Post by papibe on 2013-03-11
Hi maddtechwf. Welcome to the forums ):P

Let me start by noting that rsync is not a comprehensive backup solution. Granted, it is a powerful tool, and it is used by a lot of backup software in the background.

For copy/mirror it is fantastic, and very easy to implement.

When you start thinking on as schedule the includes full, incremental and differential backups, an rsync command won't be enough. Don't get me wrong. You could, indeed, write some scripts that take care of all that (take a look at [these]("http://rsync.samba.org/examples.html") examples). But scripts need to be tested, debugged, etc. Considering going this route would depend  on the urgency, importance of your data, and your scripting abilities.

I would start by taking a look at [this]("https://help.ubuntu.com/community/BackupYourSystem"), and [this]("http://askubuntu.com/questions/2596/comparison-of-backup-tools") reviews of several backup tools.

Having said that, here's a few pointers:

**rsync:**
For more complex backups, there are several approaches:
[LIST]
[*]for differential you can use the option --compare-dest (see [here]("http://unix.stackexchange.com/questions/25195/how-do-i-save-changed-files")).
[*]for incremental, you can use the combo --backup and --backup-dir (see [here]("http://rsync.samba.org/examples.html")), or use hardlinks (option -h) (see [here]("http://webgnuru.com/linux/rsync_incremental.php")).
[/LIST]
Here's another [guide]("http://www.jveweb.net/en/archives/2011/02/using-rsync-and-cron-to-automate-incremental-backups.html") for full and incremental backups using rsync.

**Automation:**
To automate tasks, take a look at [cron]("https://help.ubuntu.com/community/CronHowto").

**SQL:**
[LIST]
[*]You can't rsync a live database. You may have to stop it, copy it, and restart the database again.
[*]An alternative is create a dump of the database, and then rsync that.
[*]SQL have internal functionality for replication. You may take alternatives of that too.
[*]
[/LIST]
Hope it helps. Let us know how it goes.
Regards.

---

