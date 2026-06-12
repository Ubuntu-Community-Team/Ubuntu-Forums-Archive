---
title: "sudo not working (/usr/bin/sudo must be owned by uid 0) in ubuntu 16.04"
date: 2016-04-23
forum: General Help
---

### Post by terces86 on 2016-04-23
I probably messed up my permission by using the following command I stupidly just copy&pasted into the terminal:
```
sudo chown -R $(whoami) $(npm config get prefix)/{lib/node_modules,bin,share}
```

Whenever I try using sudo I get the following error message:
```
sudo: /usr/bin/sudo must be owned by uid 0 and have the setuid bit set
```

I have been searching for a solution to this, but I am unsure what I should do, especially because many solutions seem very outdated. If possible I would like to avoid having to reinstall. Any help is greatly appreciated. I won't be able to reply for the next couple of hours though, as it is getting late.

---

### Post by TheFu on 2016-04-23
It is bad.  Linux (and all Unix-like systems) are multi-user from the beginning, into the middle and at the end. That command just broke that - sudo is just the start - it is bad. Many things will not work now.

a) restore from a backup that includes all the correct owners/permissions
    or
b) reinstall the OS

Not really any other choices. Sorry.  

None of my systems have the npm command on them. No idea what it does.
```
$ npm
The program 'npm' is currently not installed. You can install it by typing:
sudo apt-get install npm

```
The recovery console idea won't work (I have doubts that it will even boot) except to restore a backup. That chown cmd was a really, really, really, bad idea.

---

### Post by yetimon_64 on 2016-04-24
> **TheFu said:**
> It is bad. ...

a) restore from a backup that includes all the correct owners/permissions
    or
b) reinstall the OS

Not really any other choices. Sorry.

Yes, agree; If possible I'd be interested to know the source of that code snippet OP, especially if it is from an online source. That is one nasty little mess maker for a linux system for any unwary user. Not nice at all.

This is one occasion a clonezilla or dd image, or even a "tarball", of the root partition would be of great usefulness, it would be recoverable in minutes OP; otherwise a full reinstall is called for sorry to have to say.

**Edit:** Not sure if this next suggestion will work OP, but I just had a thought regarding using the recovery boot option from the grub bootloader screen (in the "Advanced" section). **IF** you can get to a root prompt from a recovery boot (and I am _*not sure*_ you will be able to with sudo being damaged) it **MAY** be possible to reverse the damage from there. By issuing the same command with "root" rather than "$(whoami)" and without the use of sudo (not needed from a root prompt on a recovery boot) it may just be possible to reverse the damage. Again, I must make it absolutely clear, I have no idea if this will work, but would tend to give it a shot before trying a full reinstall.

Try the command from the root prompt on the recovery boot like,
```
chown -R root $(npm config get prefix)/{lib/node_modules,bin,share}
```

Note, I have never tried to get a root recovery prompt with a broken sudo command in play before;
this is a bit of a "shot in the dark" as far a "fix" goes.

**Edit 2:** If you get errors from the chown command at the root prompt that the drive is not writeable you may need to run the "fsck" option first to remount the drive read/write first, then drop to a root prompt and issue the above reversing command. Not sure how this will pan out for you if the fsck command is affected by your first usage of that command. Good luck, yeti.

---

### Post by Impavidus on 2016-04-24
I don't know what the command **npm** is supposed to do, but it seems it created the prefix **/usr**, so you chowned /usr/bin/sudo. **chown**, along with its friends **chgrp** and **chmod**, can remove a lot of entropy from your system if used with the recursive option **-R**. Simply reversing it as yeti suggests may work, but it will make all files owned by root even if they originally were not. I checked on my 15.10 system and it appears that most files in the affected directories (although I'm not completely sure which directories were affected) should be owned by root, but not all. In particular, on my system **/usr/bin/at** is owned by **deamon** and making it owned by root could cause problems. There may be other exceptions on your system. There are only two sure ways to fix it: restore a backup of your root directory or reinstall.

---

### Post by terces86 on 2016-04-24
npm is the node package manager. I was having problems because I wasn't able to use it to install packages without sudo. Now **I** can't use sudo...but hey, it installs node packages just fine.

Well, since I *just* setup the laptop, might just do it all again. I was just hoping that there was some command that would restore system permissions/ownerships to default values. Because it seems to be one of those things you can break very easily and then get stuck...

Thanks for your help.

[Edit]
to avoid further problems in future: What is a good method to create backups? What backup method should I use, if I want it to include the system files? I have two partitions (one for / and one for /home) and a third large partition for Data storage.

---

### Post by TheFu on 2016-04-24
> **terces86 said:**
> I was just hoping that there was some command that would restore system permissions/ownerships to default values. Because it seems to be one of those things you can break very easily and then get stuck...

