---
title: "Automatic backups without cron?"
date: 2008-01-03
forum: General Help
---

### Post by dtreichler on 2008-01-03
I recently picked up an external drive to backup irreplaceable files (documents, photos, etc.) and I'd like to setup some sort of automated system that I can basically forget about once it's going.  I've considered using rsync and cron but the computer isn't really on at predictable times (and I don't like to leave it on all the time) and I'd hate for it to miss backups because it's been off at a certain time of day for a few days.  I guess I'm almost imagining something similar to a RAID 1 where if a file changes in the primary location, it's changed simultaneously in the backup location.  I'm not looking to mirror a whole drive, just a few folders here and there. Any suggestions?

---

### Post by sancho panza on 2008-01-03
Sbackup is an option, but I doubt if its the best option for just syncing files. I suspect that you can setup cron to be flexible about the backup times too.

---

### Post by pointone on 2008-01-03
A simple rsync script that runs at shutdown, perhaps?

---

### Post by dtreichler on 2008-01-03
> **sancho panza said:**
> I suspect that you can setup cron to be flexible about the backup times too.

I'm not familiar enough with cron to know how to go about doing something of that nature.  Any hints/tips/places to look?

> **pointone said:**
> A simple rsync script that runs at shutdown, perhaps?

That's not a bad idea actually.  If all else fails, I think that'll work.  If I'm walking away from the machine, I guess it doesn't really matter if the shutdown time is a little longer.  Is there a way to flag a process run at shutdown so that it is excluded if the machine is being restarted?

Another thought that just occurred to me is to maybe do a mix of a shutdown script and cron... Set up a script that runs at shutdown and set up a cron job that runs in the middle of the night should the machine be left on for whatever reason.

---

### Post by pointone on 2008-01-03
Simply create links to your script in the /etc/rc0.d directory, ideally with a low sequence number (i.e., before the system unmounts your filesystems). This can be done manually or using the update-rc.d command (recommended). Check the update-rc.d manpage for more information.

---

### Post by -Zeus- on 2008-01-03
Put the file you want run in /etc/init.d and run this command

```
sudo update-rc.d /etc/init.d/<file> start 0 stop 123456
```

That should run it only on halt

---

### Post by dtreichler on 2008-01-03
Thanks sancho panza, pointone and zeus... I think this will work well.

---

### Post by sancho panza on 2008-01-04
> **dtreichler said:**
> I'm not familiar enough with cron to know how to go about doing something of that nature.  Any hints/tips/places to look?


Look under the "time" tab of Sbackup. It lets you schedule  a backup at a specific time, or at any time within a given frame, using some cron definition files. I dont know any more about it. Sbackup does incremental backup, not a synchronization, so it probably isnt the best choice for you, though.

---

### Post by measekite on 2008-01-04
> **dtreichler said:**
> I'm not familiar enough with cron to know how to go about doing something of that nature.  Any hints/tips/places to look?



That's not a bad idea actually.  If all else fails, I think that'll work.  If I'm walking away from the machine, I guess it doesn't really matter if the shutdown time is a little longer.  Is there a way to flag a process run at shutdown so that it is excluded if the machine is being restarted?

Another thought that just occurred to me is to maybe do a mix of a shutdown script and cron... Set up a script that runs at shutdown and set up a cron job that runs in the middle of the night should the machine be left on for whatever reason.

[COLOR=Red]**What is needed is a Cron GUI.**[/COLOR]

1.  SBackup
Does not tell you what is being backed up and the progress made.  Seems to go on forever.  You cannot have multiple backup sets.

2. GRsync
Does provide progress.  Seems to be more finite and does Support Multiple backupsets that you can name and schedule individually.

The Problem with using GRsync is it does not have a scheduler and I really do not know Cron.  Is there a GUI for Cron like there is for Rsync that will allow you to schedule multiple backup sets.  A backup set is a particular folder or drive that you can name.

Unfortunately you cannot have a backup set consisting of a bunch of different folders on one or more drives that are not nested within a parent folder.

More ideal would be a backup utility that will allow all of the above and snapshots as well that would be similar to Retrospect that runs under apple and windows.They have not intention of supporting Linux.

Any suggestions out there.

---

### Post by Bushwack on 2008-01-04
backuppc may be a little overkill for your needs, but it's pretty easy to setup and it's included in the repositories.

---

### Post by sancho panza on 2008-01-05
I guess [this is the GUI]("http://gnome-schedule.sourceforge.net/") for cron.

---

### Post by schmickers on 2008-01-27
> **-Zeus- said:**
> Put the file you want run in /etc/init.d and run this command

```
sudo update-rc.d /etc/init.d/<file> start 0 stop 123456
```

That should run it only on halt

I am having trouble with this command. I am using 7.10.

When I try it on a script I have placed in /etc/init.d, I get:
```
update-rc.d: /etc/init.d//etc/init.d/clamshutdown.sh: file does not exist
```

When I omit the path to the file, and just the file itself, for instance:

```
sudo update-rc.d clamshutdown.sh start 0 stop 123456

```

... I get:

```

update-rc.d: error: expected runlevel [0-9S] (did you forget "." ?)

```

Not sure what's going on. Anyone have any ideas?

---

