---
title: "Backup/Synch Files...."
date: 2007-09-21
forum: General Help
---

### Post by AlanR8 on 2007-09-21
This is beginning to PI** me off, here's why.

What I want to do is back up my files to my network drive. Yes, I have it mounted, and Kbackup and Simple Backup work OK. BUT, as programs they're not what I'm looking for (I think). 

What I need is to be able to copy the files from desktop to network drive as is and not to compress. I also want to be able to do incremental backups, much quicker after the first full backup. In fact going back to my Doze days, the Synch Toy application is EXACTLY what I need. (Have tried to install under Crossover Linux and it won't work).

I'm running Kubuntu and by default the backup program "Keep" installs and appears to have what I need. But when I run it I get this HUGE error message, see attached screen shot. What does it mean?

The Kubuntu install is fresh, the network drive is mounted, other backup utilities work. What's going on?

---

### Post by rhodry on 2007-09-21
> **AlanR8 said:**
> This is beginning to PI** me off, here's why.

What I want to do is back up my files to my network drive. Yes, I have it mounted, and Kbackup and Simple Backup work OK. BUT, as programs they're not what I'm looking for (I think). 

What I need is to be able to copy the files from desktop to network drive as is and not to compress. I also want to be able to do incremental backups, much quicker after the first full backup. In fact going back to my Doze days, the Synch Toy application is EXACTLY what I need. (Have tried to install under Crossover Linux and it won't work).

I'm running Kubuntu and by default the backup program "Keep" installs and appears to have what I need. But when I run it I get this HUGE error message, see attached screen shot. What does it mean?

The Kubuntu install is fresh, the network drive is mounted, other backup utilities work. What's going on?

I detect a touch of frustration creeping through here? :) Deep breaths now.

You could try a program called rdiff-backup. Here is the link to its home page [http://www.nongnu.org/rdiff-backup/](http://www.nongnu.org/rdiff-backup/) 

It does incremental backups using rsync. It is cli based but not hard to learn.

You could also do a search in Synaptic Package Manager for "backup" to see just how many options you actually have in this area. Whilst there are lots of choices, you will simply have to learn and use some of them to decide for yourself your  preferred method.

Personally I wrote my own rsync bash scripts for daily (or one-off) backups of key data and once a fortnight I run SBackup to keep a system archive. Works a treat. I automate it all with cron.

Good luck,
Rhodry.

---

### Post by AlanR8 on 2007-09-21
Rhodry

Thanks for the reply. One other thing I forgot to mention is this backup strategy will be used by the wife. Need I say more!

Personally, I don't want to go to the command line. I like a GUI....I'm an X Doze user as indeed most of us are. I'm a year into my Linux experience and ain't going back. I've spent most of this afternoon fiddling with backup options (in between contracts at the moment) and yes a tad frustrated. One of the options I did explore was "backuppc" that gives a web based interface. BUT, I couldn't log on to the interface.

Anyone have any ideas about the error message I posted.....:(

---

### Post by AlanR8 on 2007-09-22
So.....

Has anyone else got any ideas why "Keep" is producing the error message in my original post? :confused:

---

### Post by rhodry on 2007-09-22
You have lots of options for backups. I have already given you a couple.

If you want your backup to be a copy of each file  without compression, then some form of the rsync command as the background tool would be my suggestion. There is a simple gui called "grsync". It is in the universe repository. It handles some simple rsync commands.

Or, you can learn about "bash scripts" and write your own script using rsync as the primary command.  You can make that as interactive as you like. You can then put an icon on the desktop as a custom launcher - so anyone can just double click the icon to start a backup. Better still, put the script in cron for automatic execution. There are heaps of rsync sample scripts around. Do a search in these forums or Google, etc.

"Keep" is a KDE app is it not? If so, maybe nobody in these forums uses it and hence no answer to your question. You could try asking in the Kubuntu forums:

[http://kubuntuforums.net/](http://kubuntuforums.net/)

Rhodry.

---

### Post by AlanR8 on 2007-09-23
Thanks  for you replies rhody, very useful.

I've downloaded grsynch as suggested and can work with that for the time being. You're right, "Keep" is a KDE program so I'll go to the relevant forum although I do most of my research and learning in these forums!

---

