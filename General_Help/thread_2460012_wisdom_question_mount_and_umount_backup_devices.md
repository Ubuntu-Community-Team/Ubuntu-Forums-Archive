---
title: "wisdom question: mount and umount backup devices??"
date: 2021-03-31
forum: General Help
---

### Post by Old Jimma on 2021-03-31
Hello Community:

I want people to please provide their opinion about the safety of my strategy for making the back up. 

I use executable scripts that I execute using chrontab .... to back up my system.

Currently, I have a mechanical hard drive device that is mounted on startup, where a the backup of my home directory is written.

I want comments on what is safest:

[LIST]
[*]should I mount the device at start up, or
[*]should mount the device only when the executable script to make backups is executed, and then after the back up is completed, should I unmount the device?
[*]
[/LIST]

Here is my script"

> 
device="/dev/sdd1"

umount /dev/sdd1 /mnt/sdd1

mount /dev/sdd1 /mnt/sdd1

testfile="/mnt/sdd1"

if [ -e "$testfile" ]
then
  echo "drive is mounted."
  date


cd "/mnt/sdd1"
ls
rm -Rvf *
ls

pwd

date

##
NOW=$(date +"%y-%m-%d") 
#
#
##
##
cp -avL /home/somebody .
mv somebody "somebody - $NOW" 


chown -R somebody:somebody "/mnt/sdd1"

chmod -R 777 "/mnt/sdd1"
##
##
date

else
	echo "No sdd1 mounted"
	date

fi

umount /dev/sdd1 /mnt/sdd1



Thanks,
Old JImma

---

### Post by TheFu on 2021-03-31
[LIST]
[*]All the umount commands are wrong. Only 1 parameter is needed.
[*]To verify the drive is mounted, I'd ask mount.  The test above will always return true, since the directory used as the mount point will exist.
[*]No freakin' way would I have **rm -Rvf *** in a backup script.  NEVER EVER assume a pwd in any scripts.  Always specify the paths for command, config files and locations.
[*]**cp** really isn't a good backup tool.  Use **rbackup** or **rsnapshot** or **rdiff-backup** instead, so you get versioned, fast, efficient, backups. rdiff-backup fast. Getting an entire system is just a few minutes (2-5) most of the time.  Versioned backups are very important.
[*]**chmod 777** loses 50% of what a good backup holds - the permissions, owner, group, ACLs and xattrs.  Don't. Just don't do that.
[/LIST]

Should we mount and umount backup storage?  It depends.  It would be better to have a different computer "Pull" the backups from the system(s) that need backing up.  "Pull"ed backups solve some malware and crypto-locker issues.  Versioned backups addresses file corruption and backup performance considerations.  Using a different computer can address some network security aspects.  If the client machine has direct access to the backup storage, that is a potential failure.

Here's how my perl backup script on the backup server checks that the backup storage is mounted. It can be converted to bash 1-for-1.
```
sub validate_mnt_point {
  # Need to verify that the backup partition is mounted
  my $mnt=`/bin/df | grep -c $mnt_point`;
  if ( 0 == $mnt ) {
     print "ERROR: Mount point not mounted: $mnt_point $target_dir \n";
     exit 1;
  }
}
```

---

### Post by oldfred on 2021-03-31
Also do not use device like this, always use UUID or labels to create backup directory:
device="/dev/sdd1"
Devices change, when I plug in my flash drive, and reboot, every drive moves up one letter. So then your sdd would be actually sdc and you erase wrong drive.

I do backup to another drive in my system, but do not really consider it a backup, but a copy even though I may call it a backup.
My backups are to another system in another state using sneaker net, twice a year. And to multiple flash drives. My methods would not pass TheFu's best practice, but works for me.

My install script on each system, includes creation of a backup, /mnt/backup.
Then my backup script checks if mounted, and mounts it or errors out similar to TheFu's example.
Since internal drive, I could permanently mount with fstab, but do not. Not sure why?

For my copy that is not a backup, I started with this rsync script from MountainX. But then added export of installed apps, some housecleaning (most in separate script) & changes to limit what data is copied as caches & temp data not required. I do not backup system. And any system config files that I manually edit, I also copy into /home to be backed up. My /home & data partitions are separate, so each backed up.

Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&p=7015603#post7015603](http://ubuntuforums.org/showthread.php?t=868244&p=7015603#post7015603)

Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders)

---

### Post by Old Jimma on 2021-03-31
Hi Fu and Oldfred,

