---
title: "Video Files Will Not Play Over Samba"
date: 2021-12-13
forum: General Help
---

### Post by don43 on 2021-12-13
I put a new WD Red drive in my Ubuntu PC. Set up a shared folder and copied video files to the drive. Also have Emby and set up the folder there as well. I tried to access the videos from a Windows PC, the files are seen but won't play. Using a Roku, Emby sees the videos too but also they won't play. Tried an Android box to access the shared video and they won't play either. I can access photos and text files on the new drive on the network, but videos will not play.

Ubuntu 20.4, with Cinnamon Desktop.

---

### Post by TheFu on 2021-12-13
If the files are directly connected to the same Linux machine that has the media center software (I use Jellyfin), then there is ZERO need for CIFS/samba for playback.  Just use either the Emby client or any DLNA renderer/controller to play the media.

CIFS/Samba are known to have problems with streaming media. Generally, it is recommended to use NFS.  Nobody know why, but NFS just works better for Linux-based media file access over a network.

Of course, if you have to use Windows as storage for the media files (I'm so sorry), there is little choice but to get CIFS working.  In that case, you'll want to setup a CIFS mount either using /etc/fstab or autofs methods.  Doing it at the OS level, not in the media center application, will use kernel drivers instead of slower, application, connectivity.

I use autofs, so my connection settings look like this:
```
/Data/windows-pc  -fstype=cifs,iocharset=utf8,rw,vers=2.1,uid=1000,gid=1000,file_mode=0664,dir_mode=0775,credentials=/etc/samba/windows.credentials  ://172.22.22.8/Data
```

Translating that into /etc/fstab format ... I didn't verify, but this should be it:
```
//172.22.22.8/Data  /Data/windows-pc    cifs    iocharset=utf8,rw,vers=2.1,uid=1000,gid=1000,file_mode=0664,dir_mode=0775,credentials=/etc/samba/windows.credentials   0    0
```

All on 1 line.  There are 6 fields, space separated.  The "options" part cannot have any spaces.  Login credentials to the Windows share are in the credentials file.  The permissions in that mount line provide my userid/groupid (1000/1000) with full control, but Jellyfin (other) would have read-only access.  Only at mount time, using mount options, can permissions be set with CIFS and non-native Linux file systems.

---

### Post by don43 on 2021-12-13
I tried using Emby too and the videos still will not play.

---

### Post by SeijiSensei on 2021-12-13
I use the bog-simple minidlna on the server. Install the app from the repositories, edit the minidlna.conf file to point the app at the location where the files are stored, and start it up. My Roku's default video player app can see and play most of the files stored there, as can my Android phone, and, the last I looked, VLC and Windows Media Player.

You didn't tell us about the formats of the difficult files. Many players don't support the wide range of available formats, particularly open formats. I had to submit a support request to Roku to get them to fix a problem with Matroska files in their player.  Most everything will play files in the .mp4 container with AAC or mp3 audio.

When I've tried playing files using Samba, the video player would not stream the file but download a local copy first. You might be seeing the downloading step and thinking the app isn't working.

---

### Post by don43 on 2021-12-13
> **SeijiSensei said:**
> I use the bog-simple minidlna on the server. Install the app from the repositories, edit the minidlna.conf file to point the app at the location where the files are stored, and start it up. My Roku's default video player app can see and play most of the files stored there, as can my Android phone, and, the last I looked, VLC and Windows Media Player.

You didn't tell us about the formats of the difficult files. Many players don't support the wide range of available formats, particularly open formats. I had to submit a support request to Roku to get them to fix a problem with Matroska files in their player.  Most everything will play files in the .mp4 container with AAC or mp3 audio.

When I've tried playing files using Samba, the video player would not stream the file but download a local copy first. You might be seeing the downloading step and thinking the app isn't working.

I tried MP4, MPG, FLV. None played either over Samba or Emby.

---

### Post by TheFu on 2021-12-13
So ... some questions:
[LIST=1]
[*]The new drive is connected to the Ubuntu system?  
[*]Emby runs on the same Ubuntu system?
[*]Did you format the drive as EXT4 or ZFS or some other native Linux file system? 
[*]I.e. didn't leave it as NTFS?
[*]When you mount the EXT4 drive, where did you mount it, exactly?  
[*]How do you mount it? 
[/LIST]
 The **only** answer should be via the /etc/fstab

I'm 90% thinking there is a file permission problem. That's easily handled if the file system **IS NOT** NTFS.  If it is NTFS, the best answer is to wipe all the files from it, format it as ext4, setup the permissions correctly so your userid and emby have access to the files, While you are there, force the permissions to remain correct, then mount it in a place that emby can see.  

Don't mount storage under any user's HOME directory.

For example, my storage server runs Jellyfin (a fork of emby) and Plex (not much longer) and is an NFS server to the house.  I have 8 media drives. They are mounted to 
[LIST]
[*]/d/D1
[*]/d/D2
[*]/d/D3
[*]/TV
[/LIST]
The other drives are backups of those.  Jellyfin and Plex have read-only access to those places and my userid is the owner for management purposes.  /TV/Recordings is where OTA TV gets recorded. While that is happening, the jellyfin user and group are the owner/group on the file.  Every hour, I have a script run by root via cron that 

```
#!/bin/bash
/bin/chown -R thefu    "/TV/Recordings"
/bin/chgrp -R jellyfin "/TV/Recordings"
/bin/chmod -R g+w      "/TV/Recordings"
/usr/bin/find "/TV/Recordings" -type d -exec /bin/chmod g+s {} \;

```
Those are the exact commands. This results in permissions that look like this:
```
drwxrwsr-x  2 thefu jellyfin  4096 Dec 13 07:00 SEAL Team/
```
on the directories.  The files inside are similar, just without the eXecute permissions. Because my userid is the owner of everything, additional processing, like **comskip** and **apertium** can be performed to mark commercial locations and translate into a few other languages.

My userid is in the jellyfin group, BTW.  It is also in the plex group. There are probably more elegant methods. I'd prefer if jellyfin's server daemon started up with a umask of 002. That would have made the script above a little easier (actually, just the chown), but whatever ... 

IF the file system is NTFS, none of those commands work. NTFS doesn't support chown, chgrp, chmod. Hence a reason for NOT ever using NTFS nor using CIFS. It is a permissions thing.

---

### Post by don43 on 2021-12-13
> **TheFu said:**
> So ... some questions:
[LIST=1]
[*]The new drive is connected to the Ubuntu system?
[*]Emby runs on the same Ubuntu system?
[*]Did you format the drive as EXT4 or ZFS or some other native Linux file system?
[*]I.e. didn't leave it as NTFS?
[*]When you mount the EXT4 drive, where did you mount it, exactly?
[*]How do you mount it?
[/LIST]
 The **only** answer should be via the /etc/fstab

I'm 90% thinking there is a file permission problem. That's easily handled if the file system **IS NOT** NTFS.  If it is NTFS, the best answer is to wipe all the files from it, format it as ext4, setup the permissions correctly so your userid and emby have access to the files, While you are there, force the permissions to remain correct, then mount it in a place that emby can see.  

Don't mount storage under any user's HOME directory.

For example, my storage server runs Jellyfin (a fork of emby) and Plex (not much longer) and is an NFS server to the house.  I have 8 media drives. They are mounted to 
[LIST]
[*]/d/D1
[*]/d/D2
[*]/d/D3
[*]/TV
[/LIST]
The other drives are backups of those.  Jellyfin and Plex have read-only access to those places and my userid is the owner for management purposes.  /TV/Recordings is where OTA TV gets recorded. While that is happening, the jellyfin user and group are the owner/group on the file.  Every hour, I have a script run by root via cron that 

```
#!/bin/bash
/bin/chown -R thefu    "/TV/Recordings"
/bin/chgrp -R jellyfin "/TV/Recordings"
/bin/chmod -R g+w      "/TV/Recordings"
/usr/bin/find "/TV/Recordings" -type d -exec /bin/chmod g+s {} \;

```
Those are the exact commands. This results in permissions that look like this:
```
drwxrwsr-x  2 thefu jellyfin  4096 Dec 13 07:00 SEAL Team/
```
on the directories.  The files inside are similar, just without the eXecute permissions. Because my userid is the owner of everything, additional processing, like **comskip** and **apertium** can be performed to mark commercial locations and translate into a few other languages.

My userid is in the jellyfin group, BTW.  It is also in the plex group. There are probably more elegant methods. I'd prefer if jellyfin's server daemon started up with a umask of 002. That would have made the script above a little easier (actually, just the chown), but whatever ... 

IF the file system is NTFS, none of those commands work. NTFS doesn't support chown, chgrp, chmod. Hence a reason for NOT ever using NTFS nor using CIFS. It is a permissions thing.

The drive is connected to the Ubuntu system, Emby is installed on the same system. Drive is EXT4.

It's mounted at /mnt

Mounted it using Disks.

I have another drive in the system, mounted the same way and was able to add shares originally when I put the drive in there.  The videos in the older shares play fine. But trying to add any new share, the videos will not play.

---

### Post by TheFu on 2021-12-13
> **don43 said:**
> The drive is connected to the Ubuntu system, Emby is installed on the same system. Drive is EXT4.

It's mounted at /mnt

Mounted it using Disks.

I have another drive in the system, mounted the same way and was able to add shares originally when I put the drive in there.  The videos in the older shares play fine. But trying to add any new share, the videos will not play.

Ok, thanks. That answers the key questions.  
Two things remain on the "systems" side, as opposed to Emby settings.

"Disks" - I've never used that.  If it doesn't setup the mounts in the /etc/fstab, then you need to fix that.  **USE THE FSTAB.** /mnt isn't the best place, but it can work. Standards say /mnt is for temporary use, not permanent mounts, but in reality, it doesn't matter.  If you have 2 media partitions (**never** mount disks) mounted, then they would be in different subdirectories  under /mnt/ ... perhaps /mnt/d1 and /mnt/d2?  The names don't matter.

Next, check the permissions. I've shown them above. Use **ls -l** from a terminal to show the permissions. Please. Would be best to show the permissions for the working storage and the non-working storage.  Something like **ls -l /mnt/** should do it.  Please post the output wrapped in 'code tags' here.  This is how, if you need help: [Https://ubuntuforums.org/misc.php?do=bbcode#code](Https://ubuntuforums.org/misc.php?do=bbcode#code)  I've used code-tags in my post above. We do this for anything shown in a terminal or commands + the output.

I'm 99% certain this is a permissions issue, if it is a "systems" problem.

---

### Post by TheFu on 2021-12-13
BTW, I have 2 goals.
1) get emby working with the storage.
2) get samba working for Windows.  In the meantime, you can use WinSCP on Windows to manage the files using sftp/scp if ssh-server is installed on the Ubuntu box.

---

