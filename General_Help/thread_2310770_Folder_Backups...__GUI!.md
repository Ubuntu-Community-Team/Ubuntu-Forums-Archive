---
title: "Folder Backups...  GUI!"
date: 2016-01-21
forum: General Help
---

### Post by Kris_M on 2016-01-21
I use Clonezilla for partition images and it has saved me a ton of pain!  But I would not be able to use it to grab an old copy of a file. At least not easily!!!

I searched the forums but it didn't turn up much.
I googled but got a lot of terminal command line apps - I want a gui pgm.

A month ago when I installed 14.04.3 Unity I turned Backups(deja) on to backup once a week.  I finally got around to looking at the 23GB(so far) result and found that it's very hard to find a particular file in there.  googled and tried the "restore missing files" thing on both Pictures (screen shots, etc) and Downloads, both of which have seen a lot of traffic, and both of which I have just cleaned, and it found NOTHING.  Okay, I was warned that it was not reliable.  it was non-functional for me. Always test stuff before you need it!!!

I did install BackInTime last night and took a snapshot of my /home/<name> and it created what looked like a copy of my stuff in which I could easily find a folder or file as it is set up exactly like the real folders.  i understand that is incremental, though I do not know how it will react if i do a Clonezilla restore in the middle of time at some point (which I have many times), but at least I can find stuff, though restoring it is quite manual (click, copy, paste)(not a big deal)

So the question is , is there a better gui backup for my /home/<name> stuff, so I can easily find and restore some file if need be? (remember, I spent my life on windows...)

I am getting to the point where I have nearly all my stuff off my win7 boot and this is the next thing I think of (used Easeus and Acronis TrueImage on Win) - need a way to grab an old copy of my passwords, or some such. :)

Thanks!

---

### Post by tea for one on 2016-01-22
Good morning

Have a quick look at grsync, which uses a GUI for the powerful rsync utility.

Please download it from the Software Centre or via Synaptic.

