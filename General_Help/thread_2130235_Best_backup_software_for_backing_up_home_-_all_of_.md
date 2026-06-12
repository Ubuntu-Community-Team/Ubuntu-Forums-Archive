---
title: "Best backup software for backing up /home - all of it"
date: 2013-03-28
forum: General Help
---

### Post by dc41 on 2013-03-28
I recently upgraded from 10.04 LTS to 12.04 LTS and SimpleBackup is no longer working. It looks like it is no longer supported or in development, so I'm looking for a new backup solution.

The server is mainly used as a samba file server. Each user has a folder in the /home directory, so I need to back up the entire /home directory to a NAS (network attached storage) device via ftp. Can someone recommend a program that supports:

-simple to use (I don't need enterprise level power)
-automatic backup (scheduled) 
-root access (so that all the files in all the /home folders can be backed up)
-ftp access to the remote backup location
-GUI (I'm no good with the command line)
-deleting of old backups

SimpleBackup used to handle all of this just fine. It's a shame it's no longer being supported.

Any help would be greatly appreciated. 

Thanks!

---

### Post by slickymaster on 2013-03-28
Personally I use[ Déjà Dup]("https://launchpad.net/deja-dup"). It is a front end to duplicity that performs incremental backups, where only changes since the prior backup was made are stored. It has options for encrypted and automated backups. It can back up to local folders, Ubuntu One, Amazon S3, or any server to which nautilus can connect. Integration with Nautilus is superb, allowing for the restoration of files deleted from a directory and for the restoration of an old version of an individual file.

---

### Post by dc41 on 2013-03-30
Thanks for the reply. I've played around with Deja, but I can't figure out how to get it to operate as root so that it can backup all the folders in /home. Also, I don't see a place to enter the password for ftp access.

Any help would be appreciated.

Thanks!

---

### Post by slickymaster on 2013-04-01
Sorry for the late reply but I took advantage of Easter time to take a few days off.

Initially when you ran Déjà Dup under your own account there are a number of (system) files that don't back up successfully due to a lack of permissions.
Déjà Dup needs to be set up for the root user. You can either do this by logging in as root if you've enable such a login or if you haven't made it, use **gksu** as follows to configure the storage location:
```
gksu deja-dup-preferences
```
Then add/remove directories as you require.

You can find some good pointers [here]("http://www.howtogeek.com/108869/how-to-back-up-ubuntu-the-easy-way-with-dj-dup/") and [here]("http://heavygauge.blogspot.pt/2012/11/backing-up-ubuntu-using-deja-dup-inc.html").

---

### Post by lonnys on 2013-06-13
I think the thing I dislike about Deja-Dup/Duplicity is the reliance upon python and incremental backups. All the backup programs out there all start off saying "We are different. We use *incremental* backup techniques for faster backups with less storage". And I always wonder, "different from whom?", because I'd sure like to use the other program out there somewhere that basically just makes a copy of various directories "as is" and puts them on my network drive in a folder by date.

It's a bash challenge for me, most likely, and one I've yet to find a good answer for. I'd think some basic script that can run as root under cron would be more than sufficient. But when I try to Google this stuff, I come across tons of tutorials on using GUI apps like Deja-Dup and chest-beating about the benefits of incremental backups. Or how important it is to back up the whole system or partitions (I fail to ever see why).

I'm not an enterprise; I'm a home user with other users on our main Ubuntu machine. Twitter isn't collapsing here. I just occasionally need to quickly restore a file I (or someone else) didn't mean to delete. Or to go back to a prior version of it. A simple directory of dates on the network drive with a folder tree under them is more than enough. If my $89 2Tb hard drive ever runs out of room, I'll either upgrade, or delete a few months or years of super-old stuff I don't need anymore. 

Incremental, shmecremental.

---

### Post by markbl on 2013-06-14
> **lonnys said:**
> 
I'm not an enterprise; I'm a home user with other users on our main Ubuntu machine. Twitter isn't collapsing here. I just occasionally need to quickly restore a file I (or someone else) didn't mean to delete. Or to go back to a prior version of it. A simple directory of dates on the network drive with a folder tree under them is more than enough.
Have a look at rsnapshot which is in the standard packages. It is essentially a perl script over rsync which creates a "virtual" incremental set of snapshots using hard-links so although the snapshots look like full copies they only use minimal incremental disk space. I have used it for many years from a daily cron job to back up the important directories from my linux box(s). I also pull directories from my wife's windows pc simply by installing deltacopy there (free windows rsync server).

---

### Post by BBQdave on 2013-06-14
> **dc41 said:**
> I recently upgraded from 10.04 LTS to 12.04 LTS and SimpleBackup is no longer working. It looks like it is no longer supported or in development, so I'm looking for a new backup solution.

Perhaps this is too basic, but I manually back up to a portable hard drive, home ftp file server, and DVD.

**1**  Depending on the project I am working on, I back up - copy over data to a portable hard drive weekly or more often as needed.

**2 ** I use Filezilla to copy data to an eMac that I use as a home ftp file server - I back up data monthly.

**3**  Annually I back up data to DVD's - to have a hard copy of that year's data.

I have cruised along for over a decade with no data loss :)

---

### Post by cmcanulty on 2013-06-14
try grsunc. To use it as root just type in terminal ```
gksudo grsync
``` but use it normally for home or it may change permission to root. Graphic very easy and very fast can also check delete on destination to eliminate backing up deleted files. But be careful to not reverse the input and output if you use that option. Does incremental also. I backup 230Gb in a few minutes

---

### Post by oldfred on 2013-06-14
If you just want cron & rsync

 [https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

      
 Some files to exclude from /home backup - post by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

examples:
        
[http://rsync.samba.org/examples.html](http://rsync.samba.org/examples.html)

    
 Backup to external with check of mounted & email
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)
rsync confirmation list:
[http://ubuntuforums.org/showthread.php?t=1692800](http://ubuntuforums.org/showthread.php?t=1692800)
Check for mount of backup partition
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)
#[http://ubuntuforums.org/showthread.php?t=1555647&page=4](http://ubuntuforums.org/showthread.php?t=1555647&page=4)
more scripts:
[http://ubuntuforums.org/showthread.php?t=1319155](http://ubuntuforums.org/showthread.php?t=1319155)

---

