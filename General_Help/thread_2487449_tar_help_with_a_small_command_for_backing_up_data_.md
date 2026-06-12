---
title: "tar help with a small command for backing up data using crontab"
date: 2023-06-05
forum: General Help
---

### Post by mason64 on 2023-06-05
I am looking to add a small command to a crontab but its not working 

The command is 

*/2 * * * *  tar -zcf /home/username/backups/daily/backupdaily_$(date +%Y-%m-%d_%T).tar.gz /home/username/source

set to backup every 2 minutes is just a test at the moment, once its working it be set to backup every day


the source data where all the data will be stored is in /home/username/source 

i want to backup the data to backups/daily

using the name backupdaily_DATE 

the above works when i run it manually but i get an error on the output    "   tar: Removing leading `/' from member names " but the data still backs up 

Would this be the reason why the crontab doesnt work because of the error on output? would that stop the cron job from running?

Sorry if this is a noob question am newish to all this 

Thanks
Dave

---

### Post by TheFu on 2023-06-05
Tar is a terrible backup tool.  There are easier, better, more efficient, choices.

only root can backup using absolute paths.  That's because only root can restore to absolute paths.  

```
*/2 * * * * **/usr/bin/tar -**zcf /home/username/backups/daily/backupdaily_$(date +%Y-%m-%d_%T).tar.gz /home/username/source
```

Would be a better method. Never trust the PATH for scripts and definitely not for cron. Always specify the full, absolute, path to any program used.
I think newer versions of CRON may set the HOME environment variable, but I've never trusted that and always use absolute paths for all programs, all inputs and all outputs.

The cron is working, BTW. It isn't an error, it is a warning.

Now, if you want a better, faster, more efficient method, there must be 20 better choices.  I use rdiff-backup.

BTW, backing up anything to the same physical storage device is a failure. Backups need to go to a different drive or somewhere on the network.  Also, having them as versioned means you don't have duplicates of things that haven't changed.  All my systems have 90 days of versioned backups, as the minimal. Some have 366 days of versioned backups.  It is surprising how little storage is actually used to create and maintain these.

For example, my desktop system takes 11.3 GB to restore all the data from Sunday night.  Going back to Mar 1, it uses just 15.7 GB to hold all those daily versioned backups.  Seems like a bargain to me.  **rdiff-backup** is also extremely fast for each version.  Takes a few seconds to a few minutes - the line needed depends on the number of files and how much change happened since the prior backup.  The most recent backup looks like a mirror. Older backups are reverse, differential, gzip files.   diff.gz  There are some liabilities with this - intermediate backups cannot be removed without corrupting all older backups.  OTOH, the greater efficiency makes up for that.

If daily versioned backups aren't sufficient, check out **back-in-time**.  This uses rsync+hardlinks to efficiently store versioned backups.  A backup is created every hour and over time, some of those backup sets are deleted.  Eventually, there is just 1 per month retained, but do we really need 30 daily backups from 9 months ago?  It is only for the most-recent 48 hours that hourly backups are retained.  Restoring is trivial, since each backup set looks like a clone of the source directory tree.  Just copy the files you need back ... or everything.  hardlink-based backups have some liabilities too.  They don't accurately retain permissions and ACLs and owner/group over time. Just the most recent values are retained.  This is seldom an issue, but if it is, it is a big issue.

Friends don't let friends use tar for backups.  Tar was designed when 250MB was considered huge. Using it for anything larger isn't a good idea. There are better, faster, more efficient, options.

---

### Post by TheFu on 2023-06-05
BTW, date has shorter formats that can be used.  $(/usr/bin/date "+%F") is what I usually use.  Always use the full path in scripts and automation, so you don't accidentally get the wrong binary program and break the script/command.  %F is just for daily stuff.  Use $(/usr/bin/date "+%F-%T") for this test.

---

### Post by mason64 on 2023-06-05
Thanks for such a quick reply and the fix for my issue. 

As for backing up to the same drive this is just a test I will be backing up to another drive on the Pi as soon as I knew the command was working properly with no errors! 

I will take the advice onboard and look at rdiff-backup right now as i want something that does what you have pretty much said for my backups. 

Will go youtube some videos on this.

Great help!! thank you

---

