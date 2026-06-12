---
title: "Backup utility options for full and incremental backup across a network"
date: 2016-08-25
forum: General Help
---

### Post by niallcd on 2016-08-25
So, I've been doing some research on backup solutions, and I'm wondering what the community has found to be useful, given their experiences. I've looked at a few programs, but so far, I'm underwhelmed. For the most part I'm concerned about reliability which is why I'm asking you folks. I understand that nothing is perfect but I'm still curious about whats worked for people here and what hasn't. I could use rsync and if that's the best option then so be it. It would be nice if it had a gui, for other members of my family who are less terminal literate, but it's not a deal breaker.

What I have set up:
Server: I have a server running Ubuntu Server 15.10. It has a boot drive, and 6 other hard drives connected to it, internally.
Backup machine: I have a work machine running Ubuntu 15.10 in my office. It has a very similar config to the server. One boot and 6 identical drives to that of the server. 

What I'm looking to achieve:
Ideally I'm looking for a backup solution that will do:
A full backup of the servers 6 drives across a network to the backup machine in my office.
Incremental backups thereafter.

Note. I realize that a full backup takes a considerable about of time, depending on a number of factors, but it's not a priority for me. It can take as long as it needs.

My main goal, is to be able to take a drive from the backup machine, and plug into another without having to restore the data. 
If I need to take the drive into work, I'd prefer to take it from the backup machine, and not disrupt the server.

Thanks in advance.

---

### Post by TheFu on 2016-08-25
Support for 15.10 ended last month. Please upgrade to a supported release.

I don't leave backups to end-users. That never works and they get confused.  I've seen someone edit files on an internal drive, then copy them off to an external drive, calling that "a backup", then deleting the files from the internal disk - left with 1 copy, on an external, cheap, low-speed, low-quality disk.  Yep, best NOT to leave backups to end-users.

rsync is an 80% backup solution. It doesn't do everything we need in a backup tool.  However, most Unix F/LOSS backup tools are based on librsync, so a full backup only need happen once.

For about the last 8 yrs, I've been using rdiff-backup.  It does versioned backups and is suitable for system-level backups, unlike most of the tools with GUIs.  Backups need to be:
* automatic
* daily
* versioned
* off-site
* efficient
* encrypted (ideally)

rdiff-backup doesn't do encrypting itself, but the remote storage can be encrypted, if you like.  I keep 60-120 days of versioned backups for each system here. How long depends completely on the risks involved with the system.  The most current backup looks like a mirror, so to get the last copy back is just a cp command. Very convenient. If it fails, it fails loudly, as is expected in Unix. If everything works, it is almost silent.  Efficient - both in storage and time - sure the first backup takes as much time as a full copy, but after that, rdiff-backup uses diffs, so most system backups take just 1-5 minutes a day.  rdiff-backup honors ssh-keys, ~/.ssh/config, and uses ssh tunnels by default for network backups. That means there isn't any need to mount the backup storage on the client and risk any of those nasty file encryption viruses.  It would be best to "pull" the backups, not push them.

While you can grab the drive for a restore, that would break all the versioning for the following backups.  I'd get a new disk and restore the files onto that.  If the latest version isn't what you want, you can go back days, weeks, months ... however long you have backups.  Since they are stored very efficiently, keeping 60 days of backups doesn't require much overhead. Of course, how much storage is needed completely depends on the amount of data that changes daily.

I wrote a few small scripts to provide backup stats daily.
```
=== Time for Backups to xen41 === 
StartTime 1472105118.00 (Thu Aug 25 02:05:18 2016)
EndTime 1472105457.73 (Thu Aug 25 02:10:57 2016)
ElapsedTime 339.73 (5 minutes 39.73 seconds)
TotalDestinationSizeChange -19601100 (-18.7 MB)

``` is a sample for a small blog server.  rdiff-backup also has reporting capabilities, but they take longer.

Anyway - there are lots and lots of other posts about this topic. I'd encourage you to review many of them as part of the decision-making effort.  

One final thing - it is hard to automate a backup when it requires a GUI to be run.  I want backups running when I'm NOT awake and using the system(s).

---

