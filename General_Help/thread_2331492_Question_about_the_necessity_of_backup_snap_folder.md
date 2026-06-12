---
title: "Question about the necessity of backup /snap folder"
date: 2016-07-22
forum: General Help
---

### Post by fprietog on 2016-07-22
Hello,

Every day I make a backup (rsync) of all / folders except:


[LIST]
[*]cdrom
[*]dev
[*]media
[*]mnt
[*]proc
[*]run
[*]sys
[*]tmp
[/LIST]

I'ts because I think these excluded folders are repopulated with every boot or are just mount points.

So my question is; do I need to backup the new /snap folder or it's just another mount point "in disguise"?.

Thanks and best regards.

---

### Post by deepakdeshp on 2016-07-22
Hello
Here is some information on backups.
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
For taking complete system dump you can use clonezilla.

Daily backups can be limited only to the files that get chnged. Usually backing up /home should backup all changed files. You can take a full backup of hone once every week. Rest of the days you can take inctemental backup. Similarly Clonezilla backup can be taken once a week.

[https://www.google.co.in/url?sa=t&source=web&rct=j&url=http://cd-rw.org/t/how-to-complete-clonezilla-backup-and-recovery-of-your-linx-lamina-windows-x86-tablet/126&ved=0ahUKEwiLkubk3IfOAhXFMY8KHRl-CXIQFggbMAA&usg=AFQjCNHZTRQjGe8a-9YWh9fB0tBtL8FxaQ&sig2=dOfRNwmrq1lAj0J1yRjWAg](https://www.google.co.in/url?sa=t&source=web&rct=j&url=http://cd-rw.org/t/how-to-complete-clonezilla-backup-and-recovery-of-your-linx-lamina-windows-x86-tablet/126&ved=0ahUKEwiLkubk3IfOAhXFMY8KHRl-CXIQFggbMAA&usg=AFQjCNHZTRQjGe8a-9YWh9fB0tBtL8FxaQ&sig2=dOfRNwmrq1lAj0J1yRjWAg)

---

### Post by fprietog on 2016-07-22
Hi deepakdeshp,


Thanks for the info. I'm currently using incremental rsync for the backups because I use a rsync backup server as target, so I just synchronize folder contents changes.



Thanks and best regards.

---

### Post by mc4man on 2016-07-22
> **fprietog said:**
> 
I'ts because I think these excluded folders are repopulated with every boot or are just mount points.

So my question is; do I need to backup the new /snap folder or it's just another mount point "in disguise"?.

Thanks and best regards.
The /snap folder only exists once you boot up, is read only & is just reflective of any installed snaps being mounted (loop devices) at boot. So don't see any reason to backup

---

### Post by fprietog on 2016-07-22
Thanks for the answer mc4man. I was not sure of how it works.

---

### Post by mc4man on 2016-07-22
To be a bit more accurate - 
/snap will exist & /snap/<some app folder>  may exist but the folders are only populated at boot for snaps that are installed once they are mounted
If you remove a snap it's folder will be left behind in /snap (empty
Being as snaps mount read only you could never modify, add or restore to them anyway
screen shows one in Disks, so down the road if one had let's say 20 snaps you'd have 20 loop devices, ect.

---

### Post by fprietog on 2016-07-22
Thanks mc4man. 

I've just done a little test; I've deleted /snap folder (after unmounting all snaps) and reboot just created it again with snaps re-mounted.

So no need to be backed at all.

Thanks and best regards.

---

### Post by grahammechanical on 2016-07-22
There is a snap folder in /home. That snap folder has folders for each snap application that is installed and inside those folders would be any user created files from the application including application state at the time of closing. Some are hidden files.

For example, the Notes snap has /home/snap/notes/1/.config/Awaresomeness/Notes.ini & Settings.ini & Trash.ini. It is the Notes.ini that contains the notes created in the Notes snap application. 

Regards.

---

### Post by mc4man on 2016-07-22
What is a little curious is that if a snap is removed then it's folder in the $HOME dir. is also removed. Not sure if it makes sense or not, opposite of what currently happens when a package is removed.

---

### Post by fprietog on 2016-07-22
> **mc4man said:**
> What is a little curious is that if a snap is removed then it's folder in the $HOME dir. is also removed. Not sure if it makes sense or not, opposite of what currently happens when a package is removed.
¿Curious?... Better say dangerous. :sad:

---

