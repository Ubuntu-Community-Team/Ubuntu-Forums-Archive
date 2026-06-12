---
title: "How to preserve all timestamps ?"
date: 2023-01-07
forum: General Help
---

### Post by anmac1789 on 2023-01-07
Is there a way to preserve exact timestamps from android phone (galaxy s8) to ubuntu 22.04 to windows 10/11 pro ? I want to preserve birth time (creation time), changed time, modified time and access time. Is this possible for both files and folders ?

---

### Post by HermanAB on 2023-01-07
Timestamps are functions of the filesystems.  The FS with the least features would be FAT and NTFS.  

Note that NTFS actually has all the time stamps that you want to preserve, but the common tools do not display them.

---

### Post by anmac1789 on 2023-01-07
when transferring files or folders, FAT has a precision of 2 seconds, NTFS has 100 nanoseconds but one of the dates always changes when transferring between filesystems. Android folders and files also changes when transferring to windows. I'm frustrated that there is no consistency. Even windows seems to have a subsystem for linux but the timestamp issue is still there. Ugh.

---

### Post by TheFu on 2023-01-07
I'd use 
```
$ sudo rsync -avz source target
```
'rsync' is available for android and uses 'ssh'-based connection and credentials and encryption by default.

That command should keep the ctime, mtime, and atime  for all files correct.  You can pull or push with rsync.  Using sudo probably means you'll be pulling from your Linux desktop.

---

### Post by anmac1789 on 2023-01-08
> **TheFu said:**
> I'd use 
```
$ sudo rsync -avz source target
```
'rsync' is available for android and uses 'ssh'-based connection and credentials and encryption by default.

That command should keep the ctime, mtime, and atime  for all files correct.  You can pull or push with rsync.  Using sudo probably means you'll be pulling from your Linux desktop.

so ctime is change time right ? what about birth time which is equivalent of date created on windows 10/11 pro

The thing is that I am using windows 11 pro and wanting to copy files from android to windows machine since traditional windows methods can't preserve timestamps accurately.

---

### Post by HermanAB on 2023-01-08
Another way is to wrap the files into a tar archive.

---

### Post by TheFu on 2023-01-08
> **anmac1789 said:**
> so ctime is change time right ? what about birth time which is equivalent of date created on windows 10/11 pro
 
Wrong.  ctime is creation time.  
mtime is modified time.
The manpages are clear on this.

Win10+ has support for ssh and there are rsync programs for Windows going back to the mid-1990s.  Try it. See what happens. Should be 10 minutes of effort.

---

### Post by philhughes on 2023-01-08
From [1]:

Standard POSIX files have three timestamps:
- the access timestamp (atime) of the last read
- the modification timestamp (mtime) of the last write
- and the status change timestamp (ctime) of the last change to the file’s meta-information.

 Some file systems support a fourth time:
 - the birth timestamp (birthtime) of when the file was created; by definition, birthtime never changes.
 
Birth time is sometimes known as creation time (crtime).

For example:

```
$ stat afile
  File: afile
  Size: 0         	Blocks: 0          IO Block: 4096   regular empty file
Device: 10302h/66306d	Inode: 52695697    Links: 1
Access: (0600/-rw-------)  Uid: ( 1000/    phil)   Gid: ( 1000/    user)
Access: 2023-01-08 19:35:28.671123709 +0000
Modify: 2023-01-08 19:35:28.671123709 +0000
Change: 2023-01-08 19:35:28.671123709 +0000
 Birth: 2023-01-08 19:35:28.671123709 +0000

$ sudo debugfs -R 'stat <52695697>' /dev/nvme0n1p2
Inode: 52695697   Type: regular    Mode:  0600   Flags: 0x80000
Generation: 150578796    Version: 0x00000000:00000002
User:  1000   Group:  1000   Project:     0   Size: 0
File ACL: 0
Links: 1   Blockcount: 0
Fragment:  Address: 0    Number: 0    Size: 0
 ctime: 0x63bb1b00:a00223f4 -- Sun Jan  8 19:35:28 2023
 atime: 0x63bb1b00:a00223f4 -- Sun Jan  8 19:35:28 2023
 mtime: 0x63bb1b00:a00223f4 -- Sun Jan  8 19:35:28 2023
crtime: 0x63bb1b00:a00223f4 -- Sun Jan  8 19:35:28 2023
Size of extra inode fields: 32
Inode checksum: 0x4a2edd3c
```

Support for birth time in some of the file utils was added relatively recently I think, so if the file is older than when it was added, Birth time may be blank. Note that the birth time is not necessarily the time when the file was originally created, it may be the time when it was created on the current file system. However, modern rsync has the option:

