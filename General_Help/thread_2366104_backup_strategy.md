---
title: "backup strategy"
date: 2017-07-14
forum: General Help
---

### Post by edher67 on 2017-07-14
Hi, I’m looking for some backup strategies for my laptop.
 
 
 Talking to a friend, she is in love with “Time Machine” (MacOS) and looking around I found some Linux alternatives but I’m not sure this is the best approach because for what I understand this projects create recovery data inside the same HDD so if I lose my laptop I lose my data.
 
 
 At the moment, my first “backup” layer is cloud (Mega), and  every other day I just copy some files in to an external HDD. What I’m really looking for is a solution, either an application or a script, that allows me to synchronize certain folders with the external HDD, so I would just plug the HDD, run the “solution” and move on.

 
 
 Also, if you guys have a better/different backup strategy I would love to hear it.
 
 
 Thanks.

---

### Post by mastablasta on 2017-07-14
you dont' want to just synchronise, because if you have errors in file they will sync as well. what you actually want is versioned backups. it also depends if data changes often or if it is static.

anyway there is plenty of GUI tools for what you need in Linux as well as scripts and terminal based tools. there shoul dbe one in Ubutnu already i believe.
Have a look at:

Areca
Luckybackup
Duplicity
Duplicati
DejaDup
Backintime
Create Synchronicity 


rdiff-backup
rysnc (propperly setup) - can use grsync instead