There are many tools for this. They are called backups. I know this doesn't help now.
There is also a security tool, COPS. [https://en.wikipedia.org/wiki/COPS_%28software%29](https://en.wikipedia.org/wiki/COPS_%28software%29)  Used to run it back in the mid-1990s. Backups were harder then, since disk space cost $1000s, not $40 like today.  I backup about 30 systems onto a single 3TB disk ($80) and keep 60-120 days of versioned backups for each there.

> UNIX was not designed to stop its users from doing stupid things, as that would also stop them from doing clever things. 

What is a good backup tool? That is highly subjective. The way I do it for the 30 systems for which I'm responsible probably isn't the way most people do it.  There are 50+ different backup tools, each with good and bad features.  Just depends on your requirements AND skill.  Usually the less skilled the admin is, the more disk storage and downtime needed to make backups **which can be restored.**  Anyone can make a backup that cannot be restored.  There are 50 other threads here about backup and restores. Review those. You'll see all sorts of answers and some problems that people have with the different tools.

There are 3 main sorts of backups:
* bit-for-bit images (clonezilla, partimage, fsarchive, dd, ddrescue, and 10 other tools)
* file based (rsync, rsnapshot, rbackup, rdiff-backup, back-in-time, tar, and 20 others)
* obscured backups ( duplicity, bacula, and 10 others)

All of these can leverage LVM snapshots, if used. Most people new to Linux won't use LVM due to the added complexity. I use LVM on every physical disk mainly for the added flexibility it provides.

Rdiff-backup is my backup tool choice, but a full system restore requires advanced skills. Takes between 30 and 45 minutes for me to restore a system and there are a few manual steps.  Backups require 2-5 minutes daily usually.  It is highly efficient with storage and time to backup. The system can be running when the backup is made, which is a plus.  I keep 60-120 days of versioned backups for each system. The last backup appears as a mirror of the system, so to restore, can be just a copy or rsync. For example, this desktop has 
```
$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/vda1        17G   13G  2.6G  84% /

```
17G of storage. It is a running inside a KVM virtual machine.```

# rdiff-backup --list-increment-sizes vm-desk
        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Sun Apr 24 01:15:07 2016         5.41 GB           5.41 GB   (current mirror)
Sat Apr 23 01:15:07 2016         8.06 MB           5.42 GB
...
Fri Feb 26 01:15:06 2016         15.5 MB           6.90 GB
Thu Feb 25 01:15:07 2016         10.4 MB           6.91 GB
Wed Feb 24 01:15:07 2016         15.5 MB           6.93 GB
```
I can restore this machine with the data on Feb 24th, but the OS will be current. I don't backup the system. I backup the information needed to put the system back with the settings and data for that date.  Anyway, you can see the current backup is 5.41G, but for 60 days, cumulative data, is only 6.93G total. What a bargain!  

Setup a backup summary for every machine to be emailed to me daily.
```
=== Time for Backups to vm-desk === 
StartTime 1461474907.00 (Sun Apr 24 01:15:07 2016)
EndTime 1461475133.14 (Sun Apr 24 01:18:53 2016)
ElapsedTime 226.14 (3 minutes 46.14 seconds)
TotalDestinationSizeChange 9325476 (8.89 MB)
```
Shows start/end, how much and how long. Not much changed yesterday on that machine, which makes perfect sense. rdiff-backup isn't perfect, but it is the least imperfect answer for me, today.

**Bit-for-bit images** means just that. It is uses almost the same amount of storage as the original. Making a bit-for-bit backup usually requires that alternate boot media be used, so the OS is completely static.  That isn't easy to automate or accomplish for me.  I use bit-for-bit backups for Windows because my Windows-fu is very weak.  I don't know where things need to go and I have no idea how to fix a broken boot in windows. Only do it quarterly. I don't leave important data on Windows machines. It it is important, it goes on Linux storage, which gets 60-120 days of versioned backups. ;)

Obscure backups are most like the old-school backups from the 1960s.  Weekly fulls and daily incrementals. The data is put into non-trivial chunks. To restore, the same tool that was used to make the backups is required because the data storage method is efficient, but non-trivial. This isn't necessarily bad, just means that seeing a bunch of files and data, but not being able to determine which file has which data inside can't bother you.  Duplicity uses normal Unix tools to accomplish this and if you look at the feature list, it truly is THE "best practice" tool to be used.  Looked at it 3-4 yrs ago. At the time, it was extremely slow and the restored files didn't match the backed up area.  For me, that is a non-starter.  I also didn't like that having the backups encrypted was almost mandatory.  A restored backup should match the backup area if none of the files changed, right?

Anyway, lots of options.

---