--crtimes, -N            preserve create times (newness)

You can carry out your own tests to see which attributes will be preserved by the various utilities.

[1] [https://www.gnu.org/software/coreutils/manual/html_node/File-timestamps.html](https://www.gnu.org/software/coreutils/manual/html_node/File-timestamps.html)

---

### Post by anmac1789 on 2023-01-08
> **philhughes said:**
> From [1]:

Standard POSIX files have three timestamps:
- the access timestamp (atime) of the last read
- the modification timestamp (mtime) of the last write
- and the status change timestamp (ctime) of the last change to the file’s meta-information.

 Some file systems support a fourth time:
 - the birth timestamp (birthtime) of when the file was created; by definition, birthtime never changes.
 
Birth time is sometimes known as creation time (crtime).

For example:

```
$ stat afile
  File: afile
  Size: 0             Blocks: 0          IO Block: 4096   regular empty file
Device: 10302h/66306d    Inode: 52695697    Links: 1
Access: (0600/-rw-------)  Uid: ( 1000/    phil)   Gid: ( 1000/    user)
Access: 2023-01-08 19:35:28.671123709 +0000
Modify: 2023-01-08 19:35:28.671123709 +0000
Change: 2023-01-08 19:35:28.671123709 +0000
 Birth: 2023-01-08 19:35:28.671123709 +0000

$ sudo debugfs -R 'stat <52695697>' /dev/nvme0n1p2
Inode: 52695697   Type: regular    Mode:  0600   Flags: 0x80000
Generation: 150578796    Version: 0x00000000:00000002
User:  1000   Group:  1000   Project:     0   Size: 0
File ACL: 0
Links: 1   Blockcount: 0
Fragment:  Address: 0    Number: 0    Size: 0
 ctime: 0x63bb1b00:a00223f4 -- Sun Jan  8 19:35:28 2023
 atime: 0x63bb1b00:a00223f4 -- Sun Jan  8 19:35:28 2023
 mtime: 0x63bb1b00:a00223f4 -- Sun Jan  8 19:35:28 2023
crtime: 0x63bb1b00:a00223f4 -- Sun Jan  8 19:35:28 2023
Size of extra inode fields: 32
Inode checksum: 0x4a2edd3c
```

Support for birth time in some of the file utils was added relatively recently I think, so if the file is older than when it was added, Birth time may be blank. Note that the birth time is not necessarily the time when the file was originally created, it may be the time when it was created on the current file system. However, modern rsync has the option:

--crtimes, -N            preserve create times (newness)

You can carry out your own tests to see which attributes will be preserved by the various utilities.

[1] [https://www.gnu.org/software/coreutils/manual/html_node/File-timestamps.html](https://www.gnu.org/software/coreutils/manual/html_node/File-timestamps.html)

How do I use windows subsystem for linux and copy over folders and files from my android connected to my PC to windows 11 pro ? what is the command for that? or should I use windows built-in cmd?

---

### Post by philhughes on 2023-01-09
To answer your original question, in case it's not clear I don't think there is any way you can retain all 4 attributes. By the very fact of copying a file to the system, you are creating a new file, so ctime will change.

On a Linux system "cp -p" and "rsync -tU" will preserve access and modification times (but the access time of the original file will change). Even on Ubuntu 22.10, rsync does not support "-N". I don't know about other utilities preserving birth time.

I am not clear where you are mounting your phone, nor where you want the files on your phone to end up - Ubuntu, Windows or WSL or all 3? If you can see your mounted phone from Ubuntu or WSL, you may be able to use cp or rsync to preserve access and modification times. I have no experience with Windows commands. Also whether or not the various filesystems involved support these attributes is another matter.

---

### Post by anmac1789 on 2023-01-09
I only want the files and folders on windows. What about creating zip files or another archive format that preserves those 4 attributes when zipping then extracting those folders and files ?

---

### Post by TheFu on 2023-01-09
> **anmac1789 said:**
> I only want the files and folders on windows. What about creating zip files or another archive format that preserves those 4 attributes when zipping then extracting those folders and files ?

I'm confused.

You do understand that this is an Ubuntu Linux Forum and that since you posted under the "Official Flavours Support" forum, it is reasonable for everyone to assume ubuntu was to be used.  There's a different forum here for Windows and other OS questions.

Android is not Ubuntu, BTW.

---

### Post by anmac1789 on 2023-01-09
> **TheFu said:**
> I'm confused.

You do understand that this is an Ubuntu Linux Forum and that since you posted under the "Official Flavours Support" forum, it is reasonable for everyone to assume ubuntu was to be used.  There's a different forum here for Windows and other OS questions.

Android is not Ubuntu, BTW.
Ubuntu and android are both linux systems

---

### Post by QIII on 2023-01-09
But android is not Ubuntu.  Wndows is not Linux.

Are you attempting t use Ubuntu as a go-between from Android to Windows?

---

### Post by TheFu on 2023-01-09
> **anmac1789 said:**
> Ubuntu and android are both linux systems

Yes and no.  Android uses the Linux kernel, but userspace programs are completely different and throwing MS-Windows into the mix makes it nothing to do with Ubuntu.  You are trying to go from Android to MS-Windows, right?  

You've effectively taken your BMW car (android) to a Ford hobbyist group (Ubuntu) and expect that group to help with a Fiat (MS-Windows) and BMW.
For general stuff, we can help with Fords and closely related vehicles.  Sometimes people here can help with BMW and Fiat issues provided it isn't too specific.  That's why there are other sub-forums just for those need.  Other OSes are here: [https://ubuntuforums.org/forumdisplay.php?f=446](https://ubuntuforums.org/forumdisplay.php?f=446)

"Official Ubuntu Flavors" is pretty specific.  Not that we care too much. We enjoy problem solving.  The first post had Ubuntu in it, so nobody noticed.  
>  from android phone (galaxy s8) to ubuntu 22.04 to windows 10/11 pro ?
But the most recent posts are pretty clear that Ubuntu isn't related at all.
> How do I use windows subsystem for linux and copy over folders and files from my android connected to my PC to windows 11 pro ? 
Putting any Linux desktop in the middle is just adding 2 extra steps, which won't be good.  rsync.exe exists for Windows.  Use that with the Android device mounted and the options I provided many posts ago. See what happens.  You be the judge.  Either it works as you need or it doesn't.  I know of no better solution and I've been around a really long time.  rsync is one of the top 5 programs that I think everyone on any Unix-like OS needs to know.  I've been using rsync on Windows since the mid-1990s, but I never cared much about time stamps that I can't see.  The timestamps that show in GUIs will match, provided a root-like account is used - whatever you call that on your Windows system.

---

### Post by anmac1789 on 2023-01-09
> **QIII said:**
> But android is not Ubuntu.  Wndows is not Linux.

Are you attempting t use Ubuntu as a go-between from Android to Windows?

well kinda yes because some limitations that windows has, i switched over to ubuntu to make up for it then whwn i diacovered limitations on ubuntu i tried ro go back to windows and find methods to preserve dates for both windows and ubuntu then it got really complicated lol i got caught up in between making multiple backups of pictures and videos to try different methods of preserving timestamps lol

---

### Post by QIII on 2023-01-09
So, you want to use the userspace apps of one Linux-based OS to work with the userspace apps of another Linux-based OS to interact with the userspace apps of a non-Linux OS?  Each of the three having different file system functionality?

Does that not strike you as a swift path to a significant emotional event?

---

### Post by anmac1789 on 2023-01-09
> **QIII said:**
> So, you want to use the userspace apps of one Linux-based OS to work with the userspace apps of another Linux-based OS to interact with the userspace apps of a non-Linux OS?  Each of the three having different file system functionality?

Does that not strike you as a swift path to a significant emotional event?


LOL now that you say it like that you are kinda right. I've been trying to find a solution for months on end. I think I am near the concluding passage to throw in the towel and settle that there will be no swift os-interopability when it comes to timestamps preservation.

---

### Post by TheFu on 2023-01-09
> **anmac1789 said:**
> well kinda yes because some limitations that windows has, i switched over to ubuntu to make up for it then whwn i diacovered limitations on ubuntu i tried ro go back to windows and find methods to preserve dates for both windows and ubuntu then it got really complicated lol i got caught up in between making multiple backups of pictures and videos to try different methods of preserving timestamps lol

[https://askubuntu.com/questions/470134/how-do-i-find-the-creation-time-of-a-file](https://askubuntu.com/questions/470134/how-do-i-find-the-creation-time-of-a-file) provides a little program, but as stated above, the birth time is for the inode (when the file was created on the file system) and as soon as the file is copied, a new inode will be used with a new birth timestamp.  Looks like newer versions of 'stat' can read the birth timestamp directly, which would be of limited use for your needs.

For photos, use the EXIF data.  You can manipulate that using any photo library management tool.  I use exiftool.
Here's some example time information for a photo.
```
File Modification Date/Time     : 2017:12:04 18:04:47-05:00
File Access Date/Time           : 2020:06:12 08:50:58-04:00
File Inode Change Date/Time     : 2021:01:17 09:40:08-05:00
Modify Date                     : 2017:11:28 14:31:46
Date/Time Original              : 2017:11:28 14:31:46
Create Date                     : 2017:11:28 14:31:46
Date Stamp Mode                 : Off
GPS Date Stamp                  : 2017:11:28
GPS Date/Time                   : 2017:11:28 17:31:46Z
```
whereas the 'stat' for that file says:
```
Access: 2020-06-12 08:50:58.953326330 -0400
Modify: 2017-12-04 18:04:47.967114810 -0500
Change: 2021-01-17 09:40:08.377170574 -0500
 Birth: -
```  that's on a 20.04 system. The version of 'stat' isn't new enough to pull the inode file creation time.

I think Android internal storage uses ext4 too, so it wouldn't have that field either. You can't get data that doesn't exist.  My file was originally on a FAT32 microSD card.  I use the EXIF timestamp data to synchronize with GPS tracks and add GPS information later ... looks like I did that on in early December of the same year.

The EXIF "create date and time" seems correct to me for that photo. 

For video files, the container holding the files might have timestamps, but I doubt it. I don't recall seeing any standards for that and it seems that was never important for video container creation. I see just one timestamp in mkv containers and this isn't when the file was recorded. Looks like it was when it was transcoded and put into the last container only.

Interesting problem.  Sadly, I don't see any possible solution beyond what is stored inside EXIF.

---

### Post by anmac1789 on 2023-01-10
> **TheFu said:**
> [https://askubuntu.com/questions/470134/how-do-i-find-the-creation-time-of-a-file](https://askubuntu.com/questions/470134/how-do-i-find-the-creation-time-of-a-file) provides a little program, but as stated above, the birth time is for the inode (when the file was created on the file system) and as soon as the file is copied, a new inode will be used with a new birth timestamp.  Looks like newer versions of 'stat' can read the birth timestamp directly, which would be of limited use for your needs.

For photos, use the EXIF data.  You can manipulate that using any photo library management tool.  I use exiftool.
Here's some example time information for a photo.
```
File Modification Date/Time     : 2017:12:04 18:04:47-05:00
File Access Date/Time           : 2020:06:12 08:50:58-04:00
File Inode Change Date/Time     : 2021:01:17 09:40:08-05:00
Modify Date                     : 2017:11:28 14:31:46
Date/Time Original              : 2017:11:28 14:31:46
Create Date                     : 2017:11:28 14:31:46
Date Stamp Mode                 : Off
GPS Date Stamp                  : 2017:11:28
GPS Date/Time                   : 2017:11:28 17:31:46Z
```
whereas the 'stat' for that file says:
```
Access: 2020-06-12 08:50:58.953326330 -0400
Modify: 2017-12-04 18:04:47.967114810 -0500
Change: 2021-01-17 09:40:08.377170574 -0500
 Birth: -
```  that's on a 20.04 system. The version of 'stat' isn't new enough to pull the inode file creation time.

I think Android internal storage uses ext4 too, so it wouldn't have that field either. You can't get data that doesn't exist.  My file was originally on a FAT32 microSD card.  I use the EXIF timestamp data to synchronize with GPS tracks and add GPS information later ... looks like I did that on in early December of the same year.

The EXIF "create date and time" seems correct to me for that photo. 

For video files, the container holding the files might have timestamps, but I doubt it. I don't recall seeing any standards for that and it seems that was never important for video container creation. I see just one timestamp in mkv containers and this isn't when the file was recorded. Looks like it was when it was transcoded and put into the last container only.

Interesting problem.  Sadly, I don't see any possible solution beyond what is stored inside EXIF.

On my galaxy s8, I used to take pictures using the phone's camera and sometimes the date modified would be one second after the date digitized or date original timestamps. I dont know why this occurs. For most files the date modified and date digitized or date original matches. Before, I was using ubuntu 22.04 LTS and I could see the birth time but I was testing tranferring photos from my s8 --> ubuntu --> windows and I saw that the birth date is actually supposed to be the date created in windows. The only date time I couldn't or didn't know how to preserve was the date accessed.

---

### Post by TheFu on 2023-01-10
> **anmac1789 said:**
> On my galaxy s8, I used to take pictures using the phone's camera and sometimes the date modified would be one second after the date digitized or date original timestamps. I dont know why this occurs. For most files the date modified and date digitized or date original matches. Before, I was using ubuntu 22.04 LTS and I could see the birth time but I was testing tranferring photos from my s8 --> ubuntu --> windows and I saw that the birth date is actually supposed to be the date created in windows. The only date time I couldn't or didn't know how to preserve was the date accessed.

Did you look at the exif data?  That's where you'll need to look for the timestamp I think you want.  The other 3 are handed via 'sudo rsync -avz'

---