I'm not sure why this thread is solved. However, the fact this this is marked as "solved" provides further proof that backing my work up in as well as I can is essential. Thank you for your responses.

Fu and OldFred, I have some replies here that I hope will read. Please be certain that I ask questions only because I don't understand, and no other reason.

Here is what I learned from you guys:

1. Get a better plan for making backups.
2. Avoid some obvious bear traps.

In what I write below, please bear in mind that 


Here is a short list ... an not a complete list of the bear traps. Some of the problems you pointed to seem to be unresolvable. I'll explain breifly, below.

**[COLOR="#FF0000"]Biggest bear Trap[/COLOR]**

... is to refer to devices with things like **/dev/sdx** instead of **/dev/UUID**. I"ve fixed that.

**[COLOR="#FF0000"]Here are a few particulars that seem relevant.[/COLOR]**
[LIST]
[*]aside from the hard disk that came with my laptop, 3 of the 4 other storage devices are external 3TB mechanical hard drives, and 1 is an internal 1TB SSD,
[*]my needs to retrieve archived data is occasional, but requiring only finding old versions of files, documents, or musical takes that I wrongly thought I could delete. This means, that every few weeks I sort thru by backups to find old versions of scores that I wrote, or takes that I recorded.
[*] I don't want to retrieve everything I've done over the past 25 years, just to get one or 2 files.
[*] I tried the ubuntu backup app... it does not work for me...[COLOR="#FF0000"] in fact it didn't work at all[/COLOR].  
[*]
[/LIST]

So, given my needs, why not use the cp command??? It allows me pick thru file structure that is familiar to me, and allows me to find the specific files that I'm looking for.

So, Fu.... I deeply respect you and am always grateful for your replies and information. That have always helped me greatly. So, why not cp and rm  now that I've got the device names labeled using UUIDs as you've sagely advised??

**[COLOR="#FF0000"]My Original Concern[/COLOR]**

As you guys have pointed out, is is easy to screw up big-time and fast! That is why I wanted the external hard drives to not be mounted at system start up. **[COLOR="#FF0000"]To avoid screw-ups[/COLOR]**, I don't want to connect to them for any reason other than to create a new backup of my entire file system, or to access a previous version of my file system for the purposes of finding an old manuscript or take that I purposefully deleted... and subsequently changed my mind about.

**[COLOR="#FF0000"]That's why I asked for info about the mount and umount commands. I've learned that they do not work in an executable script that is run by crontab. How do I fix this???[/COLOR]**


I do a backup every night of my entire file system. that's why I have 8Tb of storage.

Thanks,
Growing Older by the Day Old JImma from the Old Country

---

### Post by HermanAB on 2021-03-31
I use a simple trick to confirm that a disk is mounted:
When I make a mount point directory, I create a file there called something like 'not-mounted'.  
When the disk is mounted, the above file should become invisible/unreachable.

The advantage is that if you go there with a file browser, then you can see immediately whether there is a problem or not.

---

### Post by TheFu on 2021-03-31
> **Old Jimma said:**
> Fu and OldFred, I have some replies here that I hope will read. Please be certain that I ask questions only because I don't understand, and no other reason.
Everyone is learning how to do things better. Nobody knows it all for every situation.

> **Old Jimma said:**
> [LIST]
[*]aside from the hard disk that came with my laptop, 3 of the 4 other storage devices are external 3TB mechanical hard drives, and 1 is an internal 1TB SSD,
[*]my needs to retrieve archived data is occasional, but requiring only finding old versions of files, documents, or musical takes that I wrongly thought I could delete. This means, that every few weeks I sort thru by backups to find old versions of scores that I wrote, or takes that I recorded.
[*] I don't want to retrieve everything I've done over the past 25 years, just to get one or 2 files.
[*] I tried the ubuntu backup app... it does not work for me...[COLOR="#FF0000"] in fact it didn't work at all[/COLOR].  
[/LIST]
I never got duplicity working for my needs either. Duplicity is the CLI version of Deja Dup, the default application Ubuntu pre-installs. It checks all the  boxes for what a backup tool should accomplish, but it makes the backup files hidden inside funky archives.  rdiff-backup, rsnapshot and rbackup all create what appears to be a mirror (like cp), but also provides versioning.  If you need the file from the last backup, just go and copy it.  The directories are the same as what you know from the source.  That's one of my requirements, BTW.

