---
title: "backing up system and creating bootable iso"
date: 2013-08-14
forum: General Help
---

### Post by msousa on 2013-08-14
Hi

I would like to back up my ubuntu system to a dvd and have that dvd be bootable. Is this possible? Now that I've gotten a number of things to work, I would also like to backup my home directory and my /var/cache/apt/archives directory to get any new system up to the same as the one I have. Does this make sense?

Thanks...

Mike

---

### Post by TheFu on 2013-08-14
> **msousa said:**
> Hi

I would like to back up my ubuntu system to a dvd and have that dvd be bootable. Is this possible? Now that I've gotten a number of things to work, I would also like to backup my home directory and my /var/cache/apt/archives directory to get any new system up to the same as the one I have. Does this make sense?

Thanks...

Mike

There used to be a tool to remaster a current dist for Ubuntu. Haven't seen much talk about it the last 2+ yrs. [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization) is all that I found with google.

As to backing up a system and being able to restore it to exactly a specific point, I do that nightly using rdiff-backup. Takes about 3 minutes per server (depending on what has changed, obviously).  I do NOT backup large media files.  This is close to how I do it: [http://www.jdpfu.com/2009/10/24/linux-home-backup-with-rdiff-backup](http://www.jdpfu.com/2009/10/24/linux-home-backup-with-rdiff-backup) though I have made it more efficient and do it more like this: [http://blog.jdpfu.com/2011/10/08/optimized-backups-for-physical-and-virtual-machines](http://blog.jdpfu.com/2011/10/08/optimized-backups-for-physical-and-virtual-machines) now.

There is a big difference in **knowing you have a good backup with everything necessary** and *thinking you might have a backup with most of the files needed.*  Big difference.

---

### Post by BBQdave on 2013-08-14
Another thought Msousa, backing up data so that it is easily accessible by any system.

On my home network, I have an old tower with Ubuntu 12.04 Server edition installed. It is a FTP file server that I access using FileZilla. On the file server, I loaded [**vsftpd**]("https://security.appspot.com/vsftpd.html"); and on my notebook, I installed [**FileZilla**]("https://filezilla-project.org/").

If something goes wrong on my notebook, I can do a fresh install of a Linux distro and restore data from my server in one to two hours. If my notebook hardware becomes toast - still have my data backed up - for new hardware.

I am cruising along no worries, with Ubuntu 12.04 Server Edition - as FTP file server, and Ubuntu Unity 12.04LTS on my notebook :D

---

### Post by SlugSlug on 2013-08-14
I find backintime good for backups but it's not very good for a full system restore, it doesn't do the SUID which is odd. I've only tried once, but I use it each time to restore my home and /etc/configs after a reinstall

---

### Post by msousa on 2013-08-14
Thanks for the info. There seems to be no preferred way to backup linux  systems, maybe because there are so many different media to backup to  and so many different things to backup. I do not have another server or  pc to backup to so my plan is to backup my ubuntu system to a dvd that I  can then reboot from if needed. Then, because I've spent so much time  getting some items to work (bemicro/de2, arduino/ardupilot mega and  beagleboard, etc) I'd like to backup some of the items I think would  make it easier to recover if needed, also onto a dvd. With writeable  dvds, I was hoping to do incremental backups every once in awhile as I  get other things to work. I'm also under the impression that my home  directory and my /var/cache/apt/archives directory contains most of what  I've changed to make things work. Am I off track?

---

### Post by TheFu on 2013-08-14
> **BBQdave said:**
> Another thought Msousa, backing up data so that it is easily accessible by any system.

On my home network, I have an old tower with Ubuntu 12.04 Server edition installed. It is a FTP file server that I access using FileZilla. On the file server, I loaded [**vsftpd**]("https://security.appspot.com/vsftpd.html"); and on my notebook, I installed [**FileZilla**]("https://filezilla-project.org/").

If something goes wrong on my notebook, I can do a fresh install of a Linux distro and restore data from my server in one to two hours. If my notebook hardware becomes toast - still have my data backed up - for new hardware.

I am cruising along no worries, with Ubuntu 12.04 Server Edition - as FTP file server, and Ubuntu Unity 12.04LTS on my notebook :D

Almost nobody should be using FTP anymore. [http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp)  The 3 most popular FTP servers have all been found with backdoors over the last 3-5 yrs - and that is just 1 reason. There are many more reasons NOT to use FTP.

2 hours for a restore seems long?  With good backups, it should be under 30 minutes for 20G or so.  That should get the OS, apps and most HOME dirs back.  Heck, my main desktop is ... 
```
$ df -h
Filesystem        Size  Used Avail Use% Mounted on
/dev/vda1          14G   11G  2.4G  81% /
```
just 14G. Two yrs ago, it was 10G.  Clearly, I keep large files outside the desktop.

With rdiff-backup as the tool, here's my backup stats for this machine:
```
$ sudo rdiff-backup --list-increment-sizes lubuntu
        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Wed Aug 14 02:03:07 2013         4.95 GB           4.95 GB   (current mirror)
Tue Aug 13 02:03:06 2013         10.2 MB           4.96 GB
Mon Aug 12 02:03:06 2013         9.34 MB           4.97 GB
Sun Aug 11 02:03:09 2013         9.71 MB           4.98 GB
Sat Aug 10 02:03:08 2013         9.25 MB           4.98 GB
.
.
.
Thu Jul 18 02:03:06 2013         9.31 MB           5.33 GB
Wed Jul 17 02:03:06 2013         18.9 MB           5.35 GB
Tue Jul 16 02:03:05 2013         9.78 MB           5.36 GB
```
Notice how small each incremental backup is? That's the change data.  4.95G is the mirror for all the files that I backup from last night.  5.36G is the total size of all backups for the last 30 days.  That's under 10% more for 30 days of backups.  Clearly, I do not backup every file, but I do save everything needed to restore to exactly the same point.   **dpkg --get-selections** for backups  and **dpkg --set-selections ** for restores are the tricks for that. Efficient backups rock.  Having a local **apt-cacher-ng** server is great too. Very fast package access that way.  

BTW, just changed the 30 day retention to 60 days to better recover after corrupted files or being hacked.  I think I can afford the storage. ;)

