---
title: "I need a simple backup tool"
date: 2016-02-28
forum: General Help
---

### Post by Gnusboy on 2016-02-28
Hi all

I am trying to figure out how to do a new backup to an external Toshiba 1 TB hard drive. A few years ago I was able to backup my home folder to the Toshiba drive. I don't recall what program I used
and can't find it now. I set it up using GParted with 2 primary Ext 4 partitions and transferred my home folder from my computer over to the external drive without a problem.
Now, I want to copy my current HOME folder with all the current data over to the external drive. 

I'd like to know whether I can simply cut and paste the updated home file over to the external drive.
 Can I use a different name it and copy it to a new folder? 
Should I try to copy it to the existing external drive folder as an incremental backup?
There is more than enough space to make a new folder.

I have looked for an answer to these questions and can't find exactly what I need. I tried Deja Dup for continuous backups, but it just copied the same files over and over without any updates. 
If you can give me a helping hand on the problem I will appreciate it. 
Thanks.
Gnusboy

---

### Post by sammiev on 2016-02-28
Have you looked at Luckybackup yet? 

It's in the software center.

---

### Post by Bucky Ball on 2016-02-28
> **sammiev said:**
> Have you looked at Luckybackup yet? 

It's in the software center.

+1. Took the words right out of my fingers. Use it as my main backup tool. You can use it to do simple things or get more complex with it. Powerful little beast if you want it to be. :)

---

### Post by HermanAB on 2016-02-28
rsync of course.

---

### Post by mikodo on 2016-02-28
Yes, for cli rsync has to be easiest. And very versatile for moving data around with many options. It is not really used for incremental backups. But for simple movement I usually use:  rsync -av options, and that works well for backups too. Just reverse the to and from. See man rsync. 

For cli with incremental backup there is rdiff-backup. The incremental are called deltas. See man rdiff-backup

For a gui one, I strongly recommend Back In Time. It is actively being developed and there is even a PPA available for its' newest stable version.

I am not sure Luckybackup is still being developed and having bug fixes done to it. You'll have to check.

For simple copy and paste of directories/files to a usb-node, you might have to watch for permissions and ownership with that. Something to consider. Just an FYI. No harm in trying it though and, seeing if you can copy it back to another folder as your regular user as a test. If not, then you need to change things as mentioned. If it becomes problematic for you, you can always re-format the drive with GParted. That doesn't completely erase the data but, it makes it very hard to see for the average person.

---

### Post by kjohri on 2016-02-29
From the command line,

$ cd <backup_dir>
$ rsync -avz --delete <home_directory> .

