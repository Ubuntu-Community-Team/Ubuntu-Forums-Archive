---
title: "How do you backup your pc?"
date: 2007-12-28
forum: General Help
---

### Post by RudolfMDLT on 2007-12-28
Hello!

How do you backup your pc? I have tried many things over the last year or so and nothing really works.... :confused:

Things that I have tried:

1) Backup over network by VIA samba, standard copy and paste home folder and mp3's - had 2 to problems with this, i) when the copy couldn't access something in the home folder it would stop and wait for me to click skip, putting a 4 hour copy on hold and also, ii)it never copied everything - It would create the folder structure first and then randomly not fill certain directories(this was using KDE's konqurer though - as far as I know gnome would fill the folders). I've lost about 150+ mp3's like this.

2) Using SambaFS to mount a network folder - Same result

3) Setting up an FTP server and doing the backup over FTP - This worked okay but I can't get the bloody FTP server to work with my new gusty server(I think the first time I got  it to work was pure luck :) ) and also you are relying on the copy thing and have to keep babysitting the backup.

3) Using Secure Copy(scp) - this works the best so far but I have to recopy EVERYTHING everytime that I want to do a backup and I like the verbose flag.

3) SSHFS - as far as network folder mounting goes this is the quickest and easiest to use as far as I have seen - though when copying you still get the "skip" dialog.

4) Ubuntu's native simple backup - this program I tried at first but once it starts you can't stop it and I just don't like the way it works, maybe I'm not using it right? How have you found simple backup?

5) Grsync - I like this. I do a network mount using sshfs and then have grsync update my backup. I can't get grsync to load a saved backup config, that is one backup config for home folder, one for mp3's ect... Though I like that fact that it gives you feed back and a report at the end. You sort of have to have faith in simple backup and as far as backups go I'd like to see the money!

With all the above I have had varying degrees of inconsistencies and problems - though Grsync really has made life a lot easier - it broke today so I'm busy hunting down that problem.

I don't need specific help on anything - I'm just looking for advice on what you guys are using to backup your systems - Maybe I've missed a new app or there is some obviously better way to do what I'm currently doing: Backing up large amounts of data weekly to a backup server running Ubuntu. 

Please post ANY advice that you may have!

Thanks in advance,

Rudolf

---

### Post by LaRoza on 2007-12-28
Disk imaging with Clonezilla. See the link in my sig.

You can image an entire disk or partition and restore it of any format.

Not sure if you want that.

For data, I do periodic burns to disks.

---

### Post by Zack McCool on 2007-12-28
Rsnapshot is my preference.  I use an external USB harddrive and backup all important system files and my home directory.  It is highly configurable, and maintains several days worth of exact copies of the info you want.

For my MP3's, Photos (and an extra copy of my home directory), I use rsync to maintain a synced copy on a NAS drive in my living room, near the front door of the house.  If there is ever a fire or other emergency, I can grab it on the way out of the house to be sure that I don't lose anything important.

---

### Post by ajgreeny on 2007-12-28
Backup of home folder with an external usb drive and grsync, which I also like.  Dead easy and very quick after the first backup.  I just use the default settings and it works beautifully, backing up everything.  I have never bothered with a complete backup of the whole OS as it seems so quick and easy with my system to just do a reinstall.  I even use aptoncd to make an iso file of everything in my /var/cache/apt/archives which I keep in home, so I can even add all the things I want easily without downloading them all again.

---

### Post by RudolfMDLT on 2007-12-28
Thanks guys - if anybody else has something to add please do!

@ajgreeny 
I backup the apt-cash too! saves a lot of time when you have to reinstall. +1 Rsync

@Zack McCool
> For my MP3's, Photos (and an extra copy of my home directory), I use rsync to maintain a synced copy on a NAS drive in my living room, near the front door of the house. If there is ever a fire or other emergency, I can grab it on the way out of the house to be sure that I don't lose anything important.
Thats kinda cool, and both your methods are based on rsync

@LaRoza
I don't think I'll be using clonezilla for weekly backups, but I'll definitely give it a shot next time I upgrade. I used to use PartImage on the system rescue CD but clonezilla seems to be a bit more user friendly. Thanks

