---
title: "best auto backup ?"
date: 2014-10-06
forum: General Help
---

### Post by mastablasta on 2014-10-06
So i setup the server, seem like it will have to be redone anyway...Found a nice gui but again it has a preety serious bug (fo rme) anyway that on the side, i am in search for automated backup system to transfer the files from dekstops onto this server.

many of them are not really explaining what protocols they use and the important things. so i am hoping someone using one of these can give me some advice. here are my requirements:

1. it can make snapshots
2. it has a windows client as well as (K)Ubuntu client
3. it can regulate bandwidth (so i can setup higher bandwidth usage at night, lower during day)
4. it performs automatic (pre-scheduled backups)
5. it can safely resume the backup in case conection gets dropped
6. it is actively maintained
7. support for large files (think HD movies DVD size or more)
8. android support (-optional-)

if there is anything like that out there i would also like to know what protocols it uses to connect with server and transfer files. sFTP, torrent... how does it check for file integrity etc... even ZFS (btrfs) is not going to help if files get on disk with errors...

so far the closest thing to this came luckybackup although i do not know what happens if connection gets dropped while files are being transfered.

oh and i only need files that move one way, no syncing.

---

### Post by ian-weisser on 2014-10-06
Are you looking for a simple solution?
Or a set of customizations? (How to script backups when connecting to your LAN vs the wider internet)
Or strategies? (Like sync media files to that server instead of backing them up with your data)

---

### Post by mastablasta on 2014-10-07
simple solution. no syncing I mean at least not in the classical two way term (we will sync via Owncloud the few files that are actually to be synced). we need something to reliably and periodically push the data to server.

there are two LAN's. one has the server where the data will be. we were thinking of using OpenVPN to connect us all into one internal network. 

but the idea is this, a remote user takes some photos on a weekend trip. they download them to their PC. then on Sunday night this data get's copied to server. on Monday the user is browsing the files and accidentally deletes or applies filters and saves. as soon as he notices this he calls the admin and there is a snapshot from previous image. they I can restore it for them. most of the data will be static. there will be some dynamic data (e.g. my webserver that is on a host could use some backup). 

we have it like this:

[TABLE="class: grid, width: 500"]
[TR]
[TD]**Network 1**[/TD]
[TD]**Network 2**[/TD]
[/TR]
[TR]
[TD]Windows XP[/TD]
[TD]Windows XP[/TD]
[/TR]
[TR]
[TD]Kubuntu&#65279;&#65279;[/TD]
[TD]Kubuntu[/TD]
[/TR]
[TR]
[TD]Kubutnu /Windows 7 (dualboot)[/TD]
[TD]Kubuntu[/TD]
[/TR]
[TR]
[TD]Chrunchbang[/TD]
[TD]Raspbian[/TD]
[/TR]
[TR]
[TD]Android[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]OpenELEC 
(does not get backed up, has it's own hard disk)[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]Server (for backups)[/TD]
[TD][/TD]
[/TR]
[/TABLE]

---

### Post by oldfred on 2014-10-07
I have been backing up with rsync to another drive and using DVDs for my most important data.

After review this thread I may convert to rdiff.

 Discussion of issues on rsycn bash file &  rdiff-backup  - TheFu
[http://ubuntuforums.org/showthread.php?t=2224428](http://ubuntuforums.org/showthread.php?t=2224428)
Sample rdiff file by TheFu
[http://ubuntuforums.org/showthread.php?t=2200427&p=12911880#post12911880](http://ubuntuforums.org/showthread.php?t=2200427&p=12911880#post12911880)
[http://blog.jdpfu.com/2013/10/20/rdiff-backup-real-use](http://blog.jdpfu.com/2013/10/20/rdiff-backup-real-use)

---

### Post by aaronsantiago89 on 2014-10-07
Might be your ISP or your router.

Was there any strange behavior happening that has to do with your Internet access.

---

### Post by mastablasta on 2014-10-08
rdiff has a limit of max 2GB files as well as some other limits. only I am not sure if this goes only for windows server, windows client or what. in genral most of backup solution I went through have very vague descriptions.

as i know rsync is doing only syncing. so if you delete something on one end it is then removed on another. if you accidentally delete something on one side... 

> The earliest releases of rdiff-backup are more than seven years old. Since then there have been more than 70 releases fixing bugs and adding features. The basic functionality on unix platforms has been tested by many people over this time and can be considered stable.
Many users seem to use rdiff-backup on MS Windows but this configuration is less well tested. Also, features such as Mac OS X resource forks, Extended Attributes, and Access Control Lists were only released about five years ago. There are no known bugs in these newer features, but they are not as thoroughly tested as the basic functionality. Native Windows support was first released six months ago.
Using rdiff-backup to backup files to a server mounted via smbfs or CIFS has been a troublesome configuration for some users. Mounting via smbfs tends to be more reliable than CIFS, although it is deprecated on Linux and does not support files greater than 2 GB. See the FAQ for more on this setup.


also the whole documentation is a bit vague on what is supported on windows and what is not. does pushing from windows to Linux work? how is the connection made with the Linux server?

---

### Post by mastablasta on 2014-10-13
been strengthening security over the weekend and trying to get the openvpn to work. I think we need UbuntuVPN - OpenVPN is way too complicated for average user. requires a massive amount of reading and possibly a degree in networking.

anyway... 

I will soon be testing automatic updates. 

so how are these pushed to server? I tried lucky backup and while selecting the source folder in windows is straight forward, selecting a destination folder on server is not so much. what puzzles me is the type of transfer one should use. is it sFTP and if so would you need some soft of FTP client along with the updates client? or is this whole thing working over some other transfer type? what are you supposed to set as target? [ftp://localhost](ftp://localhost)?

---