For more details, look at this link, [http://www.softprayog.in/tutorials/rsync]("http://www.softprayog.in/tutorials/rsync").

---

### Post by Gnusboy on 2016-02-29
Thank you all. I appreciate the help
Gnusboy

---

### Post by mastablasta on 2016-02-29
> **mikodo said:**
> 
I am not sure Luckybackup is still being developed and having bug fixes done to it. You'll have to check.
.
not sure about new iterations and features, but bugs are still being responded to by the dev. so it's maintained. maybe it reached perfection.

rdiff-backup is also in same state since 2009 i think.

in any case some apps dont' need ot be constatntly fiddled with and upgraded. kind of like cp command or something...

---

### Post by sgage on 2016-02-29
> **kjohri said:**
> From the command line,

$ cd <backup_dir>
$ rsync -avz --delete <home_directory> .

For more details, look at this link, [http://www.softprayog.in/tutorials/rsync]("http://www.softprayog.in/tutorials/rsync").

Grsync (in the repos) is a great graphical front-end for rsync - I've been using it for years to back up to an external drive. Most all of the important options are available as check-boxes. Simple, fast, and reliable.

[Edit: Grsync will also show you the rsync command that it has put together based on options selected, so you can see exactly what's going on. A good way to learn rsync, if you want to be able to run it from the CLI...]

---

### Post by ra7411 on 2016-02-29
> **sammiev said:**
> Have you looked at Luckybackup yet? 

It's in the software center.

I've been using Grsync. Is [COLOR=#000000][I]Luckybackup better, how does it differ?
[/I][/COLOR]

---

### Post by Bucky Ball on 2016-02-29
> **Gnusboy said:**
> 
Now, I want to copy my current HOME folder with all the current data over to the external drive. 



Clonezilla or fsarchiver will do this for you. If you just want to copy a partition, it's that simple. Sorry I don't have links for them on this machine, but easy enough to get info. fsarchiver is easy to understand and very simple. 

@ra7441: If you have questions you would like answers to or help with, please post them on a new thread. Thanks. We are helping the original poster here and it gets confusing when other users throw in off-topic questions (especially when their questions can't be answered, which the 'which is better' ones generally can't as it all depends what is best for your situation, not anyone else's).

Easiest way to answer your question is install Luckybackup and try it out. See if it fits. If not, uninstall. Done. :)

Good luck.

---

### Post by tom-bellas3rd on 2016-02-29
I generally have a backup once a week to my USB drive. I just simply copy my Docs, Pics and music folders and paste into the disk. No backup app needed. At least it works for me. :)

---

### Post by Bucky Ball on 2016-02-29
> **tom-bellas3rd said:**
> I generally have a backup once a week to my USB drive. I just simply copy my Docs, Pics and music folders and paste into the disk. No backup app needed. At least it works for me. :)

I don't have a 320Gb USB stick, and that is just for the laptop! :| :)

---

### Post by 1clue on 2016-02-29
```
cd <backup-dir>
cp -rax ~ .
```

---

### Post by tom-bellas3rd on 2016-02-29
I should mention that I've used Back in Time before, works great.

---

### Post by 1clue on 2016-02-29
Rsync is not good for any sort of automated backup.

Rsync keeps two directory structures in sync, but what if the rsync does its thing after file damage has occurred? Then both copies (probably all copies) are garbage.

Data damage often happens long before you detect the problem.  Sometimes months before.

People backup data for several reasons:
[LIST=1]
[*]Preserve data in case of drive failure.
[*]Preserve data in case of media damage (including something like power fail during write)
[*]Preserve data in case of accidental human event (delete, modification, fat-fingered save, etc)
[*]Preserve data in case of data corruption.
[*]Provide a mechanism to keep system live in the event of data damage (live backup: Switch to backup and you're instantly running)
[*]Distribute data to multiple systems.
[*]Preserve data in case of fire, theft, hacking, other natural and unnatural disasters which cause your computing center to be gone.
[/LIST]

These things are NOT legitimate backup tools:
[LIST=1]
[*]rsync. Does not give history, will happily backup bad data over the top of the only good copy.
[*]raid. Does not give history, not proof against fire or theft or data corruption not related to the disk surface.
[*]Anything where the backup stays in the same building as the original, or which stays online when not in use.
[/LIST]

In order for a real backup, you need to keep several timestamped copies of your data.  In order to have a good backup system, you need those timestamped copies to be frequent enough to get the unpolluted copy which is recent enough to be useful.

Here's what I do:
[LIST=1]
[*]Have several removable media of similar type.  I have an ejectable SATA 3.5" drive bay with several cheap drives, used one at a time the way you use tape cartridges.
[*]Insert a media and mount it.  For example, /mnt/backup.
[*]Create the backup folder (mkdir -p /mnt/backup/<hostname>/<yyyy-mm-dd>/home)
[*]cd <directory you just created>
[*]cp -rax /home/<user> .
[*]And so on for /etc and any other data directory not including files like database files which can't be directly copied while live.
[*]Database files need an internal backup, and then you copy that backup (probably zipped in order to give a checksum for validity) over to your backup media.
[/LIST]

I have been running computer backups since the 80s.  I used floppies, tape drives, CDROM, DVD, all sorts of stuff, both for my personal hardware and for my work.  At one point I actually had to use a backup to restore data, which was educational.  The data did not restore. None of the other backups worked either. A fresh backup with a new tape did not work.  From that point forward I have never relied on hardware or software specifically designed for backups.  No more tape drives or anything like them.  My backups are now larger than a blu-ray so I don't use them either.

I use a plain old script to copy data over to a plain old hard drive, into a new folder based on the date.  Most files are uncompressed because the bare file is fine and searching for it is much easier when it's just another folder on the hard disk. When the drive gets full you delete older backups. I have a two-stage deletion plan where every quarter I leave the folder and delete the next newer copy.  When that drive fills up I store it and buy a new drive.

Some files benefit from compression and checksums.  I zip database backups for example because they are highly compressible and benefit from the checksum.

Most importantly, I make sure the backup works. Not every time I run it, but every now and then I check that I can actually get my data off the backup and use it.  This is trivial with a plain old hard disk and shell commands.

---

### Post by 1clue on 2016-02-29
Sorry to double-tap the thread.  This is critically important.

My process outlined above is the simplest backup mechanism I can devise.  It's the most reliable as well. Like all good backup plans, it relies on both automation (a script and possibly CRON) and on human awareness and cooperation.

One might think a purely automated backup is a great idea, but it's not.  One might think that prepackaged backup software is going to take everything into account, but it can't.

The best backup for any type of information depends on the nature of that information and what you do with it.  Source code or other modified text and images, for example, may be best backed up with an scm like git, which is then backed up in the traditional way. Database backups are best with a zip and some sort of checksum.  Files in /etc are best just copied over IMO.

You, the system administrator, should be aware of and frequently reminded about your backups.  You need to know what's being backed up, when, where and how often.  You need to be reminded because as time goes on you will add some files/directories to your backup and remove others. You need to manage your media, know when each piece was originally brought into service and whether it has drive-level errors.

Some of this can be safely scripted or managed with software.  These parts should be scripted or managed with software.  Other parts need your intervention.

The OP wants a simple backup for the home directory, which is fairly easy to handle with my process.

The biggest cost of a drive failure is not the drive or the backups.  It's the time spent without functionality, because the drive will NEVER fail at a good time.  It always happens during a period of high use, right when you need it.

You have no idea what pressure is like unless you're trying to fiddle with some prepackaged but nonfunctional tape drive while several hundred (or thousand) people are sitting in their chairs waiting for you to get the database back. For me it was a useless tape drive with a four-digit price tag and several hundred people waiting while on the clock. Luckily I wasn't the one who recommended the tape drive.

Storing data in original form (uncompressed on a random access read/write drive) is the easiest way to get the data back during crunch time.  You can get back a single file or an entire tree. You can see in moments if the data corruption exists on any given backup.

good luck and have fun.

---

### Post by mikodo on 2016-02-29
> **1clue said:**
> 
good luck and have fun.
Wow! Educational posts, 1clue.

 May I superimpose on the OP's thread. You, adms/mods can say no! :)
> In order for a real backup, you need to keep several timestamped copies  of your data.  In order to have a good backup system, you need those  timestamped copies to be frequent enough to get the unpolluted copy  which is recent enough to be useful.
Would you consider rdiff-backup sufficient for this, with more than one syncing backup copy to different sources?
> I use a plain old script to copy data over to a plain old hard drive, into a new folder based on the date.
Would share that script for we trying to learn?

---

### Post by 1clue on 2016-02-29
> **mikodo said:**
> Wow! Educational posts, 1clue.

 May I superimpose on the OP's thread. You, adms/mods can say no! :)

Would you consider rdiff-backup sufficient for this, with more than one syncing backup copy to different sources?


No. You can still easily trample every copy with bad data.  The rdiff/rsync backup only gives you an up-to-date copy of another directory.  This is good for duplication of good data, not for backup.

***Edit: **The point is that you need backups every so often (once a day, once a week, whatever) and you need to keep those backups. If a file is damaged or lost, the rsync backup cannot help you. You need to travel back in time to before the damage happened.*

> 
Would share that script for we trying to learn?

I don't think my script would be helpful.  It's literally the commands I would type to do it manually, and that would vary wildly based on what data you want to save.  The **cp -rax** is literally what I use.  It runs as root.

I use commands like this:
```

TS=date +%Y-%m-%d-%H-%M-%S
DBBAK="/var/db/backups"
BACKUP="/mnt/backup/$HOST/$TS"
mkdir -p $BACKUP
cp -rax /home $BACKUP/home
tar -czf $DBBAK/mydb1.bak $BACKUP/$DBBAK/mydb1.tgz

```

Unlike my first cp -rax post, I don't actually change directories to the destination.

I add only code which is necessary for the job to get done.  I try to make my code self-explanatory for easy maintenance.  I keep it on a private git repository to track changes and I back that up as part of my backup.

I do not backup anything that comes from the Ubuntu repository or any other public repo.  All it does is waste space and will probably be obsolete by the time I need it anyway.


One thing I did not mention is live bootable backups. This can be done with rsync if you're careful, but this sort of backup does not replace the need for the sort I'm describing. For this you need to copy the entire operating system, excepting special directories like /dev and /proc and /sys which only exist in RAM.

---

### Post by sammiev on 2016-02-29
> **ra7411 said:**
> I've been using Grsync. Is [COLOR=#000000][I]Luckybackup better, how does it differ?
[/I][/COLOR]

Hi, I never tried Grsync.

I use Luckybackup because it fits my needs.

People should use what works for them. :)

---

### Post by mikodo on 2016-02-29
> **1clue said:**
>  - What you wrote -

Thank you!

---

### Post by 1clue on 2016-02-29
> **sammiev said:**
> Hi, I never tried Grsync.

I use Luckybackup because it fits my needs.

People should use what works for them. :)