Thanks guys, it seems that as far as reoccurring "copy" based backups go rsync is the best to use... Also, it seems I have a networking issue rather than a back up app issue. 

I would appreciate more comments and advice if anybody's willing to give! :)

Thanks,

Rudolf

---

### Post by der_joachim on 2007-12-28
I have written a bash script that mounts an encrypted USB hard drive, and it uses rsync to synchronize my /etc and my /home. That way, even if I somehow lose my external HDD, my data is reasonably secure. Of course, I store the backup medium in another room than my PC and laptops. :)

---

### Post by fjgaude on 2007-12-28
I use Unison to backup my laptop and desktop, because it's two-way... has nothing but reliablity. I also use Grsync to backup desktop to another machine. Both work without error over the years.

---

### Post by SOULRiDER on 2007-12-28
I have my Os in one drive and all my files in another.. so I dont really do backups, horribly unsafem i know...

... im just too lazy :P

---

### Post by Zill on 2007-12-28
> **RudolfMDLT said:**
> 
4) Ubuntu's native simple backup - this program I tried at first but once it starts you can't stop it and I just don't like the way it works...
Rudolf
Why would you want to stop a backup before it has finished?  SBackup works fine for me and runs automatically every day, saving to a backup partition on a different PC via NFS.

---

### Post by RudolfMDLT on 2007-12-28
> **SOULRiDER said:**
> I have my Os in one drive and all my files in another.. so I dont really do backups, horribly unsafem i know...

... im just too lazy :P

Drive or Partition? There is a BIG difference, a difference you'll only understand/appreciate when the physical drive goes and EVERYTHING disappears...

@Zill
I used simple backup and the deskbar search utility when Ubuntu was freshly installed. i am very in touch(full of crap) with my system and I'm aware when it's unhappy. Deskbar and the backup utility slowed down my pc, also I like having a report confirming the "belief" that the backup did happen according to plan - something running in the background without logs made me very unhappy. Also it never really did work, and over the last month having run multiple app's I have found the network to the backup server to be unstable, not so much the actual applications. The fact that all the apps mentioned so far work for the people that mentioned them and the fact that when I try them I find them useless or non-consistent points to a fault which lies beyond the app - either myself or the network.

---

### Post by Zill on 2007-12-28
> the backup utility slowed down my pc

I would guess that **most** backup utilities will slow things down!  I schedule mine for the middle of the night along with all the other Linux housekeeping so this is never a problem.  You can always kill the SBackup process if it is necessary to stop the backups manually.

I doubt that any backup system will work correctly if your networking is unreliable.

---

