---
title: "Is it possible to backup Mac APFS personal data to Ubuntu server ext4 HDD ?"
date: 2021-07-24
forum: General Help
---

### Post by freeflyjohn on 2021-07-24
I would like to be able to backup files from my Mac Book Pro (macOS High Sierra 10.13.6) over the internal network to my server which is running Ubuntu 20.04.

The server HDDs (WD Red CMR) are formatted as ext4.

I tried to backup my personal data on the Mac to the HDD in the server using tools like rsync and Carbon Copy Cloner, but these seem to fail because the Mac drive is APFS formatted and the server drive is ext4 formatted.

I used to run Ubuntu 16.04 on my server which had netatalk installed, this allowed me to use TimeMachine on the Mac and backup to the server.

When I view the Time Machine backup folder on the server, there is a .sparsebundle folder, then in that folder there is a bands folder and this is full of files named in hex.

Therefore I am unable to access my personal data within the Time Machine backup, unless I run Time Machine from the Mac.  But this is not much use if my Mac stops working (as it has in the past)

So I don't want to use Time Machine anymore, I want to use something more generic like rsync, rdiff-backup or Carbon Copy Cloner etc

Also I am not interested in backing up OS files, I only want to backup personal data such as media e.g. video, pictures, documents etc.

If a HDD fails I can always re-install an OS, unlike personal data which would be lost forever.

Is there are way to resolve this ?

---

### Post by gsahli on 2021-07-24
I think you should try rsync again. here's a guide: [https://eshop.macsales.com/blog/45185-mac-101-learn-the-power-of-rsync-for-backup-remote-archive-systems/](https://eshop.macsales.com/blog/45185-mac-101-learn-the-power-of-rsync-for-backup-remote-archive-systems/)
As far as I know, if the ubuntu drive (destination) can be mounted, it can be used for backup.

---

### Post by scorp123 on 2021-07-24
> **freeflyjohn said:**
>  I tried to backup my personal data on the Mac to the HDD in the server using tools like rsync and Carbon Copy Cloner, but these seem to fail because the Mac drive is APFS formatted and the server drive is ext4 formatted.

Please be more specific? ***What exactly*** fails? Because I use **"rsync"** between my MacBook (running macOS "Catalina") and my Linux server and it works tip top. *"it seems to fail"* is very vague. Show us what command you tried? Maybe there's something wrong with it and we find the exact reason why it really failed. Or maybe it didn't even fail and you are misinterpreting something? Please show us.

---

### Post by Tadaen_Sylvermane on 2021-07-24
Format shouldn't matter on the ends. My Windows machine can backup files direct to a samba share that is formated ext4 with zero difficulty. The file system type is quite irrelevant unless it's in the same machine. Of course Apple has been known to do their own thing forcing people to buy their special stuff.

---

### Post by freeflyjohn on 2021-07-24
Thanks all, I managed to get it working.

I stripped back the command to the very basic and started added options one by one, there must have been a syntax issue.

```

rsync -a -v -b --backup-dir="deleted_$(date +\%Y-\%m-\%d)" --delete --exclude-from /Users/myusername/rsync/rsync-exclude-list.txt /Users/myusername/Volumes/Storage/Backup/Mac/rsync

```

I came across the -b option which will be useful seeing as rsync accidentally deleted some files on the destination.

---

### Post by freeflyjohn on 2021-07-24
Nope.... spoke to soon


I have only performed rsync on the Download and the Documents folders on the Mac so far, but the size difference is vast so something is not right...


Downloads folder on the Mac: 21.02GB
Downloads folder on the sever: 2.5GB


Documents folder on the Mac: 47.02GB
Documents folder on the Server: 3.8GB


This the exclude list...

```


.Spotlight*
.Trash*
.AppleDouble*
.*
$RECYCLE.BIN
*.ini
iperf3


Applications (Parallels)
Desktop
Documents/Microsoft User Data
#Documents
#Downloads
Library
Movies
Music
Nextcloud
Parallels
Pictures
Public
Trash
rsync


```