### Post by TheFu on 2023-06-05
**tar** and **back-in-time** don't do network backups.  **rdiff-backup** does.  Backups over the network should be "pull"ed, not pushed. No access to the backup storage should be possible from the client system.  Definitely don't enable CIFS or NFS between the backup client and server system.  Crypto-ware understand network storage, so as part of the protection against that, keep the backup storage areas unavailable to client systems.

[Https://ubuntuforums.org/showthread.php?t=2482517&p=14125329#post14125329](Https://ubuntuforums.org/showthread.php?t=2482517&p=14125329#post14125329) shows some short, minimal rdiff-backup commands for local, pushed and pulled backups. Hopefully, those are helpful.

---

### Post by mason64 on 2023-06-05
great help and some very good tips - you have just taken up this weeks evenings :) thank you and i will let you know if i get stuck or how well i geton. Thanks TheFu

---

### Post by TheFu on 2023-06-05
Don't just backup 1 directory.  Do a system backup, which isn't the entire system, just enough to put back what you need, reload settigns and programs should something bad happen.


Here's a minimal rdiff-backup command to do *local* backups.  Put this into root's crontab:
```
/usr/bin/rdiff-backup \
        --exclude-sockets --exclude-device-files --exclude-fifos \
        --include /usr/local --include /etc  --include /root  --include /home \
        --exclude '**'   /       /Backups/
```

Local backups have some issues, if you want to be protected against malware or cryptoware. Obviously, if the backup storage is locally mounted, then the malware has access too.  But, it is better than no backup at all.

[LIST]
[*]/usr/local/ is where non-packaged, manually installed, software belongs.  If you aren't using it for that, start. 
[*]/etc/ is where system-level settings are stored.  While restoring all the files inside there isn't a good idea, having access to the information is really helpful.
[*]/root/  ... I put important information about my systems under /root/ to help at restore time.  Things like the list of installed packages, installed snaps, 
partition table layouts, storage information, and current hardware.  These things get updates as part of my backup script, just before the real backup, using rdiff-backup, runs.  This way, I can see when seldom used hardware disappeared, if I don't notice it immediately.
[*]/home/ this is where all local user HOME directories are placed by default.  I generally exclude cache directories from my backups, but these exclusions aren't needed when first trying a new backup tool.  Backup scripts and methods become more complex as we learn more and optimize a little every month, year.  I actually exclude lots and lots of specific directory patterns, but throwing a 20 line exclude at you now would just be scary, so I avoid it.
[/LIST]
The last line in that command says to exclude any directories not specifically included.  That's a bit odd, but necessary to have 1 command for the entire system.  This helps with _data homogeneity_, which is critical for a good backup.  Some people don't understand how important that is until it is too late.

The / on the last line is the "source" in the official rdiff-backup command, but we've excluded everything, included only the directories we want, so it effectively is there just to make the command happy.
The /Backups  is the target location for backups.  I actually use a backup server and add the `hostname` below the backup directory location.
/Backups/hadar/  --- are for the system hostname 'hadar'
/Backups/regulus/ are for regulus.
You get the idea.  My backup disk was a 2TB USB external disk for many years.  Last fall, I swapped out that old drive for a new 4TB drive.  Almost all my backups are "pull" and write to the new storage today.  Not all because rdiff-backup v2 is incompatible with v1.x servers.  rdiff-backup is a client-server architecture. On the network, it works similar to a really smart rsync and over ssh-tunnels. These are automatic.

Sigh ... hopefully, I haven't scared you off.  Setting up "pulled" system backups is a complex thing and requires some non-obvious userid tricks with ssh to work.

Most people would start with local backups, then move to pushed backups.  Pushed system-level backups does require ssh and normal multi-user knowledge/skills with that tool.  There's something that just makes "pulled" backups another level of complexity.  Or perhaps it is the way that I chose to implement them by pushing data-gathering scripts from the backup server to each remote client system as part of the pre-backup scripting.  IDK.  OTOH, if I make any changes on the backup server backup scripts, all the systems will use those changes going forward.

Hopefully, I didn't confuse you too much.