---

### Post by oldfred on 2013-08-14
I do not have a server to backup to, but use another hard drive for regular backups and then copy most important files to DVD on a periodic basis to try to capture images in case I erase or damage a file and rsync to other drive copies damaged file.
If you do not have another file, a larger flash drive would also work. I have bootable flash dries as a backup way to boot and have the Ubuntu ISO on the flash drive to boot as an installer if need be. Then I can reinstall, and restore from my backups, similar to others posted above.

 discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)

      
 [https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

---

### Post by TheFu on 2013-08-14
Great stuff there Oldfred.

I've presented a few times on Linux backups at our LUG.  Let me see if I can find a presentation links.  Enjoy:
* Backup Overview - [http://blog.jdpfu.com/ALE/ALE-NW/a09_backups.html](http://blog.jdpfu.com/ALE/ALE-NW/a09_backups.html) - Got Backup Religion?
* Rsync - [http://blog.jdpfu.com/ALE/ALE-NW/a05_rsync.html](http://blog.jdpfu.com/ALE/ALE-NW/a05_rsync.html)
* Back-In-Time Snapshots - [http://blog.jdpfu.com/ALE/ALE-NW/a08_BIT.html](http://blog.jdpfu.com/ALE/ALE-NW/a08_BIT.html) - not really good for system backups - GREAT for personal HOME backups
* rdiff-backup - [http://blog.jdpfu.com/ALE/ALE-NW/a10_rdiff_backup.html](http://blog.jdpfu.com/ALE/ALE-NW/a10_rdiff_backup.html) - great all around backup tool. Easy replacement for rsync hacks.

I hope these help someone.

Someone else presented on **Duplicati** and **Duplicity.** Both are amazing tools.  That presenter has switched to using **rdiff-backup** for most backups and only uses duplicity for "sensitive" data backups where he considers pre-encryption to the remote storage mandatory. The only things that I dislike about those tools is that backup set are used and out data is hard to get at without the tool. rdiff-backup doesn't have that issue. Anyone with minimal Linux skills can restore 1 file (or everything) easily without rdiff-backup at all. Normal tools are used.

---

### Post by oldfred on 2013-08-14
I stopped using compressed tools for backups years ago, only because my floppy disk failed and I lost entire backup even though I knew most of disk could be read. But that was years ago.

But since drive space is relatively inexpensive nowadays I still prefer just to backup files so if one file is damaged, I may be able to read other files. And I can easily restore one file without other tools to open a compressed image.

---

### Post by TheFu on 2013-08-14
> **oldfred said:**
> I stopped using compressed tools for backups years ago, only because my floppy disk failed and I lost entire backup even though I knew most of disk could be read. But that was years ago.

But since drive space is relatively inexpensive nowadays I still prefer just to backup files so if one file is damaged, I may be able to read other files. And I can easily restore one file without other tools to open a compressed image.

I understand completely. The last rdiff-backup set is a mirror - just like rsync creates. It is only the older changes which get diff'ed and gzipped. I find that to be an acceptable amount of complexity vs storage.  rsnapshot, rbackup, back-in-time are each based on hardlinks. I found them to be much less efficient on storage to the point that it mattered to me.  If I backed up just a single 14G box - no issue, but I have a small issue with VM sprawl and backup everything.  Even 4-8G at a time, it adds up.

I also use optical media for storage of non-changing files that I'd like to keep. For those, I use 10% **par2** files to fight bitrot. A simple script:
```
#!/bin/sh

for filename in "$@"; do

   # Create a 10% recovery data with blocksize of 300KB
   nice par2 create -s307200 -r10 "$filename"

done
```
Of course, it fails if a filename has spaces or certain special characters.  A little sed-action could make it "just work", but I'd rather just fix my filenames.

Combined with **gaffitter**, which will optimize file placement on specific disk sizes, and I'm able to fill optical discs almost full every time.  Just now, some of the discs from 2002 are starting to fail where the parity files really helps - zero data loss.  At the 1st sign of trouble, I pull all the data off that disc and reburn - usually with more data since switching to 8G discs happened a few years ago. They are cheaper/GB.  I'm at the point where hassle vs cost is a consideration now, so I probably will not purchase anymore DVD media and will only buy 4TB HDDs.  In theory, less than 3TB should hold (300) 8G DVDs worth of data.  That is a huge savings in hassle - saw a 3TB disk for $111 today.  OTOH, having that much data in a single "basket" is scary.

Well, there is no exact answer for backups. Each of us has to find our own workable solution ... or not.

---

### Post by BBQdave on 2013-08-14
> **TheFu said:**
> Almost nobody should be using FTP anymore.

[**vsftpd**]("https://security.appspot.com/vsftpd.html")  on a secure home network, that is to say, a hardened Ubuntu Server  behind multiple firewalls. Like anything, user error, setting up  vsftpd incorrectly, could lead to vulnerabilities. And I only access my Ubuntu Server from within my home network.

> **oldfred said:**
> I do not have a server to backup to, but use another hard drive for regular backups...

I use a portable hard drive aswell, for yet another back up of my system.

I back up weekly or as needed - depending on the projects I am working on, to my Ubuntu Server. And I back up monthly to my portable hard drive. Annually I back up data to DVD's, before that CD's, and before that ZIP Cassettes :) 

I have cruised along for over a decade, backing up data in this manner. Not lost any data yet - and I can still access data from 10 years ago :D

---

### Post by msousa on 2013-08-14
> **oldfred said:**
> 
 discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

Hey guys, thanks for all the info. In reading through this stuff I am now dizzy :
It's almost too much information, I'm not quite sure where to begin. I'm thinking I would use TAR to backup my personal files and those I generated through updates to get things to work. I'm not sure what to do about generating a boot-able dvd from my system though. If somthing happened, I would like to pop the dvd in, boot up and rebuild the drive, but I'm wondering if that is the way to go.

---

### Post by TheFu on 2013-08-15
> **msousa said:**
> Hey guys, thanks for all the info. In reading through this stuff I am now dizzy :
It's almost too much information, I'm not quite sure where to begin. I'm thinking I would use TAR to backup my personal files and those I generated through updates to get things to work. I'm not sure what to do about generating a boot-able dvd from my system though. If somthing happened, I would like to pop the dvd in, boot up and rebuild the drive, but I'm wondering if that is the way to go.

Sorry for the overload.  There are many, many ways to accomplish what you desire that do not include a custom DVD.  Honestly, the easiest, foolproof way is to clone the entire HDD to another similar HDD.  You can't use both in the same machine concurrently, but if 1 fails, you'll be able to swap in the other and be 100% back to where you were the day of the last mirror.  It is bonehead. It is free. It will work.  Recovery takes as long as it takes to swap in the mirrored HDD.  Because you would want to use UUID-based mounts and cloning a disk also clones the UUIDs, that is why you can't have the same disks running inside the same system .... but you can add the 2nd drive while in single-user-mode and mirror stuff safely by device name (/dev/sdZ) with a command like this:

```
$ sudo ddrescue /dev/sda /dev/sdZ /tmp/log
```

This mirrors not just the data, but the partitions, boot sector, even empty space or encrypted file systems ... everything on the drive 100%.
Simple. Using **ddrescue** is preferred so that any bad sectors do not stop the mirror.  You can use **dd** as well ... meh ... ddrescue would be better.

Or you could use something link **Clonezilla** or **partimage**.  These are a little smarter and don't copy empty areas. Also, they compress the output.  However, both really require that you run them from outside the disks involved.  I find partimage easier. Both work with Windows, tivos, anything too ... to a HDD, data is data. If these tools cannot be smart with the data, they fall back to dd-style copies.

After the first clone, you can continue to clone using the tools above ... or you can use rsync to speed things up. Until there is a new kernel installed, that will work perfectly. It might work perfect after a new kernel too - I don't know for certain. Sorry.

Of course, if you copy the entire disk, it takes a while. Speed, convenience and versioning are why most people backup using other tools if there is any choice.

If you just care about data and the amount is relatively small, **tar** can work fine.  KISS principal matters. You need to understand the backup method, so you can restore it.  Nobody here will be their to help, after all. ;)

---