I then commented out the Pictures folder (using a #) in the exception list and got the following error...


```



myusername/Pictures/2006.photolibrary/Database/Folders/TrashFolder.apfolder
            455 100%    0.53kB/s    0:00:00 (xfr#26, ir-chk=1091/4274)
myusername/Pictures/2006.photolibrary/Database/History/
myusername/Pictures/2006.photolibrary/Database/History/Changes/
myusername/Pictures/2006.photolibrary/Database/History/Changes/0000000001.plist
          7,116 100%    8.22kB/s    0:00:00 (xfr#27, ir-chk=1089/4274)
myusername/Pictures/2006.photolibrary/Database/Places/
myusername/Pictures/2006.photolibrary/Database/Vaults/
myusername/Pictures/2006.photolibrary/Database/Versions/
myusername/Pictures/2006.photolibrary/Database/Volumes/
myusername/Pictures/2006.photolibrary/Database/apdb/
myusername/Pictures/2006.photolibrary/Database/apdb/BigBlobs.apdb
         32,768  33%   35.24kB/s    0:00:01  rsync: [generator] readdir("/Volumes/Storage/Backup/Mac/rsync/myusername/Pictures/Photos Library.photoslibrary/Attachments/d/dc"): Not a directory (20)


rsync: [sender] write error: Broken pipe (32)
rsync error: error in socket IO (code 10) at io.c(823) [sender=3.2.3]
rsync error: received SIGUSR1 (code 19) at main.c(1612) [generator=3.2.3]



```


I even installed Homebrew on the Mac so I could install a later version of rsync (3.2.3)


The version of rsync on Ubuntu 20.04 is 3.1.3.

No wonder people don't bother to backup when its such a head ache !

---

### Post by CharlesA on 2021-07-24
That's super strange.

Can you try running it with these arguments?

```
rsync --archive --verbose --itemize-changes -b --backup-dir="deleted_$(date +\%Y-\%m-\%d)" --delete --exclude-from /Users/myusername/rsync/rsync-exclude-list.txt /Users/myusername/Volumes/Storage/Backup/Mac/rsync 2>&1 | tee -a /path/to/logfile.txt
```

Maybe that will help you see if there are any permission denied errors or other issues during the transfer.

---

### Post by freeflyjohn on 2021-07-25
> **CharlesA said:**
> That's super strange.

Can you try running it with these arguments?

```
rsync --archive --verbose --itemize-changes -b --backup-dir="deleted_$(date +\%Y-\%m-\%d)" --delete --exclude-from /Users/myusername/rsync/rsync-exclude-list.txt /Users/myusername/Volumes/Storage/Backup/Mac/rsync 2>&1 | tee -a /path/to/logfile.txt
```

Maybe that will help you see if there are any permission denied errors or other issues during the transfer.

Thanks CharlesA, I ran the command you suggested.  Below is the last part of the log file on the Mac...

```

>f++++++++++ myusername/Pictures/2006.photolibrary/Database/tmSync.plist
.d...p...... myusername/Pictures/2006.photolibrary/Database/Albums/
>f++++++++++ myusername/Pictures/2006.photolibrary/Database/Albums/HJw6IjUsQBOpU6r%Z+RW6w.apalbum
>f++++++++++ myusername/Pictures/2006.photolibrary/Database/Albums/allProjectsAlbum.apalbum
>f++++++++++ myusername/Pictures/2006.photolibrary/Database/Albums/lastImportAlbum.apalbum
>f++++++++++ myusername/Pictures/2006.photolibrary/Database/Albums/libraryFolderImplicitAlbum.apalbum
>f++++++++++ myusername/Pictures/2006.photolibrary/Database/Albums/rotationAlbum.apalbum
>f++++++++++ myusername/Pictures/2006.photolibrary/Database/Albums/trashAlbum.apalbum
.d...p...... myusername/Pictures/2006.photolibrary/Database/Faces/
.d...p...... myusername/Pictures/2006.photolibrary/Database/Faces/Detected/
.d...p...... myusername/Pictures/2006.photolibrary/Database/Faces/DetectedExternals/
.d...p...... myusername/Pictures/2006.photolibrary/Database/Faces/FaceExternals/
.d...p...... myusername/Pictures/2006.photolibrary/Database/Faces/FaceNames/
.d...p...... myusername/Pictures/2006.photolibrary/Database/Folders/
>f++++++++++ myusername/Pictures/2006.photolibrary/Database/Folders/AllProjectsItem.apfolder
>f++++++++++ myusername/Pictures/2006.photolibrary/Database/Folders/LibraryFolder.apfolder
>f++++++++++ myusername/Pictures/2006.photolibrary/Database/Folders/PublishedProjects.apfolder
>f++++++++++ myusername/Pictures/2006.photolibrary/Database/Folders/RKPhotostreamFolder.apfolder
>f++++++++++ myusername/Pictures/2006.photolibrary/Database/Folders/TopLevelAlbums.apfolder
>f++++++++++ myusername/Pictures/2006.photolibrary/Database/Folders/TopLevelSlideshows.apfolder
>f++++++++++ myusername/Pictures/2006.photolibrary/Database/Folders/TrashFolder.apfolder
.d...p...... myusername/Pictures/2006.photolibrary/Database/History/
.d...p...... myusername/Pictures/2006.photolibrary/Database/History/Changes/
>f++++++++++ myusername/Pictures/2006.photolibrary/Database/History/Changes/0000000001.plist
.d...p...... myusername/Pictures/2006.photolibrary/Database/Places/
.d...p...... myusername/Pictures/2006.photolibrary/Database/Vaults/
.d...p...... myusername/Pictures/2006.photolibrary/Database/Versions/
.d..tp...... myusername/Pictures/2006.photolibrary/Database/Volumes/
.d...p...... myusername/Pictures/2006.photolibrary/Database/apdb/
>f++++++++++ myusername/Pictures/2006.photolibrary/Database/apdb/BigBlobs.apdb
>f++++++++++ myusername/Pictures/2006.photolibrary/Database/apdb/Faces.db
>f++++++++++ myusername/Pictures/2006.photolibrary/Database/apdb/Faces.db.iplmbak
>f++++++++++ myusername/Pictures/2006.photolibrary/Database/apdb/History.apdb
>f++++++++++ myusername/Pictures/2006.photolibrary/Database/apdb/ImageProxies.apdb
>f++++++++++ myusername/Pictures/2006.photolibrary/Database/apdb/Library.apdb
>f++++++++++ myusername/Pictures/2006.photolibrary/Database/apdb/Properties.apdb
.d...p...... myusername/Pictures/2006.photolibrary/Masters/
.d...p...... myusername/Pictures/2006.photolibrary/Previews/
.d...p...... myusername/Pictures/2006.photolibrary/Thumbnails/
.d...p...... myusername/Pictures/2006.photolibrary/iLifeShared/
>f++++++++++ myusername/Pictures/2006.photolibrary/iLifeShared/AlbumData2.xml
>f++++++++++ myusername/Pictures/2006.photolibrary/iLifeShared/ApertureDatabaseTimestamp
.d...p...... myusername/Pictures/Monosnap/
.d...p...... myusername/Pictures/Photo Booth Library/
>f++++++++++ myusername/Pictures/Photo Booth Library/Recents.plist
.d...p...... myusername/Pictures/Photo Booth Library/Backdrops/
.d...p...... myusername/Pictures/Photo Booth Library/Contents/
>f++++++++++ myusername/Pictures/Photo Booth Library/Contents/PkgInfo
.d...p...... myusername/Pictures/Photo Booth Library/Originals/
>f++++++++++ myusername/Pictures/Photo Booth Library/Originals/4-up on 09-03-2013 at 17.42 #10 (original).jpg
>f++++++++++ myusername/Pictures/Photo Booth Library/Originals/4-up on 09-03-2013 at 17.42 #11 (original).jpg
>f++++++++++ myusername/Pictures/Photo Booth Library/Originals/4-up on 09-03-2013 at 17.42 #12 (original).jpg
>f++++++++++ myusername/Pictures/Photo Booth Library/Originals/4-up on 09-03-2013 at 17.42 #2 (original).jpg
>f++++++++++ myusername/Pictures/Photo Booth Library/Originals/4-up on 09-03-2013 at 17.42 #3 (original).jpg
>f++++++++++ myusername/Pictures/Photo Booth Library/Originals/4-up on 09-03-2013 at 17.42 #4 (original).jpg
>f++++++++++ myusername/Pictures/Photo Booth Library/Originals/4-up on 09-03-2013 at 17.42 #5 (original).jpg
>f++++++++++ myusername/Pictures/Photo Booth Library/Originals/4-up on 09-03-2013 at 17.42 #6 (original).jpg
>f++++++++++ myusername/Pictures/Photo Booth Library/Originals/4-up on 09-03-2013 at 17.42 #7 (original).jpg
>f++++++++++ myusername/Pictures/Photo Booth Library/Originals/4-up on 09-03-2013 at 17.42 #8 (original).jpg
>f++++++++++ myusername/Pictures/Photo Booth Library/Originals/4-up on 09-03-2013 at 17.42 #9 (original).jpg
>f++++++++++ myusername/Pictures/Photo Booth Library/Originals/4-up on 09-03-2013 at 17.42 (original).jpg
>f++++++++++ myusername/Pictures/Photo Booth Library/Originals/4-up on 09-03-2013 at 17.43 #10 (original).jpg
>f++++++++++ myusername/Pictures/Photo Booth Library/Originals/4-up on 09-03-2013 at 17.43 #11 (original).jpg
>f++++++++++ myusername/Pictures/Photo Booth Library/Originals/4-up on 09-03-2013 at 17.43 #12 (original).jpg
rsync: [generator] stat "/Volumes/Storage/Backup/Mac/rsync/myusername/Pictures/Photos Library.photoslibrary/Attachments/v/vc" failed: No such file or directory (2)
>f++++++++++ myusername/Pictures/Photo Booth Library/Originals/4-up on 09-03-2013 at 17.43 #2 (original).jpg
rsync: [generator] recv_generator: mkdir "/Volumes/Storage/Backup/Mac/rsync/myusername/Pictures/Photos Library.photoslibrary/Attachments/v/vc/vcUJVDPLQV+pkYyUa4blrg" failed: No such file or directory (2)
*** Skipping any contents from this failed directory ***
>f++++++++++ myusername/Pictures/Photo Booth Library/Originals/4-up on 09-03-2013 at 17.43 #3 (original).jpg
>f++++++++++ myusername/Pictures/Photo Booth Library/Originals/4-up on 09-03-2013 at 17.43 #4 (original).jpg
>f++++++++++ myusername/Pictures/Photo Booth Library/Originals/4-up on 09-03-2013 at 17.43 #5 (original).jpg
>f++++++++++ myusername/Pictures/Photo Booth Library/Originals/4-up on 09-03-2013 at 17.43 #6 (original).jpg
>f++++++++++ myusername/Pictures/Photo Booth Library/Originals/4-up on 09-03-2013 at 17.43 #7 (original).jpg
>f++++++++++ myusername/Pictures/Photo Booth Library/Originals/4-up on 09-03-2013 at 17.43 #8 (original).jpg
>f++++++++++ myusername/Pictures/Photo Booth Library/Originals/4-up on 09-03-2013 at 17.43 #9 (original).jpg
>f++++++++++ myusername/Pictures/Photo Booth Library/Originals/4-up on 09-03-2013 at 17.43 (original).jpg
rsync: [sender] write error: Broken pipe (32)
rsync error: error in socket IO (code 10) at io.c(823) [sender=3.2.3]
rsync error: received SIGUSR1 (code 19) at main.c(1612) [generator=3.2.3]

```


I am trying to understand rsync ,having read somewhere that rysnc needs to be installed on both the source and destination machines.

I always thought rsync only needs to be on the source machine ?

So does this mean that if rsync was not installed on the Ubuntu server, then rsync on the Mac would not work when backing up to Ubuntu server ?

I was reminded of this question when I found a different logfile.txt on the Ubuntu HDD which is different to the logfile.txt on the Mac.

The complete logfile.txt on the Ubuntu HDD is below:


```

sending incremental file list
rsync: [sender] change_dir "/Users/myusername/Volumes/Storage/Backup/Mac" failed: No such file or directory (2)


sent 19 bytes  received 12 bytes  62.00 bytes/sec
total size is 0  speedup is 0.00
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1350) [sender=3.2.3]
sending incremental file list

```

---

### Post by coffeecat on 2021-07-25
@freeflyjohn, I've edited your last two posts to remove a mass of interfering BBCode. Every single line in the code boxes had its own pair of BBCode font and color tags, which damaged the formatting of the text in the code boxes. Code boxes default to a monospace font. Specifying a non-monospace font (in this case Helvetica), destroys the neat columnar formatting.

Are you using some sort of software to compose and edit your posts? I cannot imagine adding all those BBCode tags by hand, or from the message editor toolbar.

---

### Post by freeflyjohn on 2021-07-25
Thanks coffeecat, sorry I've no idea what BBCode is ?  I have no idea what happened ?  

I opened the logfile.txt using the TextEdit app on the Mac, then copied the text from TextEdit and pasted into the post (Im using the Chrome browser) and put the code boxes at the start and end.  

I also notice that the formatting screws up if I edit a post, it seems to add additional line spacing ?

---

### Post by freeflyjohn on 2021-07-25
I've updated the version of rsync on Ubuntu to be the same as the version of rsync on the Mac.

rsync on Ubuntu was version 3.1.3 and rsync on the Mac is the latest version 3.2.3.

So now both the Mac and Ubuntu are using the same version of rsync (3.2.3)

I've started an rsycn on just the Downloads folder and its got much further than before (its still running).

So the problem seems to have been a difference in rsync versions between my Mac and Ubuntu

---

### Post by coffeecat on 2021-07-25
> **freeflyjohn said:**
> ... sorry I've no idea what BBCode is ?  

...

...and put the code boxes at the start and end.  


Run that by me again? Code boxes are created using BBCode code tags. Have a look at these:

[Basic guide to BBCode](https://ubuntuforums.org/showthread.php?t=2054969&p=12231647#post12231647) - [Fuller guide to BBCode](https://ubuntuforums.org/misc.php?do=bbcode)

Anyway, so as not to derail this thread, I suggest you start a new thread in [Forum Feedback & Help](https://ubuntuforums.org/forumdisplay.php?f=48) and we can look into this. For starters I can say that the forum software does not add additional line spacing when you edit a post unless you tell it to, and that I doubt that TextEdit was adding the BBCode. There was a truly horrendous amount of spurious BBCode in your posts, and it would be very useful to track down where that was coming from. I can also introduce you to a seemingly little known but invaluable feature of the message editor that helps you to stay in control of formatting your posts with BBCode.

---

### Post by CharlesA on 2021-07-25
> **freeflyjohn said:**
> Thanks CharlesA, I ran the command you suggested.  Below is the last part of the log file on the Mac...

```

~snip~
rsync: [generator] stat "/Volumes/Storage/Backup/Mac/rsync/myusername/Pictures/Photos Library.photoslibrary/Attachments/v/vc" failed: No such file or directory (2)
>f++++++++++ myusername/Pictures/Photo Booth Library/Originals/4-up on 09-03-2013 at 17.43 #2 (original).jpg
rsync: [generator] recv_generator: mkdir "/Volumes/Storage/Backup/Mac/rsync/myusername/Pictures/Photos Library.photoslibrary/Attachments/v/vc/vcUJVDPLQV+pkYyUa4blrg" failed: No such file or directory (2)
*** Skipping any contents from this failed directory ***
~snip~

```

I am trying to understand rsync ,having read somewhere that rysnc needs to be installed on both the source and destination machines.

I always thought rsync only needs to be on the source machine ?

So does this mean that if rsync was not installed on the Ubuntu server, then rsync on the Mac would not work when backing up to Ubuntu server ?

I was reminded of this question when I found a different logfile.txt on the Ubuntu HDD which is different to the logfile.txt on the Mac.



Where are you backing your data up to? The OP said you were backing your files up to your server via the network. However, the command you were using didn't specify a destination, and I'm not too sure how -b and --backup-dir work with rsync as I've never used them.

As for your questions if you need rsync installed on both the source and destination, if you are transferring the files with rsync over SSH. if you have a folder mounted locally (which it looks like you do), you only need it on the source machine.

> **freeflyjohn said:**
> I've updated the version of rsync on Ubuntu to be the same as the version of rsync on the Mac.

rsync on Ubuntu was version 3.1.3 and rsync on the Mac is the latest version 3.2.3.

So now both the Mac and Ubuntu are using the same version of rsync (3.2.3)

I've started an rsycn on just the Downloads folder and its got much further than before (its still running).

So the problem seems to have been a difference in rsync versions between my Mac and Ubuntu

To rule out a network or configuration issue, can you run this rsync command and see if all the files copy over?

```
rsync --archive --verbose --itemize-changes /path/to/source/folder /path/to/destination/folder 2>&1 | tee -a /path/to/logfile.txt
```

Please note: I took out the exclusions to test if this would succeed or not. If it runs successfully, delete the files in the destination and start adding in the exclusions one by one and see if any of them cause it to choke. You will probably need to delete the files in the destination before you run rsync again to make sure you start with a clean slate.

If that passes OK, add in the --backup and --backup-dir arguments and try again.

Based on the error message you are getting it sounds like one of the folders at the destination isn't being created, but I don't have a good way to confirm that is the case.

---

### Post by freeflyjohn on 2021-07-25
Seems I was wrong again :(

Why is this proving so hard !

I'm still getting the same errors

```

sending incremental file list
cd++++++++++ username/
cd++++++++++ username/Desktop/
>f++++++++++ username/Desktop/Microsoft Edge.lnk
cL++++++++++ username/Desktop/P-touch Editor.app -> /Applications/P-touch Editor 5.1/P-touch Editor.app
cL++++++++++ username/Desktop/P-touch Update Software.app -> /Applications/P-touch Update Software/P-touch Update Software.app
>f++++++++++ username/Desktop/Thumbs.db
>f++++++++++ username/Desktop/Windows 10
cd++++++++++ username/Downloads/
cd++++++++++ username/Downloads/Ender+3+Side+Spool+Holder/
>f++++++++++ username/Downloads/Ender+3+Side+Spool+Holder/LICENSE.txt
>f++++++++++ username/Downloads/Ender+3+Side+Spool+Holder/README.txt
cd++++++++++ username/Downloads/Ender+3+Side+Spool+Holder/files/
>f++++++++++ username/Downloads/Ender+3+Side+Spool+Holder/files/CE3_Long_Foot_Spool_Holder_Arm.gcode
>f++++++++++ username/Downloads/Ender+3+Side+Spool+Holder/files/CE3_Spool_Holder_Base.gcode
rsync: [sender] write error: Broken pipe (32)
rsync error: error in socket IO (code 10) at io.c(823) [sender=3.2.3]
rsync error: received SIGUSR1 (code 19) at main.c(1612) [generator=3.2.3]

```

---

### Post by CharlesA on 2021-07-25
OK, that gives us some more info.

Can you check on your server and run dmesg or check the system log?

```
sudo dmesg | tail -n 50
```

```
sudo tail -n 50 /var/log/syslog
```

rsync failed in this case because the remote server terminated the process.

You can also check to see how much memory is in use on the server with this command:
```
free -m
```

It should output something like this:
```

free -m
              total        used        free      shared  buff/cache   available
Mem:          32087       25633        2257         206        4196        5789
Swap:         16383         849       15534

```

EDIT: Is the server you are backing up to owned by you or is it hosted by another company? If it's hosted, they may have put limits on load or memory usage that you could be hitting.

---

### Post by freeflyjohn on 2021-07-25
[SIZE=2][FONT=arial]Thanks CharlesA

To answer your earlier question, this is my own server at home.

Its a Dell T30 Poweredge and connected to a 1Mb internal LAN network.

The results are below, is the problem caused by Ubuntu Firewall (ufw)?

[/FONT]```

[FONT=arial]sudo dmesg | tail -n 50[/FONT][FONT=arial]

[COLOR=#000000][  321.193524] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:7c:ff:4d:20:f0:98:08:00 SRC=192.168.178.1 DST=192.168.178.25 LEN=282 TOS=0x00 PREC=0x00 TTL=64 ID=12597 PROTO=UDP SPT=1900 DPT=47750 LEN=262 [/COLOR]
[COLOR=#000000][  321.194603] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:7c:ff:4d:20:f0:98:08:00 SRC=192.168.178.1 DST=192.168.178.25 LEN=281 TOS=0x00 PREC=0x00 TTL=64 ID=12598 PROTO=UDP SPT=1900 DPT=47750 LEN=261 [/COLOR]
[COLOR=#000000][  321.195537] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:7c:ff:4d:20:f0:98:08:00 SRC=192.168.178.1 DST=192.168.178.25 LEN=286 TOS=0x00 PREC=0x00 TTL=64 ID=12599 PROTO=UDP SPT=1900 DPT=47750 LEN=266 [/COLOR]
[COLOR=#000000][  321.196662] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:7c:ff:4d:20:f0:98:08:00 SRC=192.168.178.1 DST=192.168.178.25 LEN=279 TOS=0x00 PREC=0x00 TTL=64 ID=12600 PROTO=UDP SPT=1900 DPT=47750 LEN=259 [/COLOR]
[COLOR=#000000][  321.197697] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:7c:ff:4d:20:f0:98:08:00 SRC=192.168.178.1 DST=192.168.178.25 LEN=280 TOS=0x00 PREC=0x00 TTL=64 ID=12601 PROTO=UDP SPT=1900 DPT=47750 LEN=260 [/COLOR]
[COLOR=#000000][  321.215092] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:48:b0:2d:05:4d:f6:08:00 SRC=192.168.178.66 DST=192.168.178.25 LEN=289 TOS=0x00 PREC=0x00 TTL=64 ID=55395 DF PROTO=UDP SPT=32414 DPT=48713 LEN=269 [/COLOR]
[COLOR=#000000][  321.215255] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:18:74:2e:01:31:69:08:00 SRC=192.168.178.23 DST=192.168.178.25 LEN=383 TOS=0x00 PREC=0x00 TTL=64 ID=26494 DF PROTO=UDP SPT=32412 DPT=36807 LEN=363 [/COLOR]
[COLOR=#000000][  321.414355] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=01:00:5e:7f:ff:fa:00:18:ae:9a:88:41:08:00 SRC=192.168.178.52 DST=239.255.255.250 LEN=623 TOS=0x00 PREC=0x00 TTL=5 ID=12011 DF PROTO=UDP SPT=34455 DPT=3702 LEN=603 [/COLOR]
[COLOR=#000000][  322.193736] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:48:6d:bb:4e:e6:c5:08:00 SRC=192.168.178.60 DST=192.168.178.25 LEN=292 TOS=0x00 PREC=0x00 TTL=64 ID=19297 DF PROTO=UDP SPT=38072 DPT=47750 LEN=272 [/COLOR]
[COLOR=#000000][  322.295595] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:00:05:cd:a4:47:5f:08:00 SRC=192.168.178.24 DST=192.168.178.25 LEN=257 TOS=0x00 PREC=0x00 TTL=128 ID=3572 PROTO=UDP SPT=3911 DPT=47750 LEN=237 [/COLOR]
[COLOR=#000000][  341.193486] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:48:b0:2d:05:4d:f6:08:00 SRC=192.168.178.66 DST=192.168.178.25 LEN=516 TOS=0x00 PREC=0x00 TTL=64 ID=58007 DF PROTO=UDP SPT=45493 DPT=47750 LEN=496 [/COLOR]
[COLOR=#000000][  361.195325] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:7c:ff:4d:20:f0:98:08:00 SRC=192.168.178.1 DST=192.168.178.25 LEN=282 TOS=0x00 PREC=0x00 TTL=64 ID=15603 PROTO=UDP SPT=1900 DPT=47750 LEN=262 [/COLOR]
[COLOR=#000000][  368.708388] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=33:33:00:00:00:01:7c:ff:4d:20:f0:98:86:dd SRC=fe80:0000:0000:0000:7eff:4dff:fe20:f098 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=53805 DPT=53805 LEN=24 [/COLOR]
[COLOR=#000000][  381.197693] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:7c:ff:4d:20:f0:98:08:00 SRC=192.168.178.1 DST=192.168.178.25 LEN=282 TOS=0x00 PREC=0x00 TTL=64 ID=16181 PROTO=UDP SPT=1900 DPT=47750 LEN=262 [/COLOR]
[COLOR=#000000][  401.198720] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:7c:ff:4d:20:f0:98:08:00 SRC=192.168.178.1 DST=192.168.178.25 LEN=282 TOS=0x00 PREC=0x00 TTL=64 ID=17130 PROTO=UDP SPT=1900 DPT=47750 LEN=262 [/COLOR]
[COLOR=#000000][  421.198576] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:48:b0:2d:05:4d:f6:08:00 SRC=192.168.178.66 DST=192.168.178.25 LEN=516 TOS=0x00 PREC=0x00 TTL=64 ID=1038 DF PROTO=UDP SPT=36218 DPT=47750 LEN=496 [/COLOR]
[COLOR=#000000][  441.201602] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:7c:ff:4d:20:f0:98:08:00 SRC=192.168.178.1 DST=192.168.178.25 LEN=282 TOS=0x00 PREC=0x00 TTL=64 ID=19341 PROTO=UDP SPT=1900 DPT=47750 LEN=262 [/COLOR]
[COLOR=#000000][  461.202702] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:7c:ff:4d:20:f0:98:08:00 SRC=192.168.178.1 DST=192.168.178.25 LEN=282 TOS=0x00 PREC=0x00 TTL=64 ID=20071 PROTO=UDP SPT=1900 DPT=47750 LEN=262 [/COLOR]
[COLOR=#000000][  481.204028] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:7c:ff:4d:20:f0:98:08:00 SRC=192.168.178.1 DST=192.168.178.25 LEN=282 TOS=0x00 PREC=0x00 TTL=64 ID=20847 PROTO=UDP SPT=1900 DPT=47750 LEN=262 [/COLOR]
[COLOR=#000000][  501.205651] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:7c:ff:4d:20:f0:98:08:00 SRC=192.168.178.1 DST=192.168.178.25 LEN=282 TOS=0x00 PREC=0x00 TTL=64 ID=21563 PROTO=UDP SPT=1900 DPT=47750 LEN=262 [/COLOR]
[COLOR=#000000][  521.207363] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:7c:ff:4d:20:f0:98:08:00 SRC=192.168.178.1 DST=192.168.178.25 LEN=282 TOS=0x00 PREC=0x00 TTL=64 ID=22440 PROTO=UDP SPT=1900 DPT=47750 LEN=262 [/COLOR]
[COLOR=#000000][  541.207334] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:48:b0:2d:05:4d:f6:08:00 SRC=192.168.178.66 DST=192.168.178.25 LEN=516 TOS=0x00 PREC=0x00 TTL=64 ID=15901 DF PROTO=UDP SPT=57763 DPT=47750 LEN=496 [/COLOR]
[COLOR=#000000][  561.208084] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:48:b0:2d:05:4d:f6:08:00 SRC=192.168.178.66 DST=192.168.178.25 LEN=516 TOS=0x00 PREC=0x00 TTL=64 ID=19470 DF PROTO=UDP SPT=34193 DPT=47750 LEN=496 [/COLOR]
[COLOR=#000000][  581.210486] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:7c:ff:4d:20:f0:98:08:00 SRC=192.168.178.1 DST=192.168.178.25 LEN=282 TOS=0x00 PREC=0x00 TTL=64 ID=26122 PROTO=UDP SPT=1900 DPT=47750 LEN=262 [/COLOR]
[COLOR=#000000][  601.211911] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:7c:ff:4d:20:f0:98:08:00 SRC=192.168.178.1 DST=192.168.178.25 LEN=282 TOS=0x00 PREC=0x00 TTL=64 ID=26987 PROTO=UDP SPT=1900 DPT=47750 LEN=262 [/COLOR]
[COLOR=#000000][  605.216090] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:48:6d:bb:4e:e6:c5:08:00 SRC=192.168.178.60 DST=192.168.178.25 LEN=292 TOS=0x00 PREC=0x00 TTL=64 ID=19413 DF PROTO=UDP SPT=38072 DPT=47750 LEN=272 [/COLOR]
[COLOR=#000000][  605.347649] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:00:05:cd:a4:47:5f:08:00 SRC=192.168.178.24 DST=192.168.178.25 LEN=257 TOS=0x00 PREC=0x00 TTL=128 ID=4789 PROTO=UDP SPT=3911 DPT=47750 LEN=237 [/COLOR]
[COLOR=#000000][  605.366514] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:48:6d:bb:4e:e6:c5:08:00 SRC=192.168.178.60 DST=192.168.178.25 LEN=292 TOS=0x00 PREC=0x00 TTL=64 ID=19414 DF PROTO=UDP SPT=38072 DPT=47750 LEN=272 [/COLOR]
[COLOR=#000000][  606.004457] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:48:6d:bb:4e:e6:c5:08:00 SRC=192.168.178.60 DST=192.168.178.25 LEN=292 TOS=0x00 PREC=0x00 TTL=64 ID=19415 DF PROTO=UDP SPT=38072 DPT=15321 LEN=272 [/COLOR]
[COLOR=#000000][  606.146598] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=01:00:5e:7f:ff:fa:00:18:ae:9a:88:41:08:00 SRC=192.168.178.52 DST=239.255.255.250 LEN=152 TOS=0x00 PREC=0x00 TTL=1 ID=25303 DF PROTO=UDP SPT=37020 DPT=37020 LEN=132 [/COLOR]
[COLOR=#000000][  606.154771] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:48:6d:bb:4e:e6:c5:08:00 SRC=192.168.178.60 DST=192.168.178.25 LEN=292 TOS=0x00 PREC=0x00 TTL=64 ID=19416 DF PROTO=UDP SPT=38072 DPT=15321 LEN=272 [/COLOR]
[COLOR=#000000][  606.258652] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:48:b0:2d:05:4d:f6:08:00 SRC=192.168.178.66 DST=192.168.178.25 LEN=289 TOS=0x00 PREC=0x00 TTL=64 ID=24762 DF PROTO=UDP SPT=32414 DPT=48713 LEN=269 [/COLOR]
[COLOR=#000000][  606.258691] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:18:74:2e:01:31:69:08:00 SRC=192.168.178.23 DST=192.168.178.25 LEN=383 TOS=0x00 PREC=0x00 TTL=64 ID=40848 DF PROTO=UDP SPT=32412 DPT=36807 LEN=363 [/COLOR]
[COLOR=#000000][  606.425358] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:48:b0:2d:05:4d:f6:08:00 SRC=192.168.178.66 DST=192.168.178.25 LEN=516 TOS=0x00 PREC=0x00 TTL=64 ID=24773 DF PROTO=UDP SPT=54201 DPT=15321 LEN=496 [/COLOR]
[COLOR=#000000][  606.922421] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:00:05:cd:a4:47:5f:08:00 SRC=192.168.178.24 DST=192.168.178.25 LEN=257 TOS=0x00 PREC=0x00 TTL=128 ID=4795 PROTO=UDP SPT=3911 DPT=15321 LEN=237 [/COLOR]
[COLOR=#000000][  626.261119] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:48:b0:2d:05:4d:f6:08:00 SRC=192.168.178.66 DST=192.168.178.25 LEN=289 TOS=0x00 PREC=0x00 TTL=64 ID=27296 DF PROTO=UDP SPT=32414 DPT=48713 LEN=269 [/COLOR]
[COLOR=#000000][  645.352258] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:48:6d:bb:4e:e6:c5:08:00 SRC=192.168.178.60 DST=192.168.178.25 LEN=292 TOS=0x00 PREC=0x00 TTL=64 ID=19433 DF PROTO=UDP SPT=38072 DPT=47750 LEN=272 [/COLOR]
[COLOR=#000000][  666.268906] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:48:b0:2d:05:4d:f6:08:00 SRC=192.168.178.66 DST=192.168.178.25 LEN=289 TOS=0x00 PREC=0x00 TTL=64 ID=32661 DF PROTO=UDP SPT=32414 DPT=48713 LEN=269 [/COLOR]
[COLOR=#000000][  686.271769] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:48:b0:2d:05:4d:f6:08:00 SRC=192.168.178.66 DST=192.168.178.25 LEN=289 TOS=0x00 PREC=0x00 TTL=64 ID=35876 DF PROTO=UDP SPT=32414 DPT=48713 LEN=269 [/COLOR]
[COLOR=#000000][  706.275324] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:48:b0:2d:05:4d:f6:08:00 SRC=192.168.178.66 DST=192.168.178.25 LEN=289 TOS=0x00 PREC=0x00 TTL=64 ID=37216 DF PROTO=UDP SPT=32414 DPT=48713 LEN=269 [/COLOR]
[COLOR=#000000][  725.877406] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:7c:ff:4d:20:f0:98:08:00 SRC=212.21.153.151 DST=192.168.178.25 LEN=48 TOS=0x00 PREC=0x00 TTL=51 ID=58958 PROTO=UDP SPT=23462 DPT=51413 LEN=28 [/COLOR]
[COLOR=#000000][  746.280973] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:48:b0:2d:05:4d:f6:08:00 SRC=192.168.178.66 DST=192.168.178.25 LEN=289 TOS=0x00 PREC=0x00 TTL=64 ID=42321 DF PROTO=UDP SPT=32414 DPT=48713 LEN=269 [/COLOR]
[COLOR=#000000][  765.503001] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:48:6d:bb:4e:e6:c5:08:00 SRC=192.168.178.60 DST=192.168.178.25 LEN=292 TOS=0x00 PREC=0x00 TTL=64 ID=19481 DF PROTO=UDP SPT=38072 DPT=47750 LEN=272 [/COLOR]
[COLOR=#000000][  785.606634] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:00:05:cd:a4:47:5f:08:00 SRC=192.168.178.24 DST=192.168.178.25 LEN=257 TOS=0x00 PREC=0x00 TTL=128 ID=5515 PROTO=UDP SPT=3911 DPT=47750 LEN=237 [/COLOR]
[COLOR=#000000][  805.222934] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:48:6d:bb:4e:e6:c5:08:00 SRC=192.168.178.60 DST=192.168.178.25 LEN=292 TOS=0x00 PREC=0x00 TTL=64 ID=19500 DF PROTO=UDP SPT=38072 DPT=44942 LEN=272 [/COLOR]
[COLOR=#000000][  825.226660] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:48:6d:bb:4e:e6:c5:08:00 SRC=192.168.178.60 DST=192.168.178.25 LEN=292 TOS=0x00 PREC=0x00 TTL=64 ID=19509 DF PROTO=UDP SPT=38072 DPT=47750 LEN=272 [/COLOR]
[COLOR=#000000][  846.293858] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:48:b0:2d:05:4d:f6:08:00 SRC=192.168.178.66 DST=192.168.178.25 LEN=289 TOS=0x00 PREC=0x00 TTL=64 ID=52333 DF PROTO=UDP SPT=32414 DPT=48713 LEN=269 [/COLOR]
[COLOR=#000000][  865.235483] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:00:05:cd:a4:47:5f:08:00 SRC=192.168.178.24 DST=192.168.178.25 LEN=257 TOS=0x00 PREC=0x00 TTL=128 ID=5873 PROTO=UDP SPT=3911 DPT=44942 LEN=237 [/COLOR]
[COLOR=#000000][  885.226912] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=01:00:5e:7f:ff:fa:00:18:ae:9a:88:41:08:00 SRC=192.168.178.52 DST=239.255.255.250 LEN=623 TOS=0x00 PREC=0x00 TTL=5 ID=41339 DF PROTO=UDP SPT=34455 DPT=3702 LEN=603 [/COLOR]
[COLOR=#000000][  905.327570] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=01:00:5e:7f:ff:fa:00:18:ae:9a:88:41:08:00 SRC=192.168.178.52 DST=239.255.255.250 LEN=623 TOS=0x00 PREC=0x00 TTL=5 ID=42055 DF PROTO=UDP SPT=34455 DPT=3702 LEN=603 [/COLOR]
[/FONT]
```[FONT=arial]


[/FONT][/SIZE][COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]```

[COLOR=#000000][FONT=Menlo][SIZE=2][FONT=arial]sudo tail -n 50 /var/log/syslog[/FONT][/SIZE][/FONT][/COLOR]
[SIZE=2][FONT=arial]
[/FONT][/SIZE][COLOR=#000000][FONT=Menlo][SIZE=2][FONT=arial]Jul 25 16:00:01 homeserver crontab[6497]: (root) LIST (root)[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][SIZE=2][FONT=arial]Jul 25 16:00:11 homeserver kernel: [  666.268906] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:48:b0:2d:05:4d:f6:08:00 SRC=192.168.178.66 DST=192.168.178.25 LEN=289 TOS=0x00 PREC=0x00 TTL=64 ID=32661 DF PROTO=UDP SPT=32414 DPT=48713 LEN=269 [/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][SIZE=2][FONT=arial]Jul 25 16:00:31 homeserver kernel: [  686.271769] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:48:b0:2d:05:4d:f6:08:00 SRC=192.168.178.66 DST=192.168.178.25 LEN=289 TOS=0x00 PREC=0x00 TTL=64 ID=35876 DF PROTO=UDP SPT=32414 DPT=48713 LEN=269 [/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][SIZE=2][FONT=arial]Jul 25 16:00:51 homeserver kernel: [  706.275324] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:48:b0:2d:05:4d:f6:08:00 SRC=192.168.178.66 DST=192.168.178.25 LEN=289 TOS=0x00 PREC=0x00 TTL=64 ID=37216 DF PROTO=UDP SPT=32414 DPT=48713 LEN=269 [/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][SIZE=2][FONT=arial]Jul 25 16:01:11 homeserver kernel: [  725.877406] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:7c:ff:4d:20:f0:98:08:00 SRC=212.21.153.151 DST=192.168.178.25 LEN=48 TOS=0x00 PREC=0x00 TTL=51 ID=58958 PROTO=UDP SPT=23462 DPT=51413 LEN=28 [/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][SIZE=2][FONT=arial]Jul 25 16:01:31 homeserver kernel: [  746.280973] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:48:b0:2d:05:4d:f6:08:00 SRC=192.168.178.66 DST=192.168.178.25 LEN=289 TOS=0x00 PREC=0x00 TTL=64 ID=42321 DF PROTO=UDP SPT=32414 DPT=48713 LEN=269 [/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][SIZE=2][FONT=arial]Jul 25 16:01:50 homeserver kernel: [  765.503001] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:48:6d:bb:4e:e6:c5:08:00 SRC=192.168.178.60 DST=192.168.178.25 LEN=292 TOS=0x00 PREC=0x00 TTL=64 ID=19481 DF PROTO=UDP SPT=38072 DPT=47750 LEN=272 [/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][SIZE=2][FONT=arial]Jul 25 16:02:10 homeserver kernel: [  785.606634] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:00:05:cd:a4:47:5f:08:00 SRC=192.168.178.24 DST=192.168.178.25 LEN=257 TOS=0x00 PREC=0x00 TTL=128 ID=5515 PROTO=UDP SPT=3911 DPT=47750 LEN=237 [/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][SIZE=2][FONT=arial]Jul 25 16:02:30 homeserver kernel: [  805.222934] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:48:6d:bb:4e:e6:c5:08:00 SRC=192.168.178.60 DST=192.168.178.25 LEN=292 TOS=0x00 PREC=0x00 TTL=64 ID=19500 DF PROTO=UDP SPT=38072 DPT=44942 LEN=272 [/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][SIZE=2][FONT=arial]Jul 25 16:02:34 homeserver systemd[1421]: Started Application launched by gnome-shell.[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][SIZE=2][FONT=arial]Jul 25 16:02:34 homeserver dbus-daemon[1523]: [session uid=1000 pid=1523] Activating via systemd: service name='org.gnome.Terminal' unit='gnome-terminal-server.service' requested by ':1.92' (uid=1000 pid=7419 comm="/usr/bin/gnome-terminal.real --window " label="unconfined")[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][SIZE=2][FONT=arial]Jul 25 16:02:34 homeserver systemd[1421]: Created slice apps.slice.[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][SIZE=2][FONT=arial]Jul 25 16:02:34 homeserver systemd[1421]: Created slice apps-org.gnome.Terminal.slice.[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][SIZE=2][FONT=arial]Jul 25 16:02:34 homeserver systemd[1421]: Starting GNOME Terminal Server...[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][SIZE=2][FONT=arial]Jul 25 16:02:34 homeserver dbus-daemon[1523]: [session uid=1000 pid=1523] Successfully activated service 'org.gnome.Terminal'[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][SIZE=2][FONT=arial]Jul 25 16:02:34 homeserver systemd[1421]: Started GNOME Terminal Server.[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][SIZE=2][FONT=arial]Jul 25 16:02:35 homeserver systemd[1421]: Started VTE child process 7431 launched by gnome-terminal-server process 7422.[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][SIZE=2][FONT=arial]Jul 25 16:02:35 homeserver systemd[1421]: gnome-launched-org.gnome.Terminal.desktop-7416.scope: Succeeded.[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][SIZE=2][FONT=arial]Jul 25 16:02:50 homeserver kernel: [  825.226660] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:48:6d:bb:4e:e6:c5:08:00 SRC=192.168.178.60 DST=192.168.178.25 LEN=292 TOS=0x00 PREC=0x00 TTL=64 ID=19509 DF PROTO=UDP SPT=38072 DPT=47750 LEN=272 [/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][SIZE=2][FONT=arial]Jul 25 16:03:11 homeserver kernel: [  846.293858] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:48:b0:2d:05:4d:f6:08:00 SRC=192.168.178.66 DST=192.168.178.25 LEN=289 TOS=0x00 PREC=0x00 TTL=64 ID=52333 DF PROTO=UDP SPT=32414 DPT=48713 LEN=269 [/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][SIZE=2][FONT=arial]Jul 25 16:03:30 homeserver kernel: [  865.235483] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:00:05:cd:a4:47:5f:08:00 SRC=192.168.178.24 DST=192.168.178.25 LEN=257 TOS=0x00 PREC=0x00 TTL=128 ID=5873 PROTO=UDP SPT=3911 DPT=44942 LEN=237 [/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][SIZE=2][FONT=arial]Jul 25 16:03:50 homeserver kernel: [  885.226912] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=01:00:5e:7f:ff:fa:00:18:ae:9a:88:41:08:00 SRC=192.168.178.52 DST=239.255.255.250 LEN=623 TOS=0x00 PREC=0x00 TTL=5 ID=41339 DF PROTO=UDP SPT=34455 DPT=3702 LEN=603 [/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][SIZE=2][FONT=arial]Jul 25 16:04:05 homeserver systemd[1]: Starting Cleanup of Temporary Directories...[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][SIZE=2][FONT=arial]Jul 25 16:04:05 homeserver systemd[1]: systemd-tmpfiles-clean.service: Succeeded.[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][SIZE=2][FONT=arial]Jul 25 16:04:05 homeserver systemd[1]: Finished Cleanup of Temporary Directories.[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][SIZE=2][FONT=arial]Jul 25 16:04:06 homeserver systemd[1]: Started Session 7 of user freeflyer.[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][SIZE=2][FONT=arial]Jul 25 16:04:10 homeserver kernel: [  905.327570] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=01:00:5e:7f:ff:fa:00:18:ae:9a:88:41:08:00 SRC=192.168.178.52 DST=239.255.255.250 LEN=623 TOS=0x00 PREC=0x00 TTL=5 ID=42055 DF PROTO=UDP SPT=34455 DPT=3702 LEN=603 [/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][SIZE=2][FONT=arial]Jul 25 16:04:30 homeserver kernel: [  925.235195] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:48:6d:bb:4e:e6:c5:08:00 SRC=192.168.178.60 DST=192.168.178.25 LEN=292 TOS=0x00 PREC=0x00 TTL=64 ID=19541 DF PROTO=UDP SPT=38072 DPT=47750 LEN=272 [/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][SIZE=2][FONT=arial]Jul 25 16:04:50 homeserver kernel: [  945.545216] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=01:00:5e:7f:ff:fa:00:18:ae:9a:88:41:08:00 SRC=192.168.178.52 DST=239.255.255.250 LEN=623 TOS=0x00 PREC=0x00 TTL=5 ID=43894 DF PROTO=UDP SPT=34455 DPT=3702 LEN=603 [/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][SIZE=2][FONT=arial]Jul 25 16:05:10 homeserver kernel: [  965.654703] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=01:00:5e:7f:ff:fa:00:18:ae:9a:88:41:08:00 SRC=192.168.178.52 DST=239.255.255.250 LEN=623 TOS=0x00 PREC=0x00 TTL=5 ID=44952 DF PROTO=UDP SPT=34455 DPT=3702 LEN=603 [/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][SIZE=2][FONT=arial]Jul 25 16:05:14 homeserver kernel: [  968.695555] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=33:33:00:00:00:01:7c:ff:4d:20:f0:98:86:dd SRC=fe80:0000:0000:0000:7eff:4dff:fe20:f098 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=53805 DPT=53805 LEN=24 [/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][SIZE=2][FONT=arial]Jul 25 16:05:30 homeserver kernel: [  985.235897] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:48:6d:bb:4e:e6:c5:08:00 SRC=192.168.178.60 DST=192.168.178.25 LEN=292 TOS=0x00 PREC=0x00 TTL=64 ID=19569 DF PROTO=UDP SPT=38072 DPT=47750 LEN=272 [/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][SIZE=2][FONT=arial]Jul 25 16:05:51 homeserver kernel: [ 1005.954243] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=01:00:5e:7f:ff:fa:00:18:ae:9a:88:41:08:00 SRC=192.168.178.52 DST=239.255.255.250 LEN=623 TOS=0x00 PREC=0x00 TTL=5 ID=47386 DF PROTO=UDP SPT=34455 DPT=3702 LEN=603 [/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][SIZE=2][FONT=arial]Jul 25 16:06:11 homeserver kernel: [ 1026.102771] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=01:00:5e:7f:ff:fa:00:18:ae:9a:88:41:08:00 SRC=192.168.178.52 DST=239.255.255.250 LEN=623 TOS=0x00 PREC=0x00 TTL=5 ID=48731 DF PROTO=UDP SPT=34455 DPT=3702 LEN=603 [/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][SIZE=2][FONT=arial]Jul 25 16:06:31 homeserver kernel: [ 1045.759553] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:48:b0:2d:05:4d:f6:08:00 SRC=192.168.178.66 DST=192.168.178.25 LEN=516 TOS=0x00 PREC=0x00 TTL=64 ID=16251 DF PROTO=UDP SPT=45758 DPT=35737 LEN=496 [/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][SIZE=2][FONT=arial]Jul 25 16:06:51 homeserver kernel: [ 1066.324931] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:48:b0:2d:05:4d:f6:08:00 SRC=192.168.178.66 DST=192.168.178.25 LEN=289 TOS=0x00 PREC=0x00 TTL=64 ID=19523 DF PROTO=UDP SPT=32414 DPT=48713 LEN=269 [/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][SIZE=2][FONT=arial]Jul 25 16:07:10 homeserver kernel: [ 1085.277173] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:7c:ff:4d:20:f0:98:08:00 SRC=107.181.189.46 DST=192.168.178.25 LEN=132 TOS=0x00 PREC=0x00 TTL=48 ID=50892 PROTO=UDP SPT=51515 DPT=51413 LEN=112 [/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][SIZE=2][FONT=arial]Jul 25 16:07:26 homeserver kernel: [ 1100.702279] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=01:00:5e:7f:ff:fa:00:18:ae:9a:88:41:08:00 SRC=192.168.178.52 DST=239.255.255.250 LEN=152 TOS=0x00 PREC=0x00 TTL=1 ID=52043 DF PROTO=UDP SPT=37020 DPT=37020 LEN=132 [/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][SIZE=2][FONT=arial]Jul 25 16:07:26 homeserver kernel: [ 1101.238985] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:7c:ff:4d:20:f0:98:08:00 SRC=192.168.178.1 DST=192.168.178.25 LEN=282 TOS=0x00 PREC=0x00 TTL=64 ID=53437 PROTO=UDP SPT=1900 DPT=47750 LEN=262 [/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][SIZE=2][FONT=arial]Jul 25 16:07:26 homeserver kernel: [ 1101.240054] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:7c:ff:4d:20:f0:98:08:00 SRC=192.168.178.1 DST=192.168.178.25 LEN=281 TOS=0x00 PREC=0x00 TTL=64 ID=53438 PROTO=UDP SPT=1900 DPT=47750 LEN=261 [/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][SIZE=2][FONT=arial]Jul 25 16:07:26 homeserver kernel: [ 1101.240909] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:7c:ff:4d:20:f0:98:08:00 SRC=192.168.178.1 DST=192.168.178.25 LEN=286 TOS=0x00 PREC=0x00 TTL=64 ID=53439 PROTO=UDP SPT=1900 DPT=47750 LEN=266 [/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][SIZE=2][FONT=arial]Jul 25 16:07:26 homeserver kernel: [ 1101.241870] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:7c:ff:4d:20:f0:98:08:00 SRC=192.168.178.1 DST=192.168.178.25 LEN=279 TOS=0x00 PREC=0x00 TTL=64 ID=53440 PROTO=UDP SPT=1900 DPT=47750 LEN=259 [/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][SIZE=2][FONT=arial]Jul 25 16:07:26 homeserver kernel: [ 1101.242823] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:7c:ff:4d:20:f0:98:08:00 SRC=192.168.178.1 DST=192.168.178.25 LEN=280 TOS=0x00 PREC=0x00 TTL=64 ID=53441 PROTO=UDP SPT=1900 DPT=47750 LEN=260 [/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][SIZE=2][FONT=arial]Jul 25 16:07:26 homeserver kernel: [ 1101.330221] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:48:b0:2d:05:4d:f6:08:00 SRC=192.168.178.66 DST=192.168.178.25 LEN=289 TOS=0x00 PREC=0x00 TTL=64 ID=23615 DF PROTO=UDP SPT=32414 DPT=48713 LEN=269 [/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][SIZE=2][FONT=arial]Jul 25 16:07:26 homeserver kernel: [ 1101.330288] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:18:74:2e:01:31:69:08:00 SRC=192.168.178.23 DST=192.168.178.25 LEN=383 TOS=0x00 PREC=0x00 TTL=64 ID=1436 DF PROTO=UDP SPT=32412 DPT=36807 LEN=363 [/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][SIZE=2][FONT=arial]Jul 25 16:07:27 homeserver kernel: [ 1102.433533] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:48:b0:2d:05:4d:f6:08:00 SRC=192.168.178.66 DST=192.168.178.25 LEN=516 TOS=0x00 PREC=0x00 TTL=64 ID=23889 DF PROTO=UDP SPT=40840 DPT=47750 LEN=496 [/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][SIZE=2][FONT=arial]Jul 25 16:07:28 homeserver kernel: [ 1102.730541] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=01:00:5e:7f:ff:fa:00:18:ae:9a:88:41:08:00 SRC=192.168.178.52 DST=239.255.255.250 LEN=623 TOS=0x00 PREC=0x00 TTL=5 ID=52172 DF PROTO=UDP SPT=34455 DPT=3702 LEN=603 [/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][SIZE=2][FONT=arial]Jul 25 16:07:46 homeserver kernel: [ 1121.240146] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:7c:ff:4d:20:f0:98:08:00 SRC=192.168.178.1 DST=192.168.178.25 LEN=282 TOS=0x00 PREC=0x00 TTL=64 ID=54554 PROTO=UDP SPT=1900 DPT=47750 LEN=262 [/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][SIZE=2][FONT=arial]Jul 25 16:08:06 homeserver kernel: [ 1141.068427] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=48:4d:7e:ee:a4:aa:00:05:cd:a4:47:5f:08:00 SRC=192.168.178.24 DST=192.168.178.25 LEN=257 TOS=0x00 PREC=0x00 TTL=128 ID=6967 PROTO=UDP SPT=3911 DPT=15321 LEN=237 [/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][SIZE=2][FONT=arial]Jul 25 16:08:26 homeserver kernel: [ 1160.900741] [UFW BLOCK] IN=enp0s31f6 OUT= MAC=01:00:5e:7f:ff:fa:00:18:ae:9a:88:41:08:00 SRC=192.168.178.52 DST=239.255.255.250 LEN=152 TOS=0x00 PREC=0x00 TTL=1 ID=55093 DF PROTO=UDP SPT=37020 DPT=37020 LEN=132 [/FONT][/SIZE][/FONT][/COLOR]

```[SIZE=2][FONT=arial]

[/FONT][/SIZE]```
free -m
              total        used        free      shared  buff/cache   available
Mem:           7828        1564        4578         287        1685        5684
Swap:          4095           0        4095

```[SIZE=2][FONT=arial]
[/FONT][/SIZE]

---

### Post by CharlesA on 2021-07-25
I don't think it's a firewall issue, because we got the SIGTERM error.

What you can do is try running this command and see if it returns anything.

```
sudo grep -i -r 'out of memory' /var/log/
```

It might complain that a couple files are binaries, but that's not what we are looking for.

If that doesn't find anything, login to the server and install htop and run it:
```
htop
```

Then rerun the rsync and monitor the memory usage of your server to see how it behaves.

---

### Post by freeflyjohn on 2021-07-25
> **CharlesA said:**
> I don't think it's a firewall issue, because we got the SIGTERM error.

What you can do is try running this command and see if it returns anything.

```
sudo grep -i -r 'out of memory' /var/log/
```

It might complain that a couple files are binaries, but that's not what we are looking for.



Thanks CharlesA, this is the result from the memory check...

```


sudo grep -i -r 'out of memory' /var/log/

/var/log/auth.log:Jul 25 16:32:37 homeserver sudo: freeflyer : TTY=pts/0 ; PWD=/home/freeflyer ; USER=root ; COMMAND=/usr/bin/grep -i -r out of memory /var/log/
Binary file /var/log/journal/527904bf8ab14736a9675ba0f4111c03/system.journal matches


```

---

### Post by CharlesA on 2021-07-25
That's what I expected - no errors about memory.

Can you run a test by running rsync locally and see if it still fails? Assuming you have enough free disk space on the mac.

---

### Post by freeflyjohn on 2021-07-25
> **CharlesA said:**
> That's what I expected - no errors about memory.

Can you run a test by running rsync locally and see if it still fails? Assuming you have enough free disk space on the mac.

Thanks CharlesA, I ran the following command so that it backed up to a destination folder (called testrsync) on the Mac ...

```

rsync --archive --verbose --itemize-changes -b --backup-dir="deleted_$(date +\%Y-\%m-\%d)" --delete --exclude-from /Users/username/rsync/rsync-exclude-list.txt /Users/username /Users/username/testrsync 2>&1 | tee -a logfile.txt

```

It worked fine without any issues.

So for some reason, rsycn fails when the destination is the server.

But how do I find out why and how do I fix it ?

---

### Post by CharlesA on 2021-07-25
> **freeflyjohn said:**
> Thanks CharlesA, I ran the following command so that it backed up to a destination folder (called testrsync) on the Mac ...

```

rsync --archive --verbose --itemize-changes -b --backup-dir="deleted_$(date +\%Y-\%m-\%d)" --delete --exclude-from /Users/username/rsync/rsync-exclude-list.txt /Users/username /Users/username/testrsync 2>&1 | tee -a logfile.txt

```

It worked fine without any issues.

So for some reason, rsycn fails when the destination is the server.

But how do I find out why and how do I fix it ?

That's good news! At least that means the command is working correctly.

So, you have the server's folder mounted to /Users/myusername/Volumes/Storage/Backup/Mac/rsync right?

How is that mounted?

As for troubleshooting, you can run this command from the server and monitor it while the rsync is running.

```
watch 'dmesg | grep -v UFW | tail -n 50'
```

---

### Post by HermanAB on 2021-07-25
Hmm, I am one of the folks who use SSH for everything.  So I backup my Macs over SSH with rsync and that works OK for me.

---

### Post by CharlesA on 2021-07-25
> **HermanAB said:**
> Hmm, I am one of the folks who use SSH for everything.  So I backup my Macs over SSH with rsync and that works OK for me.

Same here. That's probably the next step if this doesn't work.

I'm trying to figure out if it's the way they are transferring the files via local mount instead of SSH that is the problem or if it's something else.

---

### Post by freeflyjohn on 2021-07-25
> **CharlesA said:**
> That's good news! At least that means the command is working correctly.

So, you have the server's folder mounted to /Users/myusername/Volumes/Storage/Backup/Mac/rsync right?

How is that mounted?

As for troubleshooting, you can run this command from the server and monitor it while the rsync is running.

```
watch 'dmesg | grep -v UFW | tail -n 50'
```

The server appears in Finder (on the Mac) as 'HOMESERVER' as shown in the screenshot below...

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=288871&stc=1[/IMG]

When I click on a drive such as 'Storage' the mount symbol appears.

However, it is temperamental because sometimes it works, sometimes it doesn't.

When it doesn't work, I have to use the Finder menu Go->Connect to server...

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=288872&stc=1[/IMG]

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=288873&stc=1[/IMG]

My samba config (/etc/samba/smb.conf) is as follows - I think it's supposed to advertise the server on the network (?)...

```

security = user
username map = /etc/samba/smbusers
name resolve order = bcast wins lmhosts


netbios name = HomeServerSMB


[Plex]
comment = Plex Media Server
path = /media/plex
read only = no
writable = yes
[General]
comment = General server
path = /media/general
read only = no
writable = yes
[Time machine]
comment = Time machine backup
path = /media/timemachine
read only = no
writable = yes
[Home]
comment = Ubuntu Home
path = /home
read only = no
writable = yes
[Storage]
comment = Storage
path = /media/storage
read only = no
writable = yes

```

I don't know whether its a Mac issue, because when I use a Windows machine (my work laptop) it always seems to connect to the server without a problem.

---

### Post by freeflyjohn on 2021-07-25
> **HermanAB said:**
> Hmm, I am one of the folks who use SSH for everything.  So I backup my Macs over SSH with rsync and that works OK for me.

I didn't think there would be any point in using SSH, because I am backing up over my internal LAN network so its safe.

I thought SSH was more for remote connections, when accessing your sever from outside the LAN network ?

I do have SSH setup and running which I use for remote access.

---

### Post by CharlesA on 2021-07-25
> **freeflyjohn said:**
> I didn't think there would be any point in using SSH, because I am backing up over my internal LAN network so its safe.

I thought SSH was more for remote connections, when accessing your sever from outside the LAN network ?

I do have SSH setup and running which I use for remote access.

You can use SSH to do file transfers even on local connections. It's just the protocol in use.

I use it when I am backing up to my second server.

Instead of trying to use the mounted smb share, try it over SSH:

```
rsync --archive --verbose --itemize-changes -b --backup-dir="deleted_$(date +\%Y-\%m-\%d)" --delete --exclude-from /Users/username/rsync/rsync-exclude-list.txt /Users/username **user@hostname:**/Users/username/testrsync 2>&1 | tee -a logfile.txt
```

---

### Post by freeflyjohn on 2021-07-25
> **CharlesA said:**
> You can use SSH to do file transfers even on local connections. It's just the protocol in use.

I use it when I am backing up to my second server.

Instead of trying to use the mounted smb share, try it over SSH:

```
rsync --archive --verbose --itemize-changes -b --backup-dir="deleted_$(date +\%Y-\%m-\%d)" --delete --exclude-from /Users/username/rsync/rsync-exclude-list.txt /Users/username **user@hostname:**/Users/username/testrsync 2>&1 | tee -a logfile.txt
```

Thanks CharlesA I'll give that a go

I have changed the SSH default port so when I use SSH I have to define the port number (e.g. ssh user@hostname -p 12345), so what would the syntax need to be in the example you gave ?

Would it be **user@hostname -p 12345:**/Users/username/testrsync ?

Would it slow the transfer speed using SSH, doesn't it have to encrypt the data and then decrypt it at the server end ?

Just seems an additional process to secure the data which on an internal network seems unnecessary, or am I missing something ?

If it does work with SSH, then I wonder why it won't work directly with samba ?

---

### Post by CharlesA on 2021-07-25
> **freeflyjohn said:**
> Thanks CharlesA I'll give that a go

I have changed the SSH default port so when I use SSH I have to define the port number (e.g. ssh user@hostname -p 12345), so what would the syntax need to be in the example you gave ?

Would it be **user@hostname -p 12345:**/Users/username/testrsync ?

It'll be a little different if you are not using the default port.

You'll need to add **-e "ssh -p 2222"** like the example below, so rsync knows what port to connect on.

```
rsync -avz -e "ssh -p 2232" SRC/ user@remote.host:/DEST/ 
```

> Would it slow the transfer speed using SSH, doesn't it have to encrypt the data and then decrypt it at the server end ?

Just seems an additional process to secure the data which on an internal network seems unnecessary, or am I missing something ?

I haven't really noticed much of a performance hit when transferring files over ssh. It can be slower than SMB, but it shouldn't be a huge difference.

It may be unnecessary, but I find it a lot less complicated than trying to set up a mounted SMB share.

> If it does work with SSH, then I wonder why it won't work directly with samba ?

If it works over SSH, then we know something with Samba is causing it to fail.

---

### Post by freeflyjohn on 2021-07-25
Found how to specify SSH port number using:
```

rsync -a -b [COLOR=#FF0000]--rsh='ssh -p 12345'[/COLOR] --progress --backup-dir="deleted_$(date +\%Y-\%m-\%d)" --delete --exclude-from /Users/username/rsync/rsync-exclude-list.txt /Users/username user@hostname:/Users/username/testrsync 2>&1 | tee -a logfile.txt

```

---

### Post by freeflyjohn on 2021-07-25
Thanks all, especially to CharlesA :)

SSH worked without any problems, using a wired network connection I managed to backup the Downloads and Desktop folders on the Mac to the server fairly quickly which is impressive considering the amount of time its taken to get it working !

I'm now uncommenting folders from the exclude list one by one and performing an rsync each time.

So it seems samba was the problem ?

From the sounds of it most of you are using SSH with rsync, so I may as well stick with SSH and forget about samba ?

Im just curious now as to why samba didnt work ?  

Is samba not very good, is that the reason why the Mac doesnt always connect to the server without having to use the "Go->Connect to server..." method ?

---

### Post by CharlesA on 2021-07-25
> **freeflyjohn said:**
> Thanks all, especially to CharlesA :)

SSH worked without any problems, using a wired network connection I managed to backup the Downloads and Desktop folders on the Mac to the server fairly quickly which is impressive considering the amount of time its taken to get it working !

I'm now uncommenting folders from the exclude list one by one and performing an rsync each time.

That's good news.

> So it seems samba was the problem ?

From the sounds of it most of you are using SSH with rsync, so I may as well stick with SSH and forget about samba ?

Im just curious now as to why samba didnt work ?  

Is samba not very good, is that the reason why the Mac doesnt always connect to the server without having to use the "Go->Connect to server..." method ?


Possibly. It's very odd through. Do you have anything in the samba logs in /var/logs?

I haven't had much experience with macs, so I can't tell you if that behavior is expected or not (but I would lean toward not).

---

### Post by scorp123 on 2021-07-26
> **HermanAB said:**
> Hmm, I am one of the folks who use SSH for everything.  So I backup my Macs over SSH with rsync and that works OK for me.

Same here. SSH for everything, zero need or use for anything else.

---

