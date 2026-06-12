---
title: "Share USB external drive between multiple users on same PC"
date: 2021-01-20
forum: General Help
---

### Post by Music_Guy on 2021-01-20
I am currently running Ubuntu Studio 20.10 on a Dell PC.  I have a USB external drive that I would like to share between multiple users on the same computer.  The drive is mounted at /media/myname/audio.  When I switch users, I can see the drive; however, I cannot open it.  I have the permissions set on the drive as: user=rwe, group=rwe, others=r.  I have turned sharing on using the drive properties, and have samba installed.  I have added the line in the smb.conf file "force user = myname".  (Of course, myname is my real username).  However, I still cannot open the drive.  What should I be doing?

---

### Post by CelticWarrior on 2021-01-20
Samba has nothing to do with sharing between users in the same computer; Samba is for network sharing exclusively.

---

### Post by Music_Guy on 2021-01-20
Do you have any suggestions as to how I can get sharing to work?

---

### Post by CelticWarrior on 2021-01-20
Not really because I don't know the specifics about that drive, partitions, file types, permission, etc.
What I usually do is to avoid the automatic mount under /media with a simple setting change in Disks:

Open Disks and select the partition
Click the double cogwheel and choose "Edit mount point"
Disable the auto option and enable to mount at the start
Keep all the other options but change - for aesthetics only - the "identify as" to "LABEL=....."
Save and enter the sudo password.

Do this from all the users and you should be fine.

---

### Post by #&amp;thj^% on 2021-01-20
> **Music_Guy said:**
> Do you have any suggestions as to how I can get sharing to work?

When you attach an external USB storage device to your system it automounts to a mount point at /media/your-user-name/XXX. The problem is Linux sets /media/your-user-name with special permissions ( acl ) that prevents anyone other than "your-user-name" from traversing the folder to get to XXX.

Props to Morbius1

If the disk is formatted as EXT4 you can use the "groups" to set the disk to a group both users belong too. Permissions on a Linux system are normally set to 755 for folders and 644 for files. But you can change that to 775 and 664, and set a group and then add both users to the group. Both will then be able to execute the disk, store and remove files. Basically all you would want.

If the disk is formatted as NTFS you need to provide user and group during the mounting of the disk. You have the dmask (directory), fmask (file) and umask (user) options for that. To set the owner, use the uid and gid. Similar to EXT you set the GID and add both users to the GID.

---

### Post by TheFu on 2021-01-20
[LIST]
[*]Put any users that need write access into the same unix group.
[*]The file system to be shared should be a native Linux, not ntfs or fat-whatever. **df -Th** will show the file system.
[*][https://ubuntuforums.org/showthread.php?t=2382965&highlight=working+chgrp](https://ubuntuforums.org/showthread.php?t=2382965&highlight=working+chgrp) explains how to do ti and the rest.
[/LIST]

IMHO, using ACLs will just lead to pain later. using normal unix permissions is how this stuff works the last 45+ yrs.

---