Having a backup isn't the only thing.  You need to test and validate the that you can restore to the same system or a completely different system.  Backups that can't be restored when needed are useless. When I was first setting up my backups, it took me 5 attempts to ensure I had all the data saves in a way that would allow a restore within a reasonable period of time.  For me, that restore time target was 1 hour.  Systems with little data are restored in about 30 minutes.  Most systems are restored in 45minutes of they have less than 50G backed up.  I have one system with nearly 40TB of storage.  Most of that storage doesn't use rdiff-backup at all. I use rsync for a delayed mirror of storage.  No versioning at all.  There's a point where I just don't want to spend the money to have daily, automatic, versioned backups for everything.  I do for the OS and normal files, even on that system with many TBs of storage, but that's ... let me look ....```

        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Sun May  7 04:35:06 2023         18.2 GB           18.2 GB   (current mirror)
Sat May  6 04:35:06 2023         96.0 MB           18.3 GB
Fri May  5 04:35:07 2023         1.17 GB           19.5 GB
...
Tue Feb  7 04:35:05 2023         73.0 MB           46.9 GB
Mon Feb  6 04:35:04 2023         2.01 GB           48.9 GB
```
About 19G to restore data from last night.  Every once in a while, I'll leave a huge file somewhere it shouldn't be on the system ... which makes the total storage needed for backups also larger as those files before they are too old and get removed automatically after X days in the backup versions.

---

### Post by mason64 on 2023-06-07
Thank you TheFu - done some testing and i think i am ready to get the backups going 

One thing 


Where do you get the data from in the last bit of code you posted with the data sized backed up and dates. 

Thanks
Dave

---

### Post by TheFu on 2023-06-07
> **mason64 said:**
>  Where do you get the data from in the last bit of code you posted with the data sized backed up and dates. 

Dude, I hope you read the documentation before blindly trusting all those options I posted.  There are lots of options for rdiff-backup and some of the text files in the backup directories have summary information which is extremely useful to slurp, parse, and view daily.

For example, I get a daily report about each backup performed for each system. I set this up with a tiny script that parses the log for the specific server in a trivial way:
```
=== Time for Backups to blog44 === 
StartTime 1686024423.00 (Tue Jun  6 00:07:03 2023)
EndTime 1686024446.24 (Tue Jun  6 00:07:26 2023)
ElapsedTime 23.24 (23.24 seconds)
TotalDestinationSizeChange 1170840 (1.12 MB)


=== Time for Backups to nextcloud-lxd === 
StartTime 1686024463.00 (Tue Jun  6 00:07:43 2023)
EndTime 1686024475.34 (Tue Jun  6 00:07:55 2023)
ElapsedTime 12.34 (12.34 seconds)
TotalDestinationSizeChange 1231142 (1.17 MB)


=== Time for Backups to pi3 === 
StartTime 1686024490.00 (Tue Jun  6 00:08:10 2023)
EndTime 1686024511.53 (Tue Jun  6 00:08:31 2023)
ElapsedTime 21.53 (21.53 seconds)
TotalDestinationSizeChange 10630174 (10.1 MB)
```
That an example from last night.  I think the script just does an **egrep**. It is ok to look at the backup storage area, just don't touch anything.

Every day, I setup to get an email that has some important backup data ... and blanks for any backups that fail ... from the Duration and Size Change, I can tell much about the backup.  As you can see, when performed daily, rdiff-backup, is pretty efficient ... taking just a few minutes on those examples.  I haven't had a backup failure in a few years - maybe longer.  When there is a failure, every program I've used complains loudly, so it isn't something that would be missed for weeks.  Of course, I have to look at the emails from cron to see those failures.  If I don't look, nobody will beat me over the head about it.

Of course, some systems have much more data that is changing all the time and those backups take longer.  Let me check.

```
=== Time for Backups to zcs45 === 
StartTime 1686034888.00 (Tue Jun  6 03:01:28 2023)
EndTime 1686036237.79 (Tue Jun  6 03:23:57 2023)
ElapsedTime 1349.79 (22 minutes 29.79 seconds)
TotalDestinationSizeChange 119452288 (114 MB)

```

What that doesn't show is that there are over a million files included in the backup. Check each for changes takes some time. Plus, there are a few DBMS files in that box. I export them to a text file, which changes every night.   Before I switched from rsync to rdiff-backup, to backup all the systems here was taking over 12 hrs.  Now it is under 30 minutes, total.  I looked at other popular backup tools based on Duplicity (duplicity, deja dup and duplicati), they were taking 8+ hours to get 1 system. I cancelled the job and never looked at them again.  It could have been I'd done something wrong. IDK.

---

### Post by mason64 on 2023-06-08
> **TheFu said:**
> Dude, I hope you read the documentation before blindly trusting all those options I posted.  There are lots of options for rdiff-backup and some of the text files in the backup directories have summary information which is extremely useful to slurp, parse, and view daily.