### Post by Irihapeti on 2007-12-28
I use TAR to backup my system, as described here:
[https://help.ubuntu.com/community/BackupYourSystem/TAR](https://help.ubuntu.com/community/BackupYourSystem/TAR)

I divide the system into several files, so that none of them is too huge. Not having an external hard drive or USB stick, I write the archives to DVD. Once I've done the initial backup, I can do incremental backups quite easily. I've written a script which fairly well automates the whole process.

Restoring a whole system by first doing a reinstall (I'd made a mess of GRUB) and then unpacking the archive was straightforward.

---

### Post by RudolfMDLT on 2007-12-28
> **Zill said:**
> I would guess that **most** backup utilities will slow things down!  I schedule mine for the middle of the night along with all the other Linux housekeeping so this is never a problem.  You can always kill the SBackup process if it is necessary to stop the backups manually.


When I do a backup manually in Ubuntu I can watch it and am aware of it, with simple backup I had random system slow downs and had to go hunting for the process and kill it. As I said, I like to have a report and I like to be aware of the system slowing down or  that the backup is active.

> 
I doubt that any backup system will work correctly if your networking is unreliable.

I agree, even though I've been using Ubuntu for almost 2 years, there are still some things that when they break, I really hit a brick wall and cannot get past them. The network seems to work when I test it, but as soon as I want to do a backup or something critical, the third part of the holey trinity - Murphy - steps in and then I get all kinds of errors: from write permissions to files just being skipped, to sshfs bombing out.

I'll start a thread on my networking issues as soon as they holiday season is over and I can actually concentrate on my home network. At the moment I just need to find a backup-system that multiple people in the community agree with and then from that point on I can work to create a network that works. 

I have to say that gusty has made life a little more difficult than edgy and that especially my networking was a whole lot more peaceful than with gusty.

Thanks for all the replies guys and also the constructive criticism, please keep it coming! ;) 

thanks,

Rudolf

---

### Post by ajgreeny on 2007-12-28
Just out of interest, and as a follow up to my earlier posts in this thread, I should add that one or two folders of mp3 and ogg files from ripped CDs would not transfer from source to backup.  After some searching I found it to be files that had commas, apostrophes, and a few other punctuation marks in the automatically made file name.  I don't know if there is any way to overcome this problem so I just did it by manually renaming the files to get rid of the offending punctuation.  All was then OK.

---

### Post by SOULRiDER on 2007-12-28
> **RudolfMDLT said:**
> Drive or Partition? There is a BIG difference, a difference you'll only understand/appreciate when the physical drive goes and EVERYTHING disappears...

@Zill
I used simple backup and the deskbar search utility when Ubuntu was freshly installed. i am very in touch(full of crap) with my system and I'm aware when it's unhappy. Deskbar and the backup utility slowed down my pc, also I like having a report confirming the "belief" that the backup did happen according to plan - something running in the background without logs made me very unhappy. Also it never really did work, and over the last month having run multiple app's I have found the network to the backup server to be unstable, not so much the actual applications. The fact that all the apps mentioned so far work for the people that mentioned them and the fact that when I try them I find them useless or non-consistent points to a fault which lies beyond the app - either myself or the network.

Different drives, not partitions. If i lost my data i would be frustrated but its not a life or death issue. If i loose it its too bad, i can live, but that doesnt mean i want it gone :P

---

### Post by ASquared21 on 2007-12-28
Hi,
I would suggest using an external hard drive as your primary storage drive.  That way, if Ubuntu crashes, you still have your files. You can probably change your program to save to the external hard drive by default.

---

### Post by ASquared21 on 2007-12-28
Hi,
Plus, you could do a complete reinstall without losing files.

---

### Post by Zack McCool on 2007-12-28
> **RudolfMDLT said:**
> 
Thats kinda cool, and both your methods are based on rsync


The huge advantage to rsync is that it only copies changed files.  It also employs compression during the data transfer, where possible, to speed things up.

rsnapshot is more useful for working directory backups, as you have the ability to go back a day, a week, a month, or whatever (depending on your config).  I do one backup per day, and keep one per day for the last week, one per week for the past month, and one per month for the past year.

I also exclude anything large, like iso, img, avi and mpg.  I spent time getting those videos, but they are not that important, and if I lose them I can get them again.

There is no point, IMO, in backing up a full system in linux.  Make sure you have all of your personal data, and all of your configuration files (fstab, samba config, exports, /home/. files, and so on).  Also, maintain a list of installed packages:

```

dpkg --get-selections | grep -v deinstall > packages

```

That way, if you need to rebuild, the process is simplified...

Install the OS, then restore your packages:

```

sudo apt-get update
sudo apt-get dist-upgrade
dpkg --set-selections < packages
sudo dselect

```

Type &#8216;I&#8216; and allow dselect to install of the the packages listed in your packages document. When it&#8217;s finished, type &#8216;Q&#8216; and hit the ENTER key to exit dselect.

Then, just restore your config files and data, and reboot.  Your system should be pretty damned near where it was (IOW: Exact...   ;) )

---

### Post by gimmy_bond on 2007-12-29
I have two questions please.

1. which bkup App is recommended to backup onto the DVD drive on the laptop.
2. Is there any way someone could guide us the "windows refugees", how to accomplish it through gui commands. It would be very helpful

---

### Post by Irihapeti on 2007-12-29
gimmy_bond:
As far as I'm aware, there isn't a nice, all-in-one GUI program that will backup your files to DVD in the way that, say, Nero Back-it-up does on Windows. I've only been using Ubuntu (or any kind of Linux) for five months, so I think I know where you are coming from. 

As I see it at present, you can use the Archive Manager to create an archive of the files you want to backup, and then use a DVD-writing program, such as Brasero or K3B, to get the archive onto a DVD. And, yes, I think it's a bit fiddly doing it that way. That's why I wrote a script.