[http://www.opbyte.it/grsync/](http://www.opbyte.it/grsync/)

---

### Post by abhijit-ghosh on 2016-01-22
HI,
You don't need to run away from command line. Learning it gradually will make life easier. It should not be that hard.
'**rsync**' is a powerful tool for backing up data. It can be used to create backup of your entire home directory or anything(data) you want, preserving the directory structure.
You simply need to open a terminal and run the command in the following way:
[COLOR=#008000]
=======================================================[/COLOR]
$[COLOR=#0000cd]rsync -a /home/<user_name>/   /media/external-hard-disk/backup-directory
[/COLOR][COLOR=#008000]=======================================================[/COLOR][COLOR=#0000cd][/COLOR]



Explanation:
**rsync** is the tool itself
**-a** is an option of rsync which means **archive mode**
**/home/<user_name>** is your home directory **(SOURCE)**
**/media/external-hard-disk/backup-directory** is the path to your external hard disk folder where you want to keep the backup **(DESTINATION)**

Note: Notice the trailing slash (/) at the end of the SOURCE path. You should do it exactly the same way, i.e. (/) at the end of SOURCE path or you will end up having a sub-directory with the name of source directory in side the DESTINATION path.




For Restoring the backup you just need to interchange the SOURCE and DESTINATION paths like:
$[COLOR=#0000cd]rsync -a  /media/external-hard-disk/backup-directory/   [COLOR=#0000cd]/home/<user_name>[/COLOR][/COLOR]

[COLOR=#ff0000]However I would like to discourage you from restoring entire home directories from such a backup since the home directory **(/home/<user_name>)** contains many hidden files and folders which are important, but the current ones in your home directories are the ones that should be there in your home directory and should not be replaced using old backups.[/COLOR] 

For avoiding such pitfalls you can rsync options like --exclude
Alternatively you can keep all your data within one master directory within your home directory and use that path to backup-restore using rsync like:

Backup:
$[COLOR=#0000cd]rsync -a /home/<user_name>/some-directory/   /media/external-hard-disk/backup-directory[/COLOR]

Restore:
$[COLOR=#0000cd]rsync -a   /media/external-hard-disk/backup-directory/[/COLOR] [COLOR=#0000cd]/home/<user_name>/some-directory[/COLOR]




You should test it out using some dummy folders first before going for the actual backup to get a hang of it. Its's simple.

--------------------------



Now if you want to automate this task at a regular set interval (like daily or weekly, etc.) you can add the same command in a simple shell script and run that script from your crontab.

Tell me if you would like to know how it is done.



And if you really want to stick to GUI then the GUI front-end GRSYNC as suggested by [**[COLOR=#000000]tea for one[/COLOR]**]("http://ubuntuforums.org/member.php?u=585392") should do the job well for you.

Remember GRSYNC is a GUI front-end of **RSYNC** only.

:)

---

### Post by Bucky Ball on 2016-01-22
I use Lucky Backup myself. Sounds like a toy, and it looks simple enough with its simple GUI, but it is a fairly powerful little monkey. It's in the repos. I do regular backups of important files with it. Next backup it only saves/changes anything that's new or has been changed so it's only the first backup that takes awhile.

Quick and easy and you can browse the backed up files as you would any other. It basically copies the files to another partition/folder as is. No compression, no changes.

---

### Post by Kris_M on 2016-01-22
> **Bucky Ball said:**
> I use Lucky Backup myself. Sounds like a toy, and it looks simple enough with its simple GUI, but it is a fairly powerful little monkey. It's in the repos. I do regular backups of important files with it. Next backup it only saves/changes anything that's new or has been changed so it's only the first backup that takes awhile.

Quick and easy and you can browse the backed up files as you would any other. It basically copies the files to another partition/folder as is. No compression, no changes.

I tried Lucky but it says my target (an ntfs partition and folder) is not mounted - usually I can mount it just by clicking on the disk which pops up the files, but this time no go...  I know, that's a romper-room question...  Also do I use regular or super user version?  Huge thanks for looking in!!!!! :D

GRSYNC is running - I want to see what it looks like

command line stuff - I am great for typos and my eyesight is not that great...

Thanks all!!!


EDIT: don't play with Firefox while you're backing up "file has vanished: "/home/kris/.cache/mozilla/firefox/g68z2x8r.test/cache2/entries/5D66973C8E7D8D87B344F29C65A5CE42F75DA465"
rsync warning: some files vanished before they could be transferred (code 24) at main.c(1183) [sender=3.1.0]
Rsync process exit status: 24"  LOL  :D:D:D

---

### Post by Kris_M on 2016-01-22
GRSYNC didn't back up my links (I noticed 3 (playonlinux and 2 others) (though the stuff was there in .wineprefix)\
This raises another whole question - how do I restore it? Just a copy paste? and does that keep the owner and permissions?
Or should I be backing up to an ext4 partition???

---

### Post by Nuno_Abreu on 2016-01-22
> **Kris_M said:**
> GRSYNC didn't back up my links (I noticed 3 (playonlinux and 2 others) (though the stuff was there in .wineprefix)\
This raises another whole question - how do I restore it? Just a copy paste? and does that keep the owner and permissions?
Or should I be backing up to an ext4 partition???
Yes, because links are not supported on Windows partitions, if that is the case.
You better use an ext4 partition for that, and there should be no problem.

Just a quick note: I normally use rsync to backup my files on a different hard drive - this little program is so neat that you can even backup an entire operating system, with the option of excluding the folders/files you want.
Here's the command I normally type.

```
rsync -av --progress /home/<username>/ /media/destination
```

With this command, it shows the transfer progress, which can be handy - careful if the destination folder/drive needs root privileges. Use sudo for that.

---

### Post by Kris_M on 2016-01-22
I seem to have settled in on BackInTime which has incremental backups, and uninstalled deja.

Thanks to all!!!!!

---

### Post by sammiev on 2016-01-22
> **Bucky Ball said:**
> I use Lucky Backup myself. Sounds like a toy, and it looks simple enough with its simple GUI, but it is a fairly powerful little monkey. It's in the repos. I do regular backups of important files with it. Next backup it only saves/changes anything that's new or has been changed so it's only the first backup that takes awhile.

Quick and easy and you can browse the backed up files as you would any other. It basically copies the files to another partition/folder as is. No compression, no changes.

1st time running the above program.

Many Thanks!

---

### Post by Kris_M on 2016-01-22
Couldn't get it to go...  :(

---

### Post by Bucky Ball on 2016-01-23
> **Kris_M said:**
> Couldn't get it to go...  :(

Lucky Backup? Sounds like the only thing that didn't happen was it mounting the partition on launch. Mount the partition then launch Lucky Backup. That's it. That's what I do. I have an external eSATA connected drive I backup to which needs to be manually mounted. All my targets in Lucky Backup are folders on the eSATA drive.

Don't know if it helps, but I just created a mountpoint in /mnt:

```
sudo mkdir /mnt/backup
```

Then run:

```
sudo blkid
```

... to find the partition you're after. Say if its /dev/sda5, then:

```
sudo mount /dev/sda5 /mnt/backup
```

There you have it. Point your targets to folders on the /mnt/backup partition. Just mount the partition to /mnt/backup when you want to backup or use a partition that is mounted 'automagically' when you plug in the device.

I wondered when you mentioned it why the partition you want to use was not mounted already when you plugged it in. What's with that? Having problems mounting USB devices automatically or some such?

---

### Post by Kris_M on 2016-01-23
> **Bucky Ball said:**
> Lucky Backup? Sounds like the only thing that didn't happen was it mounting the partition on launch. Mount the partition then launch Lucky Backup. That's it. That's what I do. I have an external eSATA connected drive I backup to which needs to be manually mounted. All my targets in Lucky Backup are folders on the eSATA drive.

Don't know if it helps, but I just created a mountpoint in /mnt:

```
sudo mkdir /mnt/backup
```

Then run:

```
sudo blkid
```

... to find the partition you're after. Say if its /dev/sda5, then:

```
sudo mount /dev/sda5 /mnt/backup
```

There you have it. Point your targets to folders on the /mnt/backup partition. Just mount the partition to /mnt/backup when you want to backup or use a partition that is mounted 'automagically' when you plug in the device.

I wondered when you mentioned it why the partition you want to use was not mounted already when you plugged it in. What's with that? Having problems mounting USB devices automatically or some such?

Thanks! Yeah I was getting a mount problem but now I just get this

[http://ubuntuforums.org/showthread.php?t=2310890](http://ubuntuforums.org/showthread.php?t=2310890)


> I have googled but can find nothing.  I get the message
and can not figure out how to get rid of it.
" status: [COLOR=#0000ff]NOT INCLUDED[/COLOR]
Checks are disabled. This task will be skipped"        

---

### Post by Bucky Ball on 2016-01-23
Silly question, but is there a tick next to the task? This message is saying something about the task not being included in the backup job. Make sure it has a valid source and target and is ticked to include in the job, then tick 'Dry' for a dry run then 'Run'.

[This page]("http://www.linux.com/learn/tutorials/322632-easy-linux-backup-with-lucky-backup") might give you some tips. There are lot of how tos regarding the use of Lucky Backup.

---

### Post by Kris_M on 2016-01-23
> **Bucky Ball said:**
> Silly question, but is there a tick next to the task? This message is saying something about the task not being included in the backup job. Make sure it has a valid source and target and is ticked to include in the job, then tick 'Dry' for a dry run then 'Run'.

[This page]("http://www.linux.com/learn/tutorials/322632-easy-linux-backup-with-lucky-backup") might give you some tips. There are lot of how tos regarding the use of Lucky Backup.

it was not - when you check the box it says this (see pic)

Never mind - it's working now - you must have scared it!!!  LOL  :D

---

### Post by Bucky Ball on 2016-01-23
In your first picture, your destination folder doesn't exist. Use one that does. Secondly, I wouldn't backup /home. Lucky can do that, but that will backup EVERYTHING on /home. This will include all settings, folders and files, hidden and otherwise. 

I generally backup specific folders of value and clone the whole / or /home partition with other software if I want to back them up. Up to you either way (but I would at least tweak the settings so you don't backup system files/folders (i.e. hidden).

Incidentally, where is /work1??? On another partition or device?

---

### Post by Kris_M on 2016-01-23
I didn't look at what it was saying this time - it worked. Maybe putting work1 in fstab helped things. Took 4 minutes.

I backup /home/kris   "kris" is just the name of the job.  I back it up to /work1/luckybackup .
Will this do incremental backups or full backup each time?

---

### Post by Bucky Ball on 2016-01-23
In your second screenshot you want to tick all of those boxes. You don't need to backup that. 

Go to the 'Command Options' tab and make it look like the attached screenshot (but adjust for your preference, e.g. you might not be backing up to a FAT/NTFS partition ... if not, untick that). The important part is that you have 'Recurse into directories' ticked and make sure that 'Delete files on the destination' is NOT ticked (after you've done the first backup definitely ticked, no matter on first to an empty folder).

---

### Post by Kris_M on 2016-01-23
I've already backed up system - how do I delete all that?

Actually there's no system in /home/kris so I'm fine.


So...  GOT IT!!!  THANKS!!!  :D

---