No I am just using the standard settings at the moment, just rdiff-backup "source Files" "backuplocation"

i am going to play with the options very soon and see what works well for me. 

Thanks 
Dave

---

### Post by TheFu on 2023-06-08
The common errror with rdiff-backup is forgetting that regardless of --include/--exclude options, there must always be an overall "source Files" "backuplocation" in the command, even if excluding everything in the "source Files" happens.

For backups, the command I posted is just about the minimal set of useful options that will easily support backing up a system with multiple directories involved.

When I'm testing a new backup tool, I use /etc/ as my source test directory.  It has files owned by different users, with specific permissions, symbolic links, and some files are only for root to view, while /etc/ is still relatively tiny.  Adding a comment to one (or 5) of the files in /etc/ does no harm, but let's me see what the next backup version causes in the target for backup area.  I always go take a look.  It is very enlightening.

BTW, reporting on versions and sizes shoujld be part of every backup tool.  Also, there needs to be a way to remove old backups, since we don't just want to keep taking backup versions forever.  Nobody has infinite storage.  These things are all in the documentation, along with caveats.  Plus, getting a working backup is only 10% of the work.  Backups aren't our goal.  The restore of a specific version of 1 file, 10 files, a directory area, or everything is the goal. Until the restore process is tested and validated, backups are meaningless.  Sorta like hiking up a mountain.  Getting to the summit is everything, but just getting to the mountain so it is even possible is what a backup is in the total backup-restore process.

---

### Post by TheFu on 2023-06-15
So, I gave a presentation a few months ago about my backup methods.  It has the code and sufficient text to put things together for local backups using rdiff-backup.
[https://lpi.jdpfu.com/2023-Backups/2023-Backup-How-To.html](https://lpi.jdpfu.com/2023-Backups/2023-Backup-How-To.html)

It is multiple files, linked.  I'd appreciate feedback for things that aren't clear.

I figure showing a concrete example would be useful along with how to get some reports and keep the backup area cleaning itself over many months of use.
If you just look at the directory, all the files will be shown, including the code as separate files.

I show the Pre-Backup Tasks more FYI, not a full script that can be taken and used blindly. They are exactly what I do, however.  Much of it is gathering current information about the system state, which can make dealing with issues that don't require a full install easier.

Hope this is helpful to someone.

---

### Post by aljames2 on 2023-06-15
Wow, thanks TheFu.  I just read it all

A great resource, even if using one of the other tools mentioned.  I learned about rdiff-backup when I was starting out and you helped me a lot in these forums with it then.  This brings together what a having a backup process really means.

I do use LVM snapshotting, and I have adapted my scripts to achieve homogeneous data, primarily by not putting so many root level directories in separate LVs.  But, I wonder now, why am I even snapshotting.  The point of the snapshot is to freeze a running system at a point in time, so now we can back up data while it’s not changing.  Probably not needed though unless you are wanting to back up a running database for websites or other DBMS applications?

Thanks again

---

### Post by TheFu on 2023-06-15
> **aljames2 said:**
> Wow, thanks TheFu.  I just read it all

A great resource, even if using one of the other tools mentioned.  I learned about rdiff-backup when I was starting out and you helped me a lot in these forums with it then.  This brings together what a having a backup process really means.

I do use LVM snapshotting, and I have adapted my scripts to achieve homogeneous data, primarily by not putting so many root level directories in separate LVs.  But, I wonder now, why am I even snapshotting.  The point of the snapshot is to freeze a running system at a point in time, so now we can back up data while it’s not changing.  Probably not needed though unless you are wanting to back up a running database for websites or other DBMS applications?

Thanks again

I worried it wasn't sufficiently clear.  You're a bit of an expert, so there shouldn't be much in there as a surprise.  I worry that intermediate-level people can't get something useful.  At my LUG presentation, there were some good questions, but as you can expect much of it was over the heads of the people who needed to setup backups and for everyone who already had backups working, they weren't looking to change.

As for LVM snapshots.  If you don't logout when backups are happening, it is possible for files to be open and actively written, so snapshots are still extremely useful.  I didn't include that for fear of being TOO technical for 90% of the people reading. 

BTW, all those pages were generated using vimwiki's html export function.  I wrote a 1-line perl command to pull the code sections out and save them to separate files too. Figured that would be helpful for some people.

---