The only write-to-DVD program I've encountered is Cedar Backup. It's in the repositories, but probably not the latest version. It's command-line, and needs to have an XML config file set up, but the documentation is quite thorough in explaining how to do it.

I realise this doesn't really answer your question. Maybe someone else knows about a program that will do what you want.

---

### Post by Zill on 2007-12-29
gimmy_bond:  I suggest you give SBackup (Simple Backup) a try.  This is a very good GUI backup app that should already be installed and runs in the background.  It does not report on progress or completion but you can always take a look at the backup location if you wish to check.

Once SBackup has completed you can burn the archive to a DVD in the usual way (eg Nautilus or K3B etc).

Lots of user guides to SBackup can be found via Google but [this link]("http://maketecheasier.com/backing-up-data-in-ubuntu-using-sbackup/2007/12/08") seems to show the main info.

---

### Post by MangasColoradas on 2007-12-29
I have just tried Sbackup to backup to another hdd, it IS nice and simple to do.

Is there anything that would back up my settings? So, if I do something stupid to Ubuntu I can restore it to an earlier time-a bit like MS system restore?

---

### Post by MangasColoradas on 2007-12-30
Could I just back up root?

---

### Post by Zill on 2007-12-30
MangasColoradas:  Settings for each user are held in each /home/user directory.  Most systemwide settings are held in the /etc directory.  By default, SBackup saves /home, /etc, /var and /usr/local so all settings will automatically be backed up.

Just make sure the backup archive is saved to DVD or somewhere else other than your HDD ;-)   Unfortunately, the SBackup default save location is /var/backup - which isn't much help if your HDD crashes!

If you need to restore everything then simply reinstall Ubuntu from the CD and then restore all your data and settings via SBackup.

---

### Post by sefs on 2007-12-30
Partimage to back up each partition

dd to back up the partition table and extended table.

---

### Post by MangasColoradas on 2007-12-31
> **Zill said:**
> MangasColoradas:  Settings for each user are held in each /home/user directory.  Most systemwide settings are held in the /etc directory.  By default, SBackup saves /home, /etc, /var and /usr/local so all settings will automatically be backed up.

Just make sure the backup archive is saved to DVD or somewhere else other than your HDD ;-)   Unfortunately, the SBackup default save location is /var/backup - which isn't much help if your HDD crashes!

If you need to restore everything then simply reinstall Ubuntu from the CD and then restore all your data and settings via SBackup.

Ok, cool. I backed up to another hdd, I agree the default save location for Sbackup is not good!

I have root/home/swap, so I would re-install root and leave home intact if I mess up the OS? And use Sbackup if I have a hdd problem? I am a total noob, sorry.

Thanks.

---

### Post by Zill on 2007-12-31
MangasColoradas:
> I have root/home/swap, so I would re-install root and leave home intact if I mess up the OS? And use Sbackup if I have a hdd problem?

That's the theory... :-)

---

### Post by CanonKen on 2007-12-31
[I use this]("http://ubuntuforums.org/showthread.php?t=613462"), had to restore a couple of times when I've messed thing up and its worked a treat

---

### Post by MangasColoradas on 2008-01-01
OK, thanks guys. :)

---

### Post by gimmy_bond on 2008-01-03
Irihapeti
thanks for the suggestion. However my issue is the DVD drive will not mount blank dvd's, even  made by TDK. I have tried it with several blank disks to no avail..

---

### Post by Zill on 2008-01-03
gimmy_bond:  As I suggested in my post #21 earlier, you should be able to use either Nautilus (Ubuntu/Gnome) or K3B (Kubuntu/KDE) to burn a blank dvd.

If you are unable to burn a dvd with these tools then I suggest you note exactly what happens and then check the forums and/or Google to see if anyone else has the same problem and, hopefully, a solution.  It will also be useful if you identify exactly the make and model of your dvd burner.

If no solution can be found then post a new query back to [http://ubuntuforums.org]("http://ubuntuforums.org")

---

### Post by Techwiz on 2008-01-04
A little program called QuickStart. I would recommend it. You can get it [_[COLOR="Blue"]here[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=613462").

---

