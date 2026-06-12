---
title: "Super basic rsync help"
date: 2008-01-18
forum: General Help
---

### Post by leenwebb on 2008-01-18
Hi all,
I have messed up my own backups too many times, so I am turning to you for help!  I've read a bunch of rsync "tutorials" but really most of them are more like man pages and not really aimed at the simple user.   I'm hoping that to an rsync-guru, this is a crazy easy question that can be answered in no-time-flat.

Here's my story:
- I have a few places that I need to back up (/var/www, /home, and some random files).  I don't want to back up the whole system, just those folders and files. 
- I like the idea of having a full snapshot once a week, and incremental each day. Do I create a seperate dated folder for each backup?  This won't be cron-ned (the computer is on at totally random times), so I'm guessing that the easiest thing is to have two scripts ('daily' and 'weekly').
- Is there a way to have the last line of the script shutdown the computer?  That way, I can put in my backup drive, tell the script to run, and forget about it. 

So that's all I want:  weekly snapshots and daily increments (keeping a few weeks' worth of older backups around) of a smattering of random folders and files.  Help!

Thanks!
Eileen

---

### Post by beercz on 2008-01-18
[This]("http://rsnapshot.org") may be just what you are looking for.  Once it's configured, it works like a charm.

---

### Post by ajgreeny on 2008-01-18
Also look at **grsync** and **sbackup,** both in the repos.  Looks like **sbackup** might be the one for you.

---

### Post by leenwebb on 2008-01-18
Sbackup seemed like a great idea, until I tried to actually recover a file from it.  It did not go well, hence my ventures into the world of rsync. (I gather from the forums that I am not the only person who has been screwed when actually trying to get something out of sbackup.) 

I have grsync right now, but I have to run a bunch of seperate backups (for the different dirs I want backed up), plus I don't see any simple way to do 'full' vs 'incremental'.  

I'll look at rsnapshot, thanks!

---

### Post by netman4ttm on 2008-01-18
While rsync is a good choice for backup, I think you will be happier in the long run with Bacula. We are running Bacula on a FreeBSD system,6.3 release candidate  but we use it to back up everything from Win NT to XP and various Linux boxes (Ubuntu, RedHat and Mepis)

---

### Post by ajgreeny on 2008-01-18
I don't know if this is the reason for your problem with sbackup, but by default it puts the backup file(s) in /var/backup rather than a separate disk with user permissions.  Perhaps changing that to another destination in the config would help.  If I'm barking up a completely wrong tree, just ignore this.

---

### Post by leenwebb on 2008-01-19
I ended up setting up rsnapshot -- I'd prefer a little more GUI, but oh well.  I really like that it automatically handles different time intervals (daily, weekly, etc).  And it has a simple and graceful way of failing when I don't turn on the external backup drive.

(ajgreeny -- I'm not sure what went wrong with sbackup.  I had set it up to use a non-default location (not a separate drive, just a different place on the same drive), and it created lots of backups.  But when I went to recover, it pretended like it had done stuff, but no files ever appeared in my recovery dir.  Hmmph.  )

That's another reason I moved to rsync -- the files are just there, in a normal format that I can use without any special program.

Thanks for everyone's advice!

---

### Post by beercz on 2008-01-22
You're welcome :-)

Hope you are getting on with rsnapshot OK.

I use it to make secure and efficient backups across the internet from remote offices to head office.

I also backup my office pc on my home server using rsnapshot, as well as backing up all my home machines onto my home server.

I have written small scripts that calls rsnapshot using the -c argument to call up the relevant configuration file (I have different configuration files depending on what is backed up) and have placed them in root's crontab file.  The scripts write the output of the backup to log files.  (I set my rsync_short_args value to  '-avv' (2 x letter v) in rsnapshot's configuration file)

I have also set up relevant ssh keys and then run the backups every night.  Next morning I check the logs.

One final thing, I have my servers "pulling" the data from the client machines, rather than the other way round (i.e. having the client machines "pushing" the data to the service machine.  I think it is more secure and the server remains in control.

---