> **Old Jimma said:**
> So, given my needs, why not use the cp command??? It allows me pick thru file structure that is familiar to me, and allows me to find the specific files that I'm looking for.
see above.

> **Old Jimma said:**
> So, Fu.... I deeply respect you and am always grateful for your replies and information. That have always helped me greatly. So, why not cp and rm  now that I've got the device names labeled using UUIDs as you've sagely advised??
I think it was Oldfred who recommended using either a UUID or LABEL.  For external drives, I'd use the LABEL - since that's how humans think better.  Just replace the UUID= with LABEL= and use whatever LABEL the partition has that you've set.  Perhaps "BACKUPS"? would be a good label?  Don't worry too much about this. What's important is NOT using the device (/dev/sdZ1), since those can and do change based on who systemd discovers storage.

> **Old Jimma said:**
> As you guys have pointed out, is is easy to screw up big-time and fast! That is why I wanted the external hard drives to not be mounted at system start up. **[COLOR="#FF0000"]To avoid screw-ups[/COLOR]**, I don't want to connect to them for any reason other than to create a new backup of my entire file system, or to access a previous version of my file system for the purposes of finding an old manuscript or take that I purposefully deleted... and subsequently changed my mind about.
Avoiding screw ups is important.  One of the screw ups I've seen and done myself is assuming USB storage for backups was mounted, but it wasn't.  All the backups ran, but rather than storing to the BACKUPS drive, it wrote to / and filled up that partition instead, which crashed the OS.  We need to pick which screw ups to avoid. ;) Sometimes there isn't just 1.

> **Old Jimma said:**
> **[COLOR="#FF0000"]That's why I asked for info about the mount and umount commands. I've learned that they do not work in an executable script that is run by crontab. How do I fix this???[/COLOR]**

Well, I'm not sure I understand this statement, since mount and umount commands DO work both in scripts and in crontabs.  mount/umount need to run with root privilege.  That means 
a) run the backup script from root's crontab (there are 3+ locations depending on how often you want to run it) 
OR
b) run the script from your own crontab, but setup automatic mounting/umounting using the fstab or autofs 
OR
c) setup sudo to allow the userid running the backup script to use mount/umount without any password necessary

Regardless, all commands should specify the full path to their location, since the PATH environment variable cannot be trusted in scripts or especially in a cron job.  What do I mean?
```
$ which mount
/usr/bin/mount
```
So everywhere you have just "mount", it needs to have "/usr/bin/mount" - that's the full path to the command.  Further, the mount commands used like:
```
device="/dev/sdd1"
umount /dev/sdd1 /mnt/sdd1
mount /dev/sdd1 /mnt/sdd1
```
I'd change to :
```
#!/bin/bash
TARGET="/mnt/backups"
LABEL=BACKUPS
/usr/bin/mkdir -p $TARGET
/usr/bin/umount  $TARGET
/usr/bin/mount LABEL=$LABEL $TARGET

# check that the mount worked here ...
if [ 0 -ne $( /usr/bin/mount |/usr/bin/grep  -c $TARGET ) ] ; then 
   echo $TARGET is mounted.
else
   echo $TARGET is NOT mounted.
   exit 1;
fi
...
```
Bash scripts must have that first line. They won't work from cron without it.

IMHO, backups should be run as root, since that's the only way to keep the different file permissions as they were.  The storage file system needs to be a Linux file system, not NTFS.

> **Old Jimma said:**
> I do a backup every night of my entire file system. that's why I have 8Tb of storage.
Thought that only your HOME directory was backed up in the other post. After all, there was a **chmod 777**.

That's enough until we see the new script.

---

### Post by Old Jimma on 2021-04-01
Hey, when I die and go to heaven I'm pretty sure I'm gonna see Herman Ab and TheFu there. 

These guys have been my guardian angels for a real long time. Were it not for them I woulda been sitttin' in a dark hole.

Old Jimma from the Old Country

---

### Post by Old Jimma on 2021-04-02
Hi TheFu,

Thanks for your superb reply. I read your reply.

I fixed the Labels, just for fun, and get better labels that I understand.

Also, I found the Timeshift app in the Ubuntu Software repository/folder. There is sort of a "howto: at [https://www.youtube.com/watch?v=ifvcrsnBAp4](https://www.youtube.com/watch?v=ifvcrsnBAp4)

I did a few experiments with it, and they restored the folders and files I deliberately deleted. It is pretty fast, too. 

Thanks for all of your advice!

Old Jimma from the Old Country

---

