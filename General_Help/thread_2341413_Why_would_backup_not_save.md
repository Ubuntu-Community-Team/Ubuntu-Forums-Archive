---
title: "Why would backup not save?"
date: 2016-10-27
forum: General Help
---

### Post by alvinmoneypit on 2016-10-27
I've been having trouble with 'backup' program running in Ubuntu 12.04.  I backup to an expansion drive attached via usb 3.0 cable.  For the last month or so, it has been doing it's weekly backup and it's been giving the message, "backing up for the first time, this may take awhile".  This evening I decided to check my backup folder and it is completely empty.  The last time I checked it about 3 months ago, it had numerous backups in it.  I wonder what could have happened to all my backups and why no new ones are being created?  I took a large folder I have on my resident hard drive and was able to move it over to the expansion drive with no problems.  Anyone have any ideas what is going on?

---

### Post by mastablasta on 2016-10-28
what backup program?

---

### Post by alvinmoneypit on 2016-10-28
The backup program bundled with Ubuntu 12.04 release.  As in, System settings > backup.

---

### Post by jerome1232 on 2016-10-28
It's called deja-dup for future reference.  I would try running it from a command line to see what, if any, output it spits out to terminal.

To open a terminal press ctrl+alt+t

to start a backup
```
deja-dup --backup
```

to open that window you normally see that lets you set preferences
```
deja-dup-preferences
```

To copy output from a terminal you need to either use ctrl+shift+c or right click and select copy.

---

### Post by alvinmoneypit on 2016-10-28
jerome 1232,

the first command brought up deja-dup starting GUI.

The second command didn't do anything -no output whatsoever.  I did not enter the password in the GUI.

---

### Post by alvinmoneypit on 2016-10-28
I removed and reinstalled deja dup. Again, it performed normally, but when I checked the location, there again was nothing in it.  I wonder how backup recalled my storage preference were set up since I removed the program, rebooted and program was gone, reinstalled and rebooted again, yet the program retained my settings??  I removed it again and installed luckybackup - using it as I type.  I'll report when it completes.

---

### Post by alvinmoneypit on 2016-10-28
I installed and set up lucky backup.  I tried to backup my normal folders.  The program seemed to be working, just as deja dup did, but it did not store the files on my destination.  I rechecked my settings by 'modify' selected 'tasks' and viewed the 'advanced' settings within.  In the advanced settings, one tab is 'command options' within I found a setting, 'destination is FAT/NFTS' not checked.  I checked that check box and tried to backup again.  This time it worked.  I'll keep this as I'm not proficient at terminal commands and luckybackup has them in the GUI.  Thanks for replies.  Somewhere along the way an update must have required the aforementioned distinction as previously deja dup worked fine.  I'll mark as 'solved'.

---

### Post by bearlake on 2016-10-28
Been using lucky backup for years now and had little to no troubles.

---

