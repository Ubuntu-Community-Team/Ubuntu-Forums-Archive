---
title: "Any way to make a full clone and/or image of mounted running drive? (running 21.04)"
date: 2021-08-15
forum: General Help
---

### Post by Advait on 2021-08-15
[COLOR=#000000][FONT=Arial]Windows 10 has Volume Shadow Service (VSS) that allows apps like Casper to make full images and bootable clones of Windows disks while they're mounted and running. Any apps do this for Ubuntu? I want to make images and clones of my main Ubuntu 21.04 drive while it's mounted and running.
[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]I'm using Timeshift to take regular daily system snapshots and that's working great. But I also want to make full images and clones without unmounting my main drive and without booting from a live USB stik.[/FONT][/COLOR][COLOR=#000000][FONT=Arial]

I read about something called Continuous Data Protection (CDP) and Linux Hot Copy, but it seems they only work on Linux/Ubuntu servers.[/FONT][/COLOR]

---

### Post by mIk3_08 on 2021-08-15
I think dd will work for this the native Linux Disk Coning I think. We also have
PartImage PartClone Clonezilla.
I think this tools can clone your data while your live on your O.S
or you might want to simply sync your vital data to the cloud. It is more safer than you have it by your own.
Or maybe there are some tools online you just have to study it for safety Cloning.
Much better you have to read the instruction of the tool for more safer cloning.
Good luck and Enjoy.

---

### Post by Tadaen_Sylvermane on 2021-08-15
If you use LVM, BTRFS, or ZFS you can do a snapshot. Then mount the snapshot and back it up while the original is still humming away doing it's job.

Are you sure a full clone is the way to go though? This isn't Windows.

It's so quick to do a fresh install that you may be better off backing up certain things and dumping them into a fresh install. I recently started using duplicity to keep my crontabs and /etc folder backed up to an external drive.  It also runs my /home/* and a few other specific places. I think it would be faster to restore from that than to try to do a full system clone / recovery.

---

### Post by monkeybrain20122 on 2021-08-15
[fsarchiver]("https://www.fsarchiver.org/quickstart/")  supports live "cloning" with the -a option providing that you don't alter the file system like installing/removing things during the cloning. fsarchiver is a lot more flexible than clonzilla since it copies files and the meta data only and is insensitive to detail drive configurations and in particular you can restore the backup to any drive with enough room for the contents. Clonzilla requires the target drive to be at least as big as the source even when the source is mostly empty, which is a show stopper for me. Also I don't think it allows live backup.

fsarchiver has a [gui]("https://launchpad.net/~dieterbaum/+archive/ubuntu/qt-fsarchiver") based on qt, it is very convenient to use but with less options than the cli (e.g it doesn't have option to exclude directories)

---

### Post by monkeybrain20122 on 2021-08-15
> **Tadaen_Sylvermane said:**
> 

It's so quick to do a fresh install that you may be better off backing up certain things and dumping them into a fresh install. I recently started using duplicity to keep my crontabs and /etc folder backed up to an external drive.  It also runs my /home/* and a few other specific places. I think it would be faster to restore from that than to try to do a full system clone / recovery.

Well if a bad update messes your system (like xorg) a fresh reinstall won't help. You'll get the same bad updated package that broke your system in the first place. And in general tedious to restore all your settings that way. (settings hacks may not include only those in /home)

---

### Post by Tadaen_Sylvermane on 2021-08-16
Fair enough. I've never had a bad update that I've been aware of of but I guess it can happen. Especially if a large number of ppa's are in use. Thank you for that.

---

### Post by Advait on 2021-08-17
> **mIk3_08 said:**
> I think dd will work for this the native Linux Disk Coning I think. We also have
PartImage PartClone Clonezilla.
I think this tools can clone your data while your live on your O.S
or you might want to simply sync your vital data to the cloud. It is more safer than you have it by your own.

OK, thanks. I'm now researching DD command. So DD command can make a bootable clone of a mounted, running drive? I need this question answered before I can proceed. I'm reading thru the DD documentation and this is not made clear.

Casper for Windows ran in the background and made bootable clones of my main drive as I simultaneously did other tasks on the pc. Can DD command do this?

Also I'm now researching PartImage and PartClone to see of they can do what Casper did. UPDATE: PartImage does not support ext4. UPDATE: Partclone requires the partition to be unmounted. 

AFAIK, Clonezilla only works on unmounted drives. Let me know if this is incorrect.

---

### Post by monkeybrain20122 on 2021-08-17
> **Advait said:**
> OK, thanks. I'm now researching DD command. So DD command can make a bootable clone of a mounted, running drive? I need this question answered before I can proceed. I'm reading thru the DD documentation and this is not made clear.

Casper for Windows ran in the background and made bootable clones of my main drive as I simultaneously did other tasks on the pc. Can DD command do this?

Also I'm now researching PartImage and PartClone to see of they can do what Casper did. UPDATE: PartImage does not support ext4.

dd is the hardcore people's favourite, but it can destroy your system if not careful, also it takes a long time. So if you have to 'research' it you may as well use other tools (I would do some smaller projects to experiment and learn it if there is the desire and need, not by cloning your whole system)  

I really recommend fsarchiver if live cloning is your goal. I have done it many times. It is safe and light and quite easy to use and it is insensitive to low level stuffs like drive configuration as in clonzilla (which cannot do live cloning)

---

### Post by Advait on 2021-08-17
> **Tadaen_Sylvermane said:**
> If you use LVM, BTRFS, or ZFS you can do a snapshot. Then mount the snapshot and back it up while the original is still humming away doing it's job.

This is true, but using BTRFS and ZFS is beyond my technical ability. I tried to use Fedora 34 with BTRFS and it was a nightmare. Every time I tried to do anything in Fedora 34 I ran head long into some arcane technical problem that required many hours of googling and forum posting. Way too much for a newbie like me.

> **Tadaen_Sylvermane said:**
>  Are you sure a full clone is the way to go though? This isn't Windows.

I want a full bootable clone on an external drive so in case my main drive goes bad, I can just open the laptop, pop in the cloned drive and easily continue my work. Casper for Windows did this super easy and with a beautiful easy newbie friendly GUI. Looks like Linux has nothing like Casper. Sigh... :( 

> **Tadaen_Sylvermane said:**
>  It's so quick to do a fresh install that you may be better off backing up certain things and dumping them into a fresh install.

As a newbie, doing a fresh install and getting my Ubuntu system back to where it is now would take 2-4 days of work.

---

### Post by HermanAB on 2021-08-17
Looking at what you stated: ‘A copy of a running system’. I would only trust zfs or btrfs snapshots - those are designed to do exactly that.  Other methods need you to shut down and reboot off different media.

---

### Post by monkeybrain20122 on 2021-08-17
> **Advait said:**
> 

I want a full bootable clone on an external drive so in case my main drive goes bad, I can just open the laptop, pop in the cloned drive and easily continue my work. Casper for Windows did this super easy and with a beautiful easy newbie friendly GUI. Looks like Linux has nothing like Casper. Sigh... :( 




I keep telling you qt-fasrachiver is super-easy and does exactly what you want with a gui. [https://launchpad.net/~dieterbaum/+archive/ubuntu/qt-fsarchiver](https://launchpad.net/~dieterbaum/+archive/ubuntu/qt-fsarchiver)
If you want something quick and easy dd is the last thing you should try. dd is also known as "disk destroyer" btw.

---

### Post by Advait on 2021-08-17
> **HermanAB said:**
> Looking at what you stated: ‘A copy of a running system’. I would only trust zfs or btrfs snapshots - those are designed to do exactly that.  Other methods need you to shut down and reboot off different media.

OK, so what I want to do is not possible on ext4. (Or it may be possible with some high level tech that's beyond my newbie capability.)

I think the answer is "No" but can I convert my ext4 drive to btrfs without messing up any of the data? Or does the conversion wipe out the data that's on the drive?

---

### Post by Advait on 2021-08-17
> **monkeybrain20122 said:**
> I keep telling you qt-fasrachiver is super-easy and does exactly what you want with a gui. [https://launchpad.net/~dieterbaum/+archive/ubuntu/qt-fsarchiver](https://launchpad.net/~dieterbaum/+archive/ubuntu/qt-fsarchiver)
If you want something quick and easy dd is the last thing you should try. dd is also known as "disk destroyer" btw.

Thanks. I've now had my morning coffee so my brain is working again. I'm now googling best way to install fsarchiver. I'll proceed and report back.

---

### Post by monkeybrain20122 on 2021-08-17
> **Advait said:**
> Thanks. I've now had my morning coffee so my brain is working again. I'm now googling best way to install fsarchiver. I'll proceed and report back.

I just gave you the link. The best way is to install is, according to the instruction there

```
sudo add-apt-repository ppa:dieterbaum/qt-fsarchiver
sudo apt update
sudo apt install qt-fsarchiver

```

---

### Post by Advait on 2021-08-17
> **monkeybrain20122 said:**
> I keep telling you qt-fasrachiver is super-easy and does exactly what you want with a gui. [https://launchpad.net/~dieterbaum/+archive/ubuntu/qt-fsarchiver](https://launchpad.net/~dieterbaum/+archive/ubuntu/qt-fsarchiver)
If you want something quick and easy dd is the last thing you should try. dd is also known as "disk destroyer" btw.

I installed fsarchiver. I'm trying to install qt-fsarchiver. See pic. Which file do I need for my AMD laptop? I'm guessing the AMD file, but I need to make sure. [https://imgur.com/a/p8gMNcE](https://imgur.com/a/p8gMNcE) (I'm putting the pic link here cuz the other way doesn't seem to be working.)

Does ubuntuforums disallow imgur links?
.
.
[IMG]https://imgur.com/a/p8gMNcE[/IMG]

---

### Post by monkeybrain20122 on 2021-08-17
You should just execute the codes in post #14. Then it will be installed.

The repository is called a ppa. PPAs are third party software repositories which offer stuffs either not in the official Ubuntu repositories or more up to date versions of the 'official' version. You have to add the ppa to your sources list, update your software pool and then install the package, which are what those three commands do.

---

### Post by monkeybrain20122 on 2021-08-17
I should add that if you want 'restore point" kind of backup snaphsots with btrfs+timeshift is probably the way to go, but I don't feel comfortable recommending it since I don't know about it too much myself. You can also use timeshift with rysnc (so no need for btrfs) Some forum member swears by it, you can also look into it. But then again I have never done it myself and before you have successfully restored a broken system there is really just reading and hearsay, and to test it you have to break a system first. :) I will do it on a disposable VM to test it out when I get around to.

---

### Post by TheFu on 2021-08-17
LVM supports snapshots too.  Make a snapshot of the file system (that freezes those blocks), use whatever tool you like to backup the snapshot.
BTRFS and ZFS support real snapshots too.  These are all "homogeneous data" methods, which means the instance that the snapshot is created, all the data for all files are frozen inside that snapshot.  This is critical, since modified files over the time that a back up takes could be inconsistent.

Unfortunately, none of these can be added after-the-fact.  The OS needs to be installed with one of those tools/file systems installed then.

**dd** doesn't have any special powers.  An inconsistent clone is highly probable if the file system isn't a snapshot.  Anything that isn't a real snapshot could get inconsistent data or some files that are actively being written wouldn't be captured correctly. Thankfully, provided you control when OS patching happens, it is trivial never to run a backup at the same time that application/OS updates happen.  It just isn't a big deal.  And if a backup today fails on a few open files, all the others will be fine and you'll probably have a copy of those same files from yesterday (and 50 other versions) which did get backed up cleanly.

Using dd is fine, fsarchiver is handy too.  Image-based backups are fine for 1-time needs, but if you need to do it all the time, use file-based backups, which are 1000x faster and more flexible.  If you are planning multiple backup solutions, I'd say that only 1 should be necessary. 

If a DBMS is being backed up, then you can be almost positive that a backup will be corrupted unless you dump the DB to a file and get that in the backup.That is extremely common on Unix systems to backup databases.  There must be 20 threads in these forums about doing that for mariaDB or mysql. Those all work, BTW. I've posted to those a few times. No snapshot required for a clean backup that way.  Or use snapshots, then the DBMS journal will ensure a non-corrupted backup. Homogeneous data for a DBMS backup is very important. Getting the data a few seconds after the journal would have inconsistent files. Snapshots prevent that.

There's really no need to make this hard.  Backing up a full server with daily, automatic, versioned, backups can be really easy.  There's an example script in these forums with LVM snapshots too.

---

### Post by monkeybrain20122 on 2021-08-18
BTW to restore with fsatchiver or qt-fsarciver you need a live usb with these tools. You can either use a Ubuntu live usb and then install one or both when you are in a restoring operation, or you can get [this]("https://sourceforge.net/projects/qt-fsarchiver/files/Live-DVD/")

---

### Post by Advait on 2021-08-18
> **monkeybrain20122 said:**
> I just gave you the link. The best way is to install is, according to the instruction there

```
sudo add-apt-repository ppa:dieterbaum/qt-fsarchiver
sudo apt update
sudo apt install qt-fsarchiver

```

OK, qt-fsarchiver is installed and running. I'm now looking thru the docs to get an understanding of the options. At first glance I don't see any options to save a backup to an external USB hard drive, but I'll keep looking.

---

### Post by dragonfly41 on 2021-08-18
Just out of curiosity I installed qt-fsarchiver since I am currently exploring different methods to archive to external SSD's.

If I look in qt-fsarchiver Backup Directory pane and open /media I see all my drives:
sda, sdb, sdc
and so I expect this is where the archive goes provided that you have prepared a drive/partition to receive it.
For this I used Gparted from my active Ubuntu 20.04.

Another tip.  I intend to update/sync small changes between <source> and <archive> and for this I use Meld to view the differences between <source> and <archive>. I can expand on how I do this but in short I use Krusader dual pane file manager and in left pane I view <source> and in right pane I view <archive> and then I run a user action which launches Meld through command line options to compare either directories or files.  Quite a handy GUI for comparing <source> and <archive>.

---

### Post by TheFu on 2021-08-18
> **Advait said:**
> OK, qt-fsarchiver is installed and running. I'm now looking thru the docs to get an understanding of the options. At first glance I don't see any options to save a backup to an external USB hard drive, but I'll keep looking.

You can write to any storage that is mounted.  That's the Unix way.

The idea of "drives" is from MS-Windows and technically incorrect.  MS-Windows uses partitions just like the rest of the computing world. Because of market share, most HDDs/flash drives come preformatted with a MS-Windows compatible file system, so end-users don't realize that is required as well.

With fsarchiver, you'll need to have an appropriate file system on a different partition to accept the .fsa file which is a smart, compressed, image, of the files on the source file system.  There are some caveats.  If fsarchiver understands the file system, it will be smarter and only include areas that actually have files.  If fsarchiver doesn't understand the file system, it will perform a full copy and compression.  Most partitions can be compressed around 50% of the used file sizes, but already compressed files (.zip, .gz, .avi, .jpg, .mov, .mkv, .mp3/4) won't compress much at all.  

I don't recall which file systems fsarchiver knows about, so check the manpage, but I'm fairly certain it understands NTFS, ext2/3/4.  I'd have doubts about btrfs and zfs.

Also, you can point fsarchiver at either the whole disk device or the partition device.  It works best at the partition (or LV) level if you intend to restore to a smaller partition later.  For anything over about 16G, I'd use a different backup solution completely and avoid anything that doesn't support versioning.

---

### Post by Advait on 2021-08-18
> **dragonfly41 said:**
> Just out of curiosity I installed qt-fsarchiver since I am currently exploring different methods to archive to external SSD's.

If I look in qt-fsarchiver Backup Directory pane and open /media I see all my drives:
sda, sdb, sdc

Ahh, there it is. I see my external drive there. Thanks. I've only been using Linux about a month so I need to get used to the whole "mount point" concept. For me, not as intuitive as Windows. Soon I'll run some backups to test it.

---

### Post by TheFu on 2021-08-18
> **Advait said:**
> Ahh, there it is. I see my external drive there. Thanks. I've only been using Linux about a month so I need to get used to the whole "mount point" concept. For me, not as intuitive as Windows. Soon I'll run some backups to test it.

It will take a few years to get over the Windows-way of doing things. Many of us were there too. Every *other* popular OS is like Linux. All of them.
A good, free, no hassle-to-download, reference book: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)
In my beginning Linux classes, we start with Chpt 1 and get as far as we can before the semester runs out. Usually 1 chptr a week.  That's only about the first 250 pgs, then the rest of the book is pure reference.  The base knowledge is critical and I don't think any book can replace the little ways to avoid future issues that a class or mentor setup can. Experience matters in Unix.

---

### Post by monkeybrain20122 on 2021-08-18
> **Advait said:**
> OK, qt-fsarchiver is installed and running. I'm now looking thru the docs to get an understanding of the options. At first glance I don't see any options to save a backup to an external USB hard drive, but I'll keep looking.

It doesn't have too many options. 

To clone your partition on the left side check the box partition save with fsarchiver.

On the right hand upper panel choose the partition you want to clone (or restore to) and on the lower panel choose under /media/yourusername/ the external device you want your backup to go (and to restore choose backup from the same panel) Then choose the number of processors to use, the  compress type and give a name to the backup file (it will automatically make a time tag) and press save partition. Then a popup will say the drive is currently mounted and if you want to do a live cloning. Just click yes. Wait for it to finish, that's it. In the meantime you can continue to use your machine, just don't modify your file system like installing or uninstalling software when this is happening.

If you restore to the same machine as a system backup you only need to clone the / partition, or if you have a separate /home you can clone that too, but you probably prefer a different way to backup your data that doesn't require overwriting the /home in restoring, like [unision-gtk]("https://www.cis.upenn.edu/~bcpierce/unison/"), which is syncing tool. it is already in the repo so you can install it with sudo apt install, or you can use the backup tool installed by default. 

You don't need to clone the vfat boot part.

To restore you need a live usb with qt-fsarchiver on it I recommend [this]("https://sourceforge.net/projects/qt-fsarchiver/files/Live-DVD/Focal/en/"), which is basically a Ubuntu live-usb with qt-fsarchiver installed. To use these tools you need a root password. It is just "ubuntu" (without quotes)

So to restore, boot up from the live usb, use gparted to reformat the corrupt partition which you have previously backed up (to ext4 usually, this is the default format unless you have tried something fancy when you installed Ubuntu)

then fire up qt-fsarchiver and choose restore partition.

Then choose the backup file and the partition to restore to as described above. When finish. shut down machine and remove life usb and then reboot, that's it.

AS I said for more options and better fine grain control (like excluding certain directories from backup to save time and space) you have to use the [cli ]("https://www.fsarchiver.org/quickstart/")version (all single line commands with options so it is not that hard), typically you can exclude everything from your /home/user and use a more flexible way to backup data if you don't have a separate /home partition. See above.

---

### Post by Advait on 2021-08-19
> **TheFu said:**
> You can write to any storage that is mounted.  That's the Unix way.

I found it. I'm new to Linux so still getting used to "mount points".

----------

> **TheFu said:**
> you can point fsarchiver at either the whole disk device or the  partition device.  It works best at the partition (or LV) level if you  intend to restore to a smaller partition later.

I'd like to use qt-fsarchiver similar to how I used Casper for Windows 10. In Casper I just hit a button essentially called "Make Full Clone to External Drive" or "Make Full Image to External Drive" and it would do it in the background while I continued my work. It *seems* FSArchiver works in a similar way and I'll be playing around with it and testing it soon.

It's most likely that I'll be restoring Clones or Images to drives of the same size.

---------------

> **TheFu said:**
> For anything over about  16G, I'd use a different backup solution completely and avoid anything  that doesn't support versioning.

I don't quite understand what you mean by "anything over 16GB"? You mean that if the size of my backup set exceeds 16GB I should not use QT-FSArchiver? The drive I want to make clones and images of is 1.2TB ext4. Should I drop FSArchiver? Please explain this 16GB limit.

"avoid anything  that doesn't support versioning" Since I'm using ext4 are you saying that using FSArchive won't work to create clones and images while my ext4 drive is mounted and running? If FSArchiver is a dead end for what I want to do, please let me know. (My understanding is that ext4 is a journaling file system, not versioning.)

Sorry for my newbie questions, but I have no experience with journaling, versioning, etc.

---

### Post by Advait on 2021-08-19
> **monkeybrain20122 said:**
> On the right hand upper panel choose the partition you want to clone (or restore to) and on the lower panel choose under /media/yourusername/ the external device you want your backup to go (and to restore choose backup from the same panel) Then choose the number of processors to use, the  compress type and give a name to the backup file (it will automatically make a time tag) and press save partition. Then a popup will say the drive is currently mounted and if you want to do a live cloning. Just click yes. Wait for it to finish, that's it. In the meantime you can continue to use your machine, just don't modify your file system like installing or uninstalling software when this is happening. 

This is very helpful. I'm wondering if sometimes Linux/Ubuntu does some software updates in the background without notifying the user? My guess is "no" but please confirm.

What is the reputation of FSArchiver doing "hot" clones of ext4 drives? (assume no software updates happen during the hot clone process) Do experts say "Yeah, it's reliable and works fine with ext4." Or do they say "It's pretty risky with ext4, good luck."? (Risky in the sense that the "hot" clone will likely be corrupted without the user knowing.)

"Hot" clone means a clone of a mounted and running ext4 drive.

----------------------------

> **monkeybrain20122 said:**
> If you restore to the same machine as a system backup you only need to  clone the / partition, or if you have a separate /home you can clone  that too, but you probably prefer a different way to backup your data  that doesn't require overwriting the /home in restoring, like [unision-gtk]("https://www.cis.upenn.edu/~bcpierce/unison/"),  which is syncing tool.

This is very helpful. I do not have a separate /home partition. I already use the very nice sync tools FreeFileSync and Restic for making multiple backups of my full /home directory. 

So to make a QT-FSArchiver clone, I would select the / directory (everything) and exclude the /home directory. That sound right? (And I would have to use the CLI to exclude the /home directory, if I understand correctly.)

----------------------------

> **monkeybrain20122 said:**
> You don't need to clone the vfat boot part.

To restore you need a live usb with qt-fsarchiver on it I recommend [this]("https://sourceforge.net/projects/qt-fsarchiver/files/Live-DVD/Focal/en/"),  which is basically a Ubuntu live-usb with qt-fsarchiver installed. To  use these tools you need a root password. It is just "ubuntu" (without  quotes)

So to restore, boot up from the live usb, use gparted to reformat the  corrupt partition which you have previously backed up (to ext4 usually,  this is the default format unless you have tried something fancy when  you installed Ubuntu)

then fire up qt-fsarchiver and choose restore partition.

Then choose the backup file and the partition to restore to as described  above. When finish. shut down machine and remove life usb and then  reboot, that's it.

AS I said for more options and better fine grain control (like excluding  certain directories from backup to save time and space) you have to use  the [cli ]("https://www.fsarchiver.org/quickstart/")version  (all single line commands with options so it is not that hard),  typically you can exclude everything from your /home/user and use a more  flexible way to backup data if you don't have a separate /home  partition. See above.

All very helpful. Thanks. This gives me a clearer sense of how it works and how to use it.

Just to make sure, it sounds like FSArchiver creates a bootable clone of my ext4 source drive. I have that right?

---

### Post by monkeybrain20122 on 2021-08-19
> **Advait said:**
> This is very helpful. I'm wondering if sometimes Linux/Ubuntu does some software updates in the background without notifying the user? My guess is "no" but please confirm.

What is the reputation of FSArchiver doing "hot" clones of ext4 drives? (assume no software updates happen during the hot clone process) Do experts say "Yeah, it's reliable and works fine with ext4." Or do they say "It's pretty risky with ext4, good luck."? (Risky in the sense that the "hot" clone will likely be corrupted without the user knowing.)

"Hot" clone means a clone of a mounted and running ext4 drive.



It is safe, I always do life cloning, have done it n times. :) The only possible risk is if you drop your computer during the process. :)

> 
This is very helpful. I do not have a separate /home partition. I already use the very nice sync tools FreeFileSync and Restic for making multiple backups of my full /home directory. 

So to make a QT-FSArchiver clone, I would select the / directory (everything) and exclude the /home directory. That sound right? (And I would have to use the CLI to exclude the /home directory, if I understand correctly.)


If you don't have a separate home then there is nothing to exclude. Typically you have a vfat partition for efi boot, you don't need to clone that. Just don't touch it when you restore. Leave it the way it is.

 Then you have something like /dev/sdaX which is where your whole system is, clone that. There is no problem if you don't have a separate /home, it just take longer and the file size is bigger. There is no exclude option in qt-fsarchiver.

I don't know where TheFu pulls out his magic number 16G. It seems to be his personal preference rather than software limitations.

If you use the cli (fsarchiver instead of qt-fsarchiver) you could exclude directories like /home/username/Music, /home/username/Videos /home/username/Documents etc where you probably have a lot data to keep the clone small, but then when you restore those data would be missing and you have to restore them separately from your data backup.

**But you can't exclude the whole /home, it needs a 'shell" even without data, else it won't boot.**


> Just to make sure, it sounds like FSArchiver creates a bootable clone of my ext4 source drive. I have that right?

Well depends on what you want to do. If you just want to restore to your hard drive in case of disasters like bad update then the steps I described is sufficient. It would be bootable after the restore with no additional step since the bootloader is already there.

If you want to transfer your system to a different drive or a different computer then it need to be able to boot so the vfat partition that we don't do here would need to be included (or you need to manually add the bootloader afterwards)

If you want to create an identical system in a second hard drive and run it in the **same computer** for some reasons then you need to change the uuid too, or the computer get confused.


More from here [https://forums.linuxmint.com/viewtopic.php?t=233270](https://forums.linuxmint.com/viewtopic.php?t=233270)

---

### Post by Advait on 2021-08-19
****Monkeybrain20122 wrote** &#8220;It is safe, I always do life cloning, have done it n times. The only possible risk is if you drop your computer during the process. &#8221; 
 
Good news. I read somewhere else that doing a hot clone with a journaling filesystem can be risky. But it seems that FSArchiver has solved that issue. 

 
****Monkeybrain20122 wrote** &#8220;But you can't exclude the whole /home, it needs a 'shell" even without data, else it won't boot.&#8221; 
 
All my user files are in a separate directory under /home (/home/all_my_user_files) I don't keep anything in /home/Documents or /home/Music, etc. So sounds like it's easy for me to use the FSArchiver CLI to exclude /home/all_my_user_files. I have that right? 

 
****Monkeybrain20122 wrote** &#8220;If you just want to restore to your hard drive in case of disasters like bad update then the steps I described is sufficient.&#8221; 
 
Yes. Exactly. This is my main use case. I don't imagine restoring the clone to some other computer. 
 
In any case I should be safe cuz I've heard that Ubuntu updates never cause problems. :-)  :lolflag:

 
****Monkeybrain20122 wrote** &#8220;It would be bootable after the restore with no additional step since the bootloader is already there.&#8221; 
 
Nice! Just what I want.

 
****Monkeybrain20122 wrote** &#8220;If you want to create an identical system in a second hard drive and run it in the same computer for some reasons then you need to change the uuid too, or the computer get confused.&#8221; 
 
Dude! I think you just solved another problem I was having. Every few days I use Parted Magic and Clonezilla to make full clones of my main drive to an external drive. I've been wanting to boot test the clones but I can't cuz the clone is an exact copy. People on the forums said not to boot test the clone when it's connected to my pc cuz it would confuse things and may cause corruption. No one mentioned the option of changing the UUID on the cloned drive. If what you say is accurate, then I can change the UUID on the clone dive and safely boot test the clone drive while it's connected to my laptop with a USB cable. This sound right? 
 
Thanks.

---

### Post by Advait on 2021-08-19
OK, here's my first crack at crafting an actual savefs command for FSArchiver.

fsarchiver savefs /media/advait/Buddha1TB/fsa_1.fsa /dev/nvme0n1p2 --exclude=/home/AUFs --verbose --jobs=4 --compress=7

/media/advait/Buddha1TB/ This is my mount point for the target drive. (External drive connected by USB cable.)

nvme0n1p2 is the partition with my Ubuntu 21.04 install (it's an internal nvme drive).

As far as I can tell, my CPU has 16 cores. Or is it 16 threads? Is a core the same as a thread? My System Monitor displays 16 CPUs.

Questions: 

1. is fsa_1.fsa supposed to be a file or a directory?

2. When I execute the command, does it create the fsa_1.fsa directory (or file)? Or do I have to do that before I execute the command?

3. /home/AUFs is the actual directory location where I keep all my user files (docs, music, video, pics). Will this command exclude all of /home/AUFs?

4. Is /home/AUFs the same as ~/AUFs ?

5. My command look OK?

(I'd like to post this to the FSArchiver forum but I can't locate it. Seems to be defunct. Is there an FSArchiver forum somewhere? I didn't find one on reddit.)

---

### Post by monkeybrain20122 on 2021-08-19
> **Advait said:**
> OK, here's my first crack at crafting an actual savefs command for FSArchiver.

fsarchiver savefs /media/advait/Buddha1TB/fsa_1.fsa /dev/nvme0n1p2 --exclude=/home/AUFs --verbose --jobs=4 --compress=7

/media/advait/Buddha1TB/ This is my mount point for the target drive. (External drive connected by USB cable.)

nvme0n1p2 is the partition with my Ubuntu 21.04 install (it's an internal nvme drive).

As far as I can tell, my CPU has 16 cores. Or is it 16 threads? Is a core the same as a thread? My System Monitor displays 16 CPUs.

Questions: 

1. is fsa_1.fsa supposed to be a file or a directory? 

It is the name of the backup file that fsarchiver creates


> 2. When I execute the command, does it create the fsa_1.fsa directory (or file)? Or do I have to do that before I execute the command?


It will create it.
> 3. /home/AUFs is the actual directory location where I keep all my user files (docs, music, video, pics). Will this command exclude all of /home/AUFs?

I don't think it is a good idea since that way your user's home directory (AUFS) will be excluded so it will be missing if you just restore (I usually reformat the partition before restoring to make sure no remnants of the corrupt system is left) You may encounter problems. Also that way all your configuration will be gone.

If you have no /home partition (which is not the same as a /home directory. The /home partition means during install you put the /home directory in a separate partition, it is not the default configuration) and your data are not in specific subdirectories (like Music, Documents) then I suggest you just clone the whole thing with qt-fsarchiver on the safe side and it is easier that way. Just remember to make a separate /home next time.

> 4. Is /home/AUFs the same as ~/AUFs ?

Yes, but don't exclude it or your clone may not work. But I tend to use the full path when running commands with sudo. And for certain things like making soft links I think (I could be wrong) only the full path works.

> 5. My command look OK?

1) Don't do the --exclude for the reasons I mentioned above
2) To do life cloning (i.e what you call "hot cloning") you need the flags -a -A,
3) it has to run with sudo

So it goes like
```

sudo fsarchiver savefs -v -j$(nproc) -a -A /media/advait/Buddha1TB/fsa_1.fsa /dev/nvme0n1p2  --compress=7
```

See the savefs is always safe, the question is whether restore works. If you exclude the whole /home/username directory then I don't think it will.

---

### Post by monkeybrain20122 on 2021-08-19
You see the problem with cloning software is that you never know if it really works until you try a restore but you don't want to risk blowing up your working system if it doesn't work. So here are some ideas. 1) If you have a spare computer just make a clone and restore to it and see how it goes (either set up a minimal Ubuntu system there and do everything there, or clone your 'real system' and restore it there, but in that case you need to copy the boot part as well, see the Linux Mint forum link I gave above) 2) set up a VM with your favourite virtualization software, do a trial there to get a better feel of how it works.

---

### Post by Advait on 2021-08-20
[COLOR=#000000][FONT=Arial]****Monkeybrain20122 wrote** “I don't think it is a good idea since that way your user's home directory (AUFS) will be excluded so it will be missing if you just restore (I usually reformat the partition before restoring to make sure no remnants of the corrupt system is left) You may encounter problems. Also that way all your configuration will be gone. If you have no /home partition (which is not the same as a /home  directory. The /home partition means during install you put the /home directory in a separate partition, it is not the default configuration) and your data are not in specific subdirectories (like Music, Documents) then I suggest you just clone the whole thing with qt-fsarchiver on the safe side and it is easier that way. Just remember to make a separate /home next time.”
-------------------------------[/FONT][/COLOR]

I don't have a separate /home partition. 

I have multiple daily backups of all my user files in /home/AUFs so it's no problem at all for me to restore them if needed (all the backups are on multiple separate external drives and I use syncing backup apps). The more I think about the more I'd like to exclude /home/AUFs. It will make the clone much smaller and quicker to make and easier to manage. And I can put it on a smaller drive. 

My understanding is that **--exclude=/home/AUFs** will only exclude /home/AUFS and will include everything else in /home, including the config files you mentioned. This correct?

Just to be clear, AUFS is not my username. My Ubuntu system username is advait. ( advait@advait-Bravo-15-A4DDR:~$ )

AUFs just stands for 'Advait User Files'. It's just a folder I created to hold all my user files (I like having all my user files under one folder).

---

### Post by monkeybrain20122 on 2021-08-20
> **Advait said:**
> 

AUFs just stands for 'Advait User Files'. It's just a folder I created to hold all my user files (I like having all my user files under one folder).



Just to clarify. If your structure is /home -> advait -> AUFS (where A -> B means B is a subdirectory of A), advait is your username so your $HOME is /home/advait, which cannot be excluded. But /home/advait/AUFS can be safely excluded.

However in that case the path is /home/advait/AUFS, not /home/AUFS. Under /home are the homes of different users (Linux is a multiuser system), it is not for you to store data.

---

### Post by TheFu on 2021-08-20
> **Advait said:**
>  
Just to be clear, AUFS is not my username. My Ubuntu system username is advait. ( advait@advait-Bravo-15-A4DDR:~$ )

AUFs just stands for 'Advait User Files'. It's just a folder I created to hold all my user files (I like having all my user files under one folder).

That is an unfortunate name collision.  AUFS is also a popular overlay file system used on Linux, so some people could have made all sorts of assumptions about that.

Also, putting storage under /home/ that isn't a user's HOME directory really isn't done for many reasons.  People will make assumptions - best to move it under /media/ or /opt/ or even create /data/aufs, if you like.   You can do whatever you like, but it is very odd.  It will be confusing when working in a team or asking questions.

BTW, there is nothing magical about /home/advait.  It is just an entry in the password databases.  It can point anywhere.  Again, /home is just common for where user account HOME directories are located, but I've seen them under /users/{name} and /nfs/u/{name} and a few other places over the decades.   For a home Linux system (specifically Ubuntu), using /home/ for user HOME directories is expected and, in fact, snap packages won't work otherwise.

---

### Post by TheFu on 2021-08-20
If you are making an image-based backup, this isn't a directory thing. It is the entire partition.  That's the point of using fsarchive.
If you want directory/file based backups then there are 50 better tools - at least 50.

---

### Post by dragonfly41 on 2021-08-20
> [COLOR=#000000]If you want directory/file based backups then there are 50 better tools - at least 50.[/COLOR]

After much pondering  and reading I have concluded that I need both in my backup workflow:
(a) LuckyBackup for "directory/file" based backups (although it offers snapshots)
and (still investigating) ...
(b) something like Vorta [https://vorta.borgbase.com/](https://vorta.borgbase.com/)

Choice of LuckyBackup 
This blog sets out some of the reasons.

[https://www.reallinuxuser.com/luckybackup-is-a-powerful-backup-solution-for-linux/](https://www.reallinuxuser.com/luckybackup-is-a-powerful-backup-solution-for-linux/)

In particular the author writes:

1) it must be possible to directly access the backed up files
2) it must be possible to write different sources to different targets
3) it must be possible to activate or deactivate parts of the backup as needed


and the author goes on to write


Ad 1. A lot of backup solutions, for Linux, but also for MacOS and Windows, have the property that they place the files to be protected in a compressed file or an encrypted file. These backup files can only be opened or restored via the same backup software, or must first be decompressed. That is all very nice, but for myself I need software that just makes an exact copy of my files to another location and can therefore access and use these copied files in the same way as the original files without additional steps or software.


=====================================

The other point is that I will be backing up to both SSD and old recycled HDD devices.
The points about sudden failure of SSD's has hit a nerve.

=====================================

[P.S.] A helpful video.

[https://www.youtube.com/watch?v=ZRjEIsQZsoI&ab_channel=DJWare](https://www.youtube.com/watch?v=ZRjEIsQZsoI&ab_channel=DJWare)

---

### Post by monkeybrain20122 on 2021-08-20
> **dragonfly41 said:**
> 

In particular the author writes:

1) it must be possible to directly access the backed up files
2) it must be possible to write different sources to different targets
3) it must be possible to activate or deactivate parts of the backup as needed


and the author goes on to write


Ad 1. A lot of backup solutions, for Linux, but also for MacOS and Windows, have the property that they place the files to be protected in a compressed file or an encrypted file. These backup files can only be opened or restored via the same backup software, or must first be decompressed. That is all very nice, but for myself I need software that just makes an exact copy of my files to another location and can therefore access and use these copied files in the same way as the original files without additional steps or software.





For all these requirements I think unison-gtk fits the bill, it is simple and intuitive to use and is in the repo. I use it for data bakup.

---

### Post by Advait on 2021-08-20
Here's the updated command with the folder exclude argument:

[COLOR=#1d1c1d][FONT=Arial]sudo fsarchiver savefs -v -j$(nproc) -a -A /media/advait/Buddha1TB/fsa_1.fsa /dev/nvme0n1p2  --compress=7 **--exclude=/home/advait/AUFs** [/FONT][/COLOR]

Look OK?

**By the way, what is -j$(nproc)?** I'm guessing nproc = number of processors. Shouldn't I use --jobs=4 ? I've got 16 CPUs (threads?) so what do you think is the ideal number to use?

[COLOR=#1d1c1d][FONT=Arial]sudo fsarchiver savefs -v -j4 -a -A /media/advait/Buddha1TB/fsa_1.fsa /dev/nvme0n1p2  --compress=7 **--exclude=/home/advait/AUFs** 

This look OK?[/FONT][/COLOR]

(When I get a moment, I'll give responses to some of the issues raised in recent posts. Most importantly, big thanks to all of you for helping me wrap my head around using fsarchiver! O:) )

---

### Post by TheFu on 2021-08-20
> **monkeybrain20122 said:**
> For all these requirements I think unison-gtk fits the bill, it is simple and intuitive to use and is in the repo. I use it for data bakup.

As I wrote, there are lots of tools that do file-based backups well.  Everyone here knows that I prefer rdiff-backup for many reasons. It is in the Canonical Repos.

Previously, I used **rsync**+hardlink tools. Hardlinks can make for really efficient storage of versioned backups.  Those include:
**rsnapshot** - in the Canonical Repos
[LIST]
[*][Https://popey.com/blog/2020/12/straightforward-linux-backups-with-rsnapshot/](Https://popey.com/blog/2020/12/straightforward-linux-backups-with-rsnapshot/)
[*][Https://www.cyberciti.biz/faq/linux-unix-apple-osx-bsd-rsync-copy-hard-links/](Https://www.cyberciti.biz/faq/linux-unix-apple-osx-bsd-rsync-copy-hard-links/)
[/LIST]
**rbackup** - an old script from Unix Power Tools O'Reilly book
**back-in-time** - in the Canonical Repos [https://backintime.readthedocs.io/en/latest/](https://backintime.readthedocs.io/en/latest/)  My Mom used this for years.

Most of the new tools that everyone seems to like are just different GUIs over rsync+hardlinks.  I suppose marketing matters. 

I looked at the **duplicity** family. That's **Deja Dup** and **Duplicati**. They check all the best practice list for excellent backups, except they encode the backups into tiny, encrypted, chunks.  That's good and bad.  I want a restore process that is just a cp or rsync - no fancy tools needed.  Deja Dup is the default backup tool included in Gnome3 Ubuntu for years now.  I tested Duplicati years ago and it was terribly slow. Crazy slow.

And there are always the really old tools like **dump** and **restore**. These are the tools we had in the 1970s that would be take a 0-level dump weekly (full backup), then 7 incremental  2-level dumps daily.  To restore, we'd find the closest full backup (usually a Sunday) and restore it, followed by the incremental backups to the restore date we wanted. I haven't seen dump/restore uses since the 1990s.

The typical backup schedule:
```
S M T W T F S
- – - – - – - 
D D D D D D M
D D D D D D F
D D D D D D F
D D D D D D F
```

Duplicity still needs periodic "full backups" and basically the schedule above from 1970 is still used with those tools.

rdiff-backup works in the opposite way.  That last backup "set" is a mirror of the current system at that time, and older, incremental, changed data is stored as gzip diff files.  If there aren't any changes, then the current file is carried forward into the latest backup set (it doesn't actually get moved, but you get the idea).  Additionally, rdiff-backup does versioning of file metadata, like permissions, groups, owner, ACLs, and xattrs.  To restore the last backup made with rdiff-backup, we can use cp, rsync, or rdiff-backup -r now commands.  We can use a GUI program to traverse down the backup tree (it is a mirror of the source) and copy the selected files we want, then paste those back in the target file system. Files owned by a different userid will need to use sudo in the restore effort to retain all the permissions.

None of the rsync+hardlink backup tools retain that data in different versions. Only the latest metadata is retained. That's a flaw.  But since they appear as full mirrors for each set of data, the restore by cp, rsync, or GUI is possible. The different userid caveat and sudo applies here too.  

In general, only backups for a single user's HOME can be run by a normal userid.  All other backups - system-level or for multiple users, must be run with elevated privileges ...i.e. sudo.

---

### Post by monkeybrain20122 on 2021-08-20
Just type

echo $(nproc) in the terminal to find out. 

Instead of using a fix number -j4 or -j8 since this differ from machine to machine.  If you invoke it with the environmental variable $(nproc) and type -j$(nproc) instead then the system takes care of it automatically.

---

### Post by Advait on 2021-08-20
[SIZE=3][FONT=arial]> **monkeybrain20122 said:**
> Just type

echo $(nproc) in the terminal to find out. 

Instead of using a fix number -j4 or -j8 since this differ from machine to machine.  If you invoke it with the environmental variable $(nproc) and type -j$(nproc) instead then the system takes care of it automatically.

OK, thanks. So the final version of the command is 

[COLOR=#1d1c1d]sudo fsarchiver savefs -v -j$(nproc) -a -A /media/advait/Buddha1TB/fsa_1.fsa /dev/nvme0n1p2  --compress=7 [B]--exclude=/Home/advait/AUFs

[/B]Does it pass the final test? (I changed /home to /Home to make it correct.)

Here's the pic of my /Home directory setup -> [https://imgur.com/a/TJnJvUe](https://imgur.com/a/TJnJvUe)  So my understanding now is that /Home/AUFs is the same as /Home/advait/AUFs. That correct?


-------------
advait@advait-Bravo-15-A4DDR:~$ echo $(nproc) 
16 


[/COLOR][/FONT][/SIZE]

---

### Post by Advait on 2021-08-21
> **monkeybrain20122 said:**
> Just type echo $(nproc) in the terminal to find out.  Instead of using a fix number -j4 or -j8 since this differ from machine to machine.  If you invoke it with the environmental variable $(nproc) and type -j$(nproc) instead then the system takes care of it automatically.

Just curious what "takes care of it automatically" actually means? Does it mean that "the system" just uses all the CPUs by default? Or does "the system" control the number of CPUs being used based on other apps also in use?

---

### Post by Advait on 2021-08-21
(Reply to 'TheFu') I'm using Timeshift to do a daily snapshot of my system. Seems to work pretty good. I've had to restore my system once and it worked.

---

### Post by monkeybrain20122 on 2021-08-21
Actually it is /home, other than that it looks fine.

Question: So timeshift doesn't do what you want? Can it do live cloning? I never use it.

---

### Post by Advait on 2021-08-21
> **monkeybrain20122 said:**
> Actually it is /home, other than that it looks fine..

You sure? Did you see the pic at Imgur? So /home is different from /Home? I guess that means /home is some kind of "system" directory with a special purpose and /Home is just a "normal, non-system" directory available for the user. That sound right?

So the final version is 

[SIZE=3][FONT=arial][COLOR=#1d1c1d]sudo fsarchiver savefs -v -j$(nproc) -a -A /media/advait/Buddha1TB/fsa_1.fsa /dev/nvme0n1p2  --compress=7 **--exclude=/home/advait/AUFs**[/COLOR][/FONT][/SIZE]

Looks good?

[SIZE=3][FONT=arial][COLOR=#1d1c1d]So **--exclude=/home/Home/advait/AUFs**[/COLOR][/FONT][/SIZE] would be incorrect?
.
.

---

### Post by monkeybrain20122 on 2021-08-21
There is no Home unless you have created it. The normal structure is /home/yourusername. This is your $HOME (which is an environmental variable) Inside your $HOME (/home/yourusername) is where you put your user files. So I assume your layout is that AUFs is some directort where you store your data and it sits inside /home/advait

---

### Post by Advait on 2021-08-21
> **monkeybrain20122 said:**
> There is no Home unless you have created it. The normal structure is /home/yourusername. This is your $HOME (which is an environmental variable) Inside your $HOME (/home/yourusername) is where you put your user files. So I assume your layout is that AUFs is some directort where you store your data and it sits inside /home/advait

Still confusing to me, but no worries. The Imgur pic shows my Home directory and AUFs and the folders underneath it. AUFs is under both /home and /Home depending on how I view the directory structure. Confusing, but I'll save that puzzle for later.

I went ahead and plugged in my external USB hard drive. Then I went into terminal and executed the command:

[SIZE=3][FONT=arial][COLOR=#1d1c1d]sudo fsarchiver savefs -v -j$(nproc) -a -A /media/advait/Buddha1TB/fsa_1.fsa /dev/nvme0n1p2  --compress=7 --exclude=/home/advait/AUFs

FSArchiver is now grinding thru my files. Looks like it's doing what it's supposed to do. 

This is the first app that has maxed out all 16 cores at once. Wow.

---------------------
Update: Looks like it (successfully?) finished. Took about 20 minutes.

Statistics for filesystem 0 
* files successfully processed:....regfiles=275886, directories=40686, symlinks=54335, hardlinks=67901, specials=61 
* files with errors:...............regfiles=0, directories=0, symlinks=0, hardlinks=0, specials=0 
advait@advait-Bravo-15-A4DDR:~$  

Here's the pic of the clone file: [https://imgur.com/a/H3inN4K](https://imgur.com/a/H3inN4K) Looks like a successful backup. Excluding all my user files probably sped up the backup by about 95%. Would have been a little scary to see all my 16 cores pegged to 100% for 5-6 hours.
 

Thanks again to everyone who posted suggestions. 
[/COLOR][/FONT][/SIZE]

---

### Post by Advait on 2021-08-21
> **monkeybrain20122 said:**
> Just to clarify. If your structure is /home -> advait -> AUFS (where A -> B means B is a subdirectory of A), advait is your username so your $HOME is /home/advait, which cannot be excluded. But /home/advait/AUFS can be safely excluded.

However in that case the path is /home/advait/AUFS, not /home/AUFS. Under /home are the homes of different users (Linux is a multiuser system), it is not for you to store data.

This was very helpful. Thanks.

---

### Post by Advait on 2021-08-21
> **monkeybrain20122 said:**
> Question: So timeshift doesn't do what you want? Can it do live cloning? I never use it.

I don't think Timeshift (based on rsync) can make images or clones. But I haven't looked thru the docs in detail. I'm now a big fan of Timeshift since it recently successfully restored my system to an earlier state after something went wrong. Timeshift is not for backing up user files. It's only for taking system snapshots (it's default setting is to ignore all user files). 

Wow. I think this is the first time I've shared some (possibly) useful knowledge on this forum (rather than just asking endless newbie questions.) :P   :D

---

### Post by Advait on 2021-08-21
> **TheFu said:**
> If you are making an image-based backup, this isn't a directory thing. It is the entire partition.  That's the point of using fsarchive.
If you want directory/file based backups then there are 50 better tools - at least 50.

1. Excluding all my user files has good advantages for me in regards to using FSArchiver. I think it will be easy for me to restore my user files after restoring a partition.

2. I use Restic, FreeFileSync and Deja Dup to make daily backups of just my user files. FreeFileSync has a beautiful easy GUI and the saved files are all in native, unmodified format with no compression.

If I get time I want to explore the other backup options.

---

### Post by monkeybrain20122 on 2021-08-21
> **Advait said:**
> [SIZE=3][FONT=arial][COLOR=#1d1c1d]
---------------------
Update: Looks like it (successfully?) finished. Took about 20 minutes.

Statistics for filesystem 0 
* files successfully processed:....regfiles=275886, directories=40686, symlinks=54335, hardlinks=67901, specials=61 
* files with errors:...............regfiles=0, directories=0, symlinks=0, hardlinks=0, specials=0 
advait@advait-Bravo-15-A4DDR:~$  

[/COLOR][/FONT][/SIZE]

Great. But with all cloning software you can't know whether it really works until you have done a restore. Since you don't want to mess with your working system, I suggest you test it out somehow. If You have a spare computer laying around you can do a trial run with the complete savefs/resfs workflow, or you can try in a VM.

---

### Post by TheFu on 2021-08-21
> **Advait said:**
> 1. Excluding all my user files has good advantages for me in regards to using FSArchiver. I think it will be easy for me to restore my user files after restoring a partition.

2. I use Restic, FreeFileSync and Deja Dup to make daily backups of just my user files. FreeFileSync has a beautiful easy GUI and the saved files are all in native, unmodified format with no compression.

If I get time I want to explore the other backup options.

O! M! G!   If you are using more than 1 backup tool, you've made this entirely too difficult.  1 tool should accomplish all that is needed. If that isn't the situation, pick a better tool.

Playing around with lots of different tools is fine, but only 1 should be needed.

---

### Post by Advait on 2021-08-21
> **monkeybrain20122 said:**
> Great. But with all cloning software you can't know whether it really works until you have done a restore. Since you don't want to mess with your working system, I suggest you test it out somehow. If You have a spare computer laying around you can do a trial run with the complete savefs/resfs workflow, or you can try in a VM.

I don't have a spare pc but I'm intrigued at trying the VM option. Great tip! I'll do some googling to see if someone has made a step by step of how to restore a FSArchiver clone to a VM in Ubuntu. When I try to do it myself, I'll probably run into some brick walls and will be posting more questions on the forum. It will be a good exercise and help me learn more about using VMs.

---

### Post by Advait on 2021-08-21
[SIZE=4][FONT=arial]> **TheFu said:**
> O! M! G!   If you are using more than 1 backup tool, you've made this entirely too difficult.  1 tool should accomplish all that is needed. If that isn't the situation, pick a better tool. Playing around with lots of different tools is fine, but only 1 should be needed.[COLOR=#1d1c1d]

As a Linux/Ubuntu newbie, learning how to successfully use the various backup apps greatly helped me to learn some of the basics of using Linux/Ubuntu.[/COLOR][COLOR=#1d1c1d]No harm in using various backup apps. Having multiple backups increases the security of my data. And all my backup apps (except Clonezilla) run in the background.
[/COLOR]
[COLOR=#1d1c1d]Restic has restore points (nice) and can restore prior versions of files and folders (nice). 
[/COLOR]
[COLOR=#1d1c1d]FreeFileSysnc has a beautiful intuitive GUI (nice) and backs up files without any modifications (nice).[/COLOR]
[COLOR=#1d1c1d]
Timeshift can take system snapshots (nice) and makes it easy to restore a prior snapshot (nice).[/COLOR]
[COLOR=#1d1c1d]
With FSArchiver I can make a fast (only 20 minutes) hot clone (very nice) of my main partition and exclude all my user files (nice). Clonezilla can&#8217;t do that. Thus FSArchiver allows me to easily store multiple versions of the clone on a smaller drive (nice, I can backup an older clone if I want). The hot clone means I can keep working and don&#8217;t need to mess with shutting everything down and waiting 20 minutes and then rebooting (nice).[/COLOR]

[COLOR=#1d1c1d]So, each of the various backup apps offer certain advantages. Using them all means I get the best of all and multiple backups of various types (all nice. And more secure).[/COLOR]
[/FONT][/SIZE]

---

### Post by monkeybrain20122 on 2021-08-22
> **Advait said:**
> I don't have a spare pc but I'm intrigued at trying the VM option. Great tip! I'll do some googling to see if someone has made a step by step of how to restore a FSArchiver clone to a VM in Ubuntu. When I try to do it myself, I'll probably run into some brick walls and will be posting more questions on the forum. It will be a good exercise and help me learn more about using VMs.

Basically you can run a VM like  a real machine. Depends on what VM software you use the details may differ but the idea is the same. 

Install Ubuntu in VM, boot from iso. When installing, choose "Advanced" option, use only part of the virtual drive to install Ubuntu. Use the rest as an "external media" to store your backup in the savefs step. You can create the partitions with gparted first (do "Try Ubuntu") before you start the installer. After installing Ubuntu, put some random files in it to make it realistic, or you can create a few folders to make it look sort of like your real set up. Shut down, remove live iso, then boot into Ubuntu again. Install fsarchiver, run savefs and save to the partition that you made. To restore, shut down VM, attach the live iso and change boot order to boot from iso. Boot up VM. You are now in the live session. then install fsarchiver (sudo apt install fsarchiver) since it is not included in the live usb, now do a restfs from there.

---

### Post by Advait on 2021-08-22
> **monkeybrain20122 said:**
> Basically you can run a VM like  a real machine. Depends on what VM software you use the details may differ but the idea is the same. 

Install Ubuntu in VM, boot from iso. When installing, choose "Advanced" option, use only part of the virtual drive to install Ubuntu. Use the rest as an "external media" to store your backup in the savefs step. You can create the partitions with gparted first (do "Try Ubuntu") before you start the installer. After installing Ubuntu, put some random files in it to make it realistic, or you can create a few folders to make it look sort of like your real set up. Shut down, remove live iso, then boot into Ubuntu again. Install fsarchiver, run savefs and save to the partition that you made. To restore, shut down VM, attach the live iso and change boot order to boot from iso. Boot up VM. You are now in the live session. then install fsarchiver (sudo apt install fsarchiver) since it is not included in the live usb, now do a restfs from there.

I've got VBox installed and I've played around with it a little. When I get some time I'll work on these steps. Thanks.

---

### Post by TheFu on 2021-08-22
There are 3 ways to make a snapshot on Linux.  Anything else is a lie or misunderstanding.  LVM, ZFS, BTRFS have snapshot capabilities built-into their volume management. Creating a snapshot takes less than 1 second and is effectively instantaneous.  No files can be copied or movied in this process - if that happens, then it is NOT a snapshot.

FSArchiver doesn't make the underlying file system quiesced.  If it is on and working, then files are being modified while the tool runs.  There are techniques to minimize that, but not in a multi-user boot (i.e. boot into single-user mode).  Or use something like LVM to create a snapshot and backup that with fsarchiver.  That would be fine as well.
From the fsarchiver manpage:
```
       -A, --allow-rw-mounted
              Allow to save a filesystem which is mounted in read-write (live backup). By
              default  fsarchiver  fails  with an error if the device is mounted in read-
              write mode which allows modifications to be done on the  filesystem  during
              the backup. Modifications can drive to inconsistencies in the backup. [B]Using
              LVM snapshots is the recommended way to make backups since it will  provide
              consistency, but it is only available for filesystems which are on LVM log&#8208;
              ical volumes.[/B]
```
Which is what I've said, but it isn't automatic. You have to set up LVM snapshots - which requires using LVM as the first step.  If LVM isn't used, then there is nothing to be done, except boot into single-user mode or boot from an alternative OS (flash drive) to use fsarchiver.

FWIW.

---

### Post by Advait on 2021-08-23
> **TheFu said:**
> There are 3 ways to make a snapshot on Linux.  Anything else is a lie or misunderstanding.  LVM, ZFS, BTRFS have snapshot capabilities built-into their volume management.

Thanks for the details. Very helpful. It gives me a better understanding of what a snapshot really is.

My feeling is that doing a fresh install of Ubuntu 21.04 to get LVM or BTRFS would take a lot of time, more time than I have. 

And my understanding is doing a fresh install is the only way to convert my ext4 file system to LVM or BTRFS.

Perhaps in the future there will be some tools available that will allow a Linux newbie like me to easily and safely convert ext4 to LVM or BTRFS without needing to do a fresh install. I browse some Linux blogs and listen to various Linux podcasts so I'm sure they'll give notice if such a tool becomes available.

Thanks again for your suggestions! :)

And thanks again to the Ubuntu Forums community for your patience in helping me understand FSArchiver. I'll be using it every few days.

---

### Post by TheFu on 2021-08-23
LVM isn't a file system. It is volume management.  A file system still needs to be placed on top of the LVM Logical Volume. Any file system can be put there, but there are integrations with ext4 that make it the best choice of file system under LVM.

BTRFS and ZFS have the file system AND volume manager merged into a single tool. This wasn't typically done for a long time.  Perhaps you've heard of Veritas VM and Veritas FS?  Those were available for almost every OS - including Windows.  They were only used inside Enterprises.  LVM is the Linux take on that.  HP, IBM, Sun Microsystems all had their own versions of volume managers, but most places would buy Veritas.  LVM on Linux has been enterprise ready for over 20 yrs.  I must say, there isn't any GUI to manage it.  But I don't know of any GUI to manage BTRFS or ZFS either.

There is no conversion to LVM.  There is only wipe and create fresh on the disks involved.  The installer has a checkbox that will lay down LVM.  1 checkbox.  Now, I must say that the defaults for what it creates aren't really what I'd use, but for someone new, it is probably good enough for 6 months.  The worst thing it does (I don't recall the exact setup for 21.04, sorry), is I think it allocates all the storage to LVs, so there isn't any room for snapshots left.  That sorta defeats the main purpose for using LVM.  Which means one of the first things post-install would be to reduce the "root" LV from way-too-huge, down to 35GB size.  Do that ASAP. The longer someone waits, the harder it is to safely accomplish.

A fresh install of any Ubuntu is 15 minutes.  Right?  Actually, it is more like 10 minutes if you know what you are doing.
Getting your settings and critical data and all the APT-installed packages back is another 15 minutes.  So, in 30 minutes, with selective backups of the actual important data, a fully restore, "feels like your system" Ubuntu, is available.  Then about another 15 minutes for any excess data to be restored ... say music files or other media.  That's sorta been my entire point in this thread.  Restoring is 45 minutes - that pretty much a worse case outcome.

And if it is 30-45 minutes using selected, file-based, versioned, backups, what's the point of using image-based backups at all?  I just don't see it.

---

### Post by Advait on 2021-08-23
> **TheFu said:**
> BTRFS and ZFS have the file system AND volume manager merged into a single tool.

If I'm reading these articles correctly, it looks like there are tools to convert my ext4 to Btrfs without needing to do a reinstall. 

Here [https://www.thegeekdiary.com/how-to-convert-ext-file-systems-to-btrfs/](https://www.thegeekdiary.com/how-to-convert-ext-file-systems-to-btrfs/) and here [http://manpages.ubuntu.com/manpages/bionic/man8/btrfs-convert.8.html](http://manpages.ubuntu.com/manpages/bionic/man8/btrfs-convert.8.html) 

Am I reading them correctly? No need to reinstall Ubuntu if I use these tools to convert to Btrfs?

(Rest assured I will do multiple backups before doing the conversion.)

I'm a newbie, but it looks like Btrfs is quite comparable to LVM-ext4. Is there some reason a newbie like me should not use Btrfs?

You prefer Btrfs or LVM-ext4? Why?

---

### Post by TheFu on 2021-08-23
Sorry. I've avoided btrfs due to some documented corruption issues with it and my primary workloads.  

My data is too important to trust to a file system that has had some catastrophic data loss issues.  When that happened, it became a "never use" option to me.  When Redhat deprecated btrfs from their systems, that spoke volumes to me as well.  Even a year ago, for my main workloads, btrfs was specifically recommended against being used.  I think Redhat has put btrfs back into the last release, but I've moved on.

When I choose to change volume management or file systems, that's often a 10 yr commitment.  My use of LVM is very deep at this point.  I have some ZFS too, but only about 50G worth. the other 30+TB is LVM+ext4.

I wouldn't know anything about tools that convert file systems. Sorry.  Some things just seem like terrible ideas. That is one.  Putting passwords into a cloudy service is another.  Putting unencrypted files into cloudy storage is another.  Bad ideas. They just "smell bad."

There are all sorts of things that are possible, but still bad ideas.

---

### Post by monkeybrain20122 on 2021-08-23
> **Advait said:**
> If I'm reading these articles correctly, it looks like there are tools to convert my ext4 to Btrfs without needing to do a reinstall. 

Here [https://www.thegeekdiary.com/how-to-convert-ext-file-systems-to-btrfs/](https://www.thegeekdiary.com/how-to-convert-ext-file-systems-to-btrfs/) and here [http://manpages.ubuntu.com/manpages/bionic/man8/btrfs-convert.8.html](http://manpages.ubuntu.com/manpages/bionic/man8/btrfs-convert.8.html) 

Am I reading them correctly? No need to reinstall Ubuntu if I use these tools to convert to Btrfs?


I am currently testing btrfs. It is true that that is a tool (btrfs-convert) that converts ext4 to btrfs, but from what I read it is not very reliable and many people have lost their systems for failed conversion. I don't know whether these posts are still relevant as some are quite old. But if I were to do it on a working system I will do a tried and true complete clone with other tools first. Again I suggest setting up btrfs on a VM first to test it out in case. One oddity I find is that it seems that diskspace are being used up very fast, I read that df is not reliable for reading btrfs, also syslog grows very fast and when I limit its size the issue goes away (the snapshots themselves are pretty small) 

AFAIK OpenSuse is the only distro that uses btrfs as default.

---

### Post by Advait on 2021-08-24
> **TheFu said:**
> Sorry. I've avoided btrfs due to some documented corruption issues with it and my primary workloads.  My data is too important to trust to a file system that has had some catastrophic data loss issues.  When that happened, it became a "never use" option to me.  When Redhat deprecated btrfs from their systems, that spoke volumes to me as well.  Even a year ago, for my main workloads, btrfs was specifically recommended against being used.  I think Redhat has put btrfs back into the last release, but I've moved on.

When I choose to change volume management or file systems, that's often a 10 yr commitment.  My use of LVM is very deep at this point.  I have some ZFS too, but only about 50G worth. the other 30+TB is LVM+ext4. I wouldn't know anything about tools that convert file systems. Sorry.  Some things just seem like terrible ideas. That is one.  Putting passwords into a cloudy service is another.  Putting unencrypted files into cloudy storage is another.  Bad ideas. They just "smell bad." There are all sorts of things that are possible, but still bad ideas.

> **monkeybrain20122 said:**
> I am currently testing btrfs. It is true that that is a tool (btrfs-convert) that converts ext4 to btrfs, but from what I read it is not very reliable and many people have lost their systems for failed conversion. I don't know whether these posts are still relevant as some are quite old. But if I were to do it on a working system I will do a tried and true complete clone with other tools first. Again I suggest setting up btrfs on a VM first to test it out in case. One oddity I find is that it seems that diskspace are being used up very fast, I read that df is not reliable for reading btrfs, also syslog grows very fast and when I limit its size the issue goes away (the snapshots themselves are pretty small) 

AFAIK OpenSuse is the only distro that uses btrfs as default.
[COLOR=#1d1c1d][FONT=Arial]
I did a bit of googling and looks like Btrfs has a mixed reputation re stability. And it's the default fs in Fedora 34 so I'm guessing the Fedora people did some level of vetting that it has sufficient quality to include. Maybe Btrfs is good enough for home users but not quite ready for business.
[/FONT][/COLOR]
[COLOR=#1d1c1d][FONT=Arial]And looks like LVM-ext4 would probably work well for me. [/FONT][/COLOR]

[COLOR=#1d1c1d][FONT=Arial]So the risky option is to make some good backups and try the Btrfs conversion. Or play it safe and, when I get some free time, do a fresh install of Ubuntu and select LVM during the install process. I’ll google some more and decide.[/FONT][/COLOR]

[COLOR=#1d1c1d][FONT=Arial]One of the big headaches I had with various 21.04 apps was dealing with file permission issues. If I use LVM-ext4, do the file permissions work the same as in 21.04 ext4 without LVM?[/FONT][/COLOR]

[COLOR=#1d1c1d][FONT=Arial]Please confirm. [/FONT][/COLOR]

[COLOR=#1d1c1d][FONT=Arial]Thanks!

PS: I should also ask what are the problems / issues with using LVM-ext4?
[/FONT][/COLOR]

---

### Post by TheFu on 2021-08-24
Unix file permissions work the same on every popular OS in the world, except 1.  That 1 OS comes from a NW state in the USA and requires payment to use, payment to connect to any "servers" they offer. Those are called "CALs", btw.

>  PS: I should also ask what are the problems / issues with using LVM-ext4?
It is an enterprise storage volume manager. What some people consider problems, others consider features.  Setup a VM, create some small storage areas with LVM and work through a few tutorials if you want to understand more.  I did exactly that.  The good news is that LVM is LVM across all Linux systems, so the LVM tutorials for any distro are just as valid.

I've posted about LVM in these forums many times. That includes an architecture diagram, what I consider ideal layers, etc. How to backup with LVM snapshots. That information is all in these forums for you to see.

---

### Post by Advait on 2021-08-25
> **TheFu said:**
> Unix file permissions work the same on every popular OS in the world

Thanks. Just wanted to confirm as part of my due diligence in researching LVM-ext4.

--------------------
> **TheFu said:**
> Setup a VM, create some small  storage areas with LVM and work through a few tutorials if you want to  understand more.

Good idea. I put this project on my list.

-------------------------------------------
> **TheFu said:**
> I've posted about LVM in these forums many times. That includes an  architecture diagram, what I consider ideal layers, etc. How to backup  with LVM snapshots. That information is all in these forums for you to  see. 

I read your posts here: [https://ubuntuforums.org/showthread.php?t=2456011&highlight=lvm+snapshots+backup](https://ubuntuforums.org/showthread.php?t=2456011&highlight=lvm+snapshots+backup) Very helpful.
---------------------------

---

### Post by smith32 on 2021-09-06
Anyway to make a full clone and/or image of the mounted running drive? I'm still confused.





[[COLOR="#000000"]QuickPayPortal[/COLOR]]("https://quickpayportalme.com/")

---

### Post by monkeybrain20122 on 2021-09-06
> **smith32 said:**
> Anyway to make a full clone and/or image of the mounted running drive? I'm still confused.





[[COLOR=#000000]QuickPayPortal[/COLOR]]("https://quickpayportalme.com/")

fsarchiver, see above.

---

### Post by TheFu on 2021-09-06
> **smith32 said:**
> Anyway to make a full clone and/or image of the mounted running drive? I'm still confused.

Yes. How to do it depends on whether file corruption is ok or not.  There are lots of things that are possible, but not good ideas.

a) Linux doesn't mount "drives".  It mounts either partitions or LVs or whatever BTRFS or ZFS calls their equivalent. 
b) LVs can be quiesced using LVM snapshots.  Then the snapshot can be backed up (or imaged) using any tool you like, safely, without file corruption likely underneath.
c) BTRFS and ZFS both support proper snapshots too.
d) If we use a virtual machine with qcow2, the qcow2 storage method also supports snapshots. Those can also be backed up or imaged using almost any tool you like.

Many backup tools call things "snapshots" which actually ARE NOT snapshots.  Proper snapshots are created in less than 1 second.  Backup snapshots take much longer and leave time for different files to become out of sync while the backup runs.  Some backup tools recognize the volume manager is available and that the volume manager supports proper snapshots, so it will use those.  However, those same tools continue to use the "snapshot" term for other backup sets that are not created using the volume manager snapshot.  On an active server, this can make the backups useless.  On a desktop, the risks for file corruption during the backup process is less, but still exist.  Because computers *KNOW* when we really need a good backup to work, that will be the day that the file we need is corrupted in the backup.  There's no science to this, but it seems to happen that way.

---

### Post by Advait on 2021-09-07
@thefu - Very helpful for me.

---

