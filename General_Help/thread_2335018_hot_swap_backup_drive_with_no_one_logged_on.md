---
title: "hot swap backup drive with no one logged on"
date: 2016-08-24
forum: General Help
---

### Post by naughtmcnoone on 2016-08-24
I am setting up a system using xubuntu 16.04.01 LTS.

It has a Startech HSB100SATBK 5.25" Trayless mobile rack for 3.5" HDD.

It works fine when someone is logged in.  The auto mount feature shows an icon on the users desktop for the drive.
I can remove the drive, and the icon disappears.  When I plug in another drive, it comes back, and the drive automatically mounts.

What I am trying to do, is have the drive mount automatically, to a specific location, without any user logged on.
That way, the drive can be swapped out without any need for a user to log onto the system, and the backup will run as a crontab.

Has anyone been able to do this?

Cheers!

Naught McNoone

---

### Post by TheFu on 2016-08-24
Edit the /etc/fstab.
There is a how-to - good will find it.

---

### Post by naughtmcnoone on 2016-08-25
@TheFu

I am trying to get it to work with autofs.

I already looked at an entry into fstab.
Adding an entry to the fstab works, sort of.  
It will unmount after the drive is removed, but it is not a clean unmount.  
It will remount it's self, as well, but again, not cleanly.

I am must be misinterpreting the autofs manpage, or missing something that should be obvious.

Cheers!

Naught

---

### Post by TheFu on 2016-08-25
I've never had great luck with NTFS and autofs.  The issue is that autofs wants/needs to have a userid for permissions and NTFS permissions aren't easily maintained on a Unix system.  If you can, switch to a Unix file system and all this will *just work*.

I'm a big user of autofs for about 20 yrs. Love it for USB devices, I just don't use it for NTFS. Sorry.

If you'd like more help, perhaps from others, posting the auto.master and auto.WHATEVER-YOU-CALLED-IT file would help a bunch. Please use *code tags*.  We need to details to help, right?

---

### Post by naughtmcnoone on 2016-08-26
@TheFu

The intent is to have a backup of the whole system, that can be rotated on a regular basis.
If the system becomes corrupt, or (possible, but not probable,) infected or hacked then I can go back and restore it.

The backup program works fine, as long a the drive is mounted properly.

All drives, including the back up drives are ext4.
The hot swap drive is not a shared network drives. 
It is only available in local mode.