[https://en.wikipedia.org/wiki/List_of_backup_software](https://en.wikipedia.org/wiki/List_of_backup_software)

personally i use Areca since it works on Linux and Windows and it is quite easy to setup the way i want it.
Luckybackup and Duplicati are also good.

---

### Post by speartip on 2017-07-14
+1 For Areca. Tried others but keep coming back to this. A bit of a learning curve to start with, but documentation is fairly good.
[http://www.areca-backup.org](http://www.areca-backup.org)

---

### Post by TheFu on 2017-07-14
+1 to what mastablasta wrote.

I use rdiff-backup, but there are many, many, many others. Each has pros and cons and depends on what you want out of a backup.  Just your files and settings is very different than having a full system backup which can be restored (or recreated quickly) to the same point it was before the issue happened.

I'm not a fan of physically connecting storage directly to a system.  This is how Windows viruses can spread. Also via CIFS/SMB shares, so those should be avoided too.  It is just a matter of time before that becomes common on Linux/Unix systems too.  I prefer backup methods that use client/server methods and the backup "server" pulls the data. The client machines cannot push the data - that would violate the proper security for the backups.

If you just want a trivial GUI to backup what most end-users think they need, aptTik is probably it.
[http://ubuntuhandbook.org/index.php/2017/01/aptik-backup-ppa-installed-apps-users-data/](http://ubuntuhandbook.org/index.php/2017/01/aptik-backup-ppa-installed-apps-users-data/) has more details. It is better than nothing.

If you want something similar to what Apple provides, there's a tool called Back-In-Time.  It uses hardlinks and rsync to have multiple versions.  I used it on Mom's computer years ago. It isn't as efficient as rdiff-backup, at least not for my data, but it does have some slick ideas that are very cool.  As a backup set gets older, fewer and fewer are retained.  Do most people really need daily backups from 3 months ago?  Nope. But having a 3 month old and 4 month old backup DOES make perfect sense.  That's BackInTime's premise and I think it does make some sense.  1 backup is retained per year.  1 monthly backup is retained for the current year, etc.  I remember the tool didn't retain weekly backups or daily backups as long as I wanted.  Custom schedules and retention is probably  possible, it wasn't worth my time to figure that out.  And it was designed for end-user backups, not system-wide backups. At the time, it was a hassle to make system-wide backups, which must run as root.  It does have a pretty GUI.  Oh ... and for rsync or back-in-time to work, the target backup storage must be Linux formatted.  Not NTFS.  This is because the extra metadata for each file and directory weren't stored outside the target file system. As the file permissions or ownership changed over time, that data was lost.  On a Unix system, owners, groups, permissions, ACLs are critical to a backup tool.

If you want to recover a system after a HDD failure - you'll need more.

---

### Post by edher67 on 2017-07-19
Thank you for your answers, it took a while to reply because I was reading the documentation and doing some testing. At this point I believe Areca it's exactly what I was looking for.

> **mastablasta said:**
> you dont' want to just synchronise, because if you have errors in file they will sync as well. what you actually want is versioned backups. it also depends if data changes often or if it is static.


what you said about synchronize makes a lot of sense.


> **TheFu said:**
> 

I'm not a fan of physically connecting storage directly to a system.   This is how Windows viruses can spread. Also via CIFS/SMB shares, so  those should be avoided too.  It is just a matter of time before that  becomes common on Linux/Unix systems too.  I prefer backup methods that  use client/server methods and the backup "server" pulls the data. The  client machines cannot push the data - that would violate the proper  security for the backups.

Did you mean an actual server (a 24/7 dedicated computer)? For what a read around a lot of people prefer this as a back up solution, but at this moment I can't afford to have one, I do have an old laptop that i could re purpose  but the electric bill alone would be to much for me. Also, I know I could use a VPS like Digital Ocean but even $5 a month can, some times, be hard to find.


Once again, Thank you.

---

### Post by TheFu on 2017-07-19
> **edher67 said:**
> Did you mean an actual server (a 24/7 dedicated computer)? For what a read around a lot of people prefer this as a back up solution, but at this moment I can't afford to have one, I do have an old laptop that i could re purpose  but the electric bill alone would be to much for me. Also, I know I could use a VPS like Digital Ocean but even $5 a month can, some times, be hard to find.


The "server" only needs to be on when it is pulling backups.  The first backup would take long, has to copy everything, right?  But the next ones and all the next ones would be diffs and take just a few minutes depending on what data changed since the last backup.  Most of my daily backups take 2-3 minutes.  Every once in a while, if I've been really busy, maybe 7-10 minutes.

Can you have the "server" on for 10 minutes a backup?

I would never suggest using a VPS for a backup server for a home system.  Everything needs to be encrypted for a backup.  There is sensitive data you don't know about in there.  Just assume it contains all your online purchase data, banking data, and "secrets."  How many people have "nothing important" on their phones only to be mad when that private photo got leaked?

---

### Post by mastablasta on 2017-07-20
> **edher67 said:**
> 
Did you mean an actual server (a 24/7 dedicated computer)? For what a read around a lot of people prefer this as a back up solution, but at this moment I can't afford to have one, I do have an old laptop that i could re purpose  but the electric bill alone would be to much for me. Also, I know I could use a VPS like Digital Ocean but even $5 a month can, some times, be hard to find.

what is your planned solution then? 

if it is external drive, then you can add that to RaspberyPi which can be on all the time (consumes 1W or so on standby) and it won't cost much to buy it. you might even get away with RaspberryPi Zero which costs about 5$. another option is to get a networked drive. they are same as external drives only a little bit more expensive.

for some basic backup of relatively static data a USB drive will also do. propper backup program will just copy any differences. and if you didn't have any or much, then not much will be copied if anything at all. so drive doesn't get used as much and should last for a while. of course USB drive is then part of PC and not networked and separated.

---

### Post by TheFu on 2017-07-20
Raspberry Pi I/O - both network and disk are terrible.  Not suitable for a "backup server."

Cheap networked disks almost always come with CIFS/SMB enabled and don't support a Linux file system.  Running CIFS on a network is a liability thanks to the current group of malware that encrypts all networked storage it can find.

The same applies for any directly connected "backup" storage.  If a computer will automatically find the storage, then it can encrypt it.

These are some of the reasons why a client/server backup model is so important to me.  We've seen these issues a few times in the last few years.  We know how to avoid them - 
* client/server backups
* over the network
* automatic
* versioned
* with a server that "pulls" the backups.

THAT should be the end goal.  Of course, not everyone can start with a solution like that, so if there isn't any other choice, a directly connected USB disk, that is only connected during backups, would be the cheapest, least risky solution.  Be certain to use versioned backups and only have it connected DURING the time data is actually being written.  I would probably connect it, go take a shower, then disconnect it before leaving for the day.  The longer it is connected, the greater the risks.

Of course, the risks of not having versioned backups are 100x greater than being directly connected and doing backups that way.  Always try to estimate the risks for our mitigation strategies to avoid going overboard when it doesn't make sense.

A backup server makes perfect sense for me.  I have about 20 different computer OS installations here, between all the different devices, phones, tablets, routers, virtual machines, and real computers.  Trying to connect a USB disk to each of them, daily, to get a backup would be too hard.  Other people probably have different, more simple, environments.

---