+1 for using what fits your needs.

The big problem is deciding what those are with a clear head. My opinions on this are based on prior experience and those of my associates.

> **mikodo said:**
> Thank you!

No problem!

---

### Post by Geoffrey_Arndt on 2016-03-02
OK, I'll ask the obvious (which I believe hasn't been referenced so far . . ?) . . . . what about the official Ubuntu desktop preferred backup tool (Deja-Dup)?   

Are we saying it doesn't work, or is in some way substantially inferior to other apps such as Back-in-Time or Lucky?   

My main concern is not speed (an extra 5-10 minutes to do is not a game changer), . . . . but reliability of copy/compress/encrypt, and ease of restore.   

And, . . . . if Deja-Dup (duplicity) isn't suitable for average home or small business user, why would Canonical select it versus Lucky or Back-in-Time?

**EDIT**:   I just went back and looked at the original post comments . . . and noticed where Deja-Dup is said to only copy the same files over & over (versus adds, changes, deletes)?   Is that correct . . is that the experience of other users also?

---

### Post by Bucky Ball on 2016-03-02
Yes, deja dup. And for that matter, what about Simple Backup Suite (sbackup). You can find it in the repositories.

---

### Post by Geoffrey_Arndt on 2016-03-02
Thanks Bucky . . . my 1st preference is always to try the simplest method first, and move to more comples/capable IF or AS needed only.   So, am testing backups to a local Dropbox folder.  I have one labelled "Selective_Backup_A", and another labelled "Selective_Backup_B".   The A folder will be used for the Deja_Dup backups, the B folder will be for Simple Backup Suite (which seems similar to Back-in-Time).   Folder A is encrypted, Folder B is partially encrypted.

Anyway, I'll try both on a set schedule of 15 days.   My backup files are likely MUCH smaller than many typical users here at Ubuntu Forums, as the only thing I'm really concerned about are the important docs in my home directory and maybe a couple hundred audio files, and fifteen to twenty video files.    System config files (such as found in etcee (.etc)) . . . are not critical to me as I run a pretty standard/vanilla Unity DE, and customizing a new install takes about 60 to 90 minutes tops (once every two or three years).   I have two PROD machines (production) and four TEST (play) machines.   The Test machines not really backed up - - except for one directory on critical apps.

Again, thanks for the info . . maybe if the OP is still following this thread, he/she will take a look at these suggestions also (btw . . . am doubting Deja-Dup not capable of delta-backups as suggested in first message of this thread).

G

---