Each of the backup drives is identical (consecutive ser#'s, surprise!) 
I have modified the drives so that each has the exact same UUID, so the system will see them as the same drive, regardless of which one is plugged in.

Only the administrator has access to the local system.  Everyone else access it through a samba share, media server, etc.

Here is the entry in /etc/auto.master:[INDENT=3]***/media/hotswap /etc/auto.mount***[/INDENT]
 
Here is the entry in /etc/auto.mount:[INDENT=3]***/media/hotswap -fstype=auto,sync,rw :UUID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx***[/INDENT]
 
When I run autofs stop / start, reload, or status I do not get any error message.

Here is the output for autofs status:[INDENT=3]***root@serverxxx# /etc/init.d/autofs status***[/INDENT]
[INDENT=3]***&#9679; autofs.service - LSB: Automounts filesystems on demand***[/INDENT]
[INDENT=3]***   Loaded: loaded (/etc/init.d/autofs; bad; vendor preset: enabled)***[/INDENT]
[INDENT=3]***   Active: active (running) since Thu 2016-08-25 11:38:17 EDT; 23h ago***[/INDENT]
[INDENT=3]***     Docs: man:systemd-sysv-generator(8)***[/INDENT]
[INDENT=3]***  Process: 3252 ExecStart=/etc/init.d/autofs start (code=exited, status=0/SUCCESS)***[/INDENT]
[INDENT=3]***   CGroup: /system.slice/autofs.service***[/INDENT]
[INDENT=3]***           &#9492;&#9472;3294 /usr/sbin/automount --pid-file /var/run/autofs.pid***[/INDENT]
[INDENT=3]***Aug 25 11:38:16 serverxxx systemd[1]: Starting LSB: Automounts filesystems on demand...***[/INDENT]
[INDENT=3]***Aug 25 11:38:16 serverxxx autofs[3252]:  * Starting automount...***[/INDENT]
[INDENT=3]***Aug 25 11:38:17 serverxxx autofs[3252]:    ...done.***[/INDENT]
[INDENT=3]***Aug 25 11:38:17 serverxxx systemd[1]: Started LSB: Automounts filesystems on demand.***[/INDENT]


I am looking for a way to have automount to work without anyone logged on.

Ideas or suggestions?
One thought is to leave the administrator logged in, all the time.  That however, is not a good idea, as prying hands will succumb to curiosity, and cause grief to the system.

Another idea is to have crontab dismount the drive, run fsck, then remount the drive, just before the scheduled backup.  That would help is the swap did not go cleanly.

Cheers!

Naught

---

### Post by TheFu on 2016-08-26
I thought UUIDs have to be unique within a single system.  Try using some other id to mount the backup disk, not the UUID.  Or did I read that all wrong?  The UUID doesn't have a leading ':' character in autofs either. The leading : is for devices, not labels or UUIDs.

Solve 1 thing at a time. Get autofs working. Then work on samba ... but samba doesn't have anything to do with backups, right? Ah. I see you aren't.

I don't do image-based backups - to get a good image, the entire system would need to be quiesced.  Are you using LVM snapshots to get that or going into single-user-mode?

Ok .. onto the autofs config issues.  I'll use different examples that you should map for your situation.
Inside auto.master:
```
/misc   /etc/auto.misc
```
The line in the file above would make ... backups go to lets see .... "/media/hotswap/media/hotswap" - is that what you intend?
BTW, using /media could be a really bad idea.  /media is managed by the OS. Best to use a different top level directory.  I like /Data or /D, myself.

Inside /etc/auto.misc ...
```
tv  -nodev,nosuid,timeout=2,fstype=ext4     :/dev/disk/by-label/TV-FILES
```
This will place the files into /misc/tv/ .... See how the top directory in auto.misc is used, then "tv" is added?  That's a key thing to using autofs.  There is a way to specify the exact directory using the **/-** option in auto.master. Regardless, don't use /media. That is asking for problems.

Try that first. Then we can look at other issues. I suspect this will solve the issues, however, I don't have **any** 16.04 systems here. Too new for our use.  14.04 is the latest server and we still have a 12.04 left.

---

### Post by naughtmcnoone on 2016-09-09
The issue is solved.

Thank you for your help and suggestions.

I mulled over the suggestions, and decided to start from scratch.

I reset all the autofs and related config files back to original default on install.

I added this entry into the fstab:

[INDENT]*# Mount hotswap drive for all users*[/INDENT]
[INDENT]*# /dev/sdc1*[/INDENT]
[INDENT]*UUID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx /hotswap ext4 sync,auto,exec,suid,rw,user	0	2*[/INDENT]

The result is the drive will mount cleanly on boot, and can be removed and replaced by it's twin (using the same UUID,) with no other action by the user.
The crontab script that does the backup will check to make sure that the drive is present and mounted properly.

As long as the drives are not switched during the backup (03:00 AM local time,) everything works.
As no one is (usually) awake at that time, then there is no issue.

 Cheers!

Naught

---

### Post by TheFu on 2016-09-09
There can be a security issue in having the backups inside the machine AND mounted.  Backups have many uses, but more and more protection against "bad actors" is becoming the primary reason.  If your back script mounts and umounts the storage only as needed, that would be a helpful step.

Are you doing mirrored backups or using some efficient tool that does versioned backups too?  Versioned backups are very helpful when trying to determine what happened, when, after the fact. When you are hacked (eventually everyone is), it is nice to have those versioned backups on a different system to see when the bad stuff started.  60 days of versioned backups doesn't really take all that much storage these days.

---

