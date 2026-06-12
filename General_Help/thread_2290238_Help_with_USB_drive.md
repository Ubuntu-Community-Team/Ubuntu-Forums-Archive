---
title: "Help with USB drive"
date: 2015-08-10
forum: General Help
---

### Post by daniel294 on 2015-08-10
Hi all,
 
I want to back up a windows image to an external USB drive connected to my Ubuntu server.
I formatted the USB drive with ext4 and mounted it. I also added it to the samba and even (temporary) gave it 777 permissions.
I can r/w from Windows do this drive (mapped as a network share) with no problems at all.
The problem is, that when I use wbAdmin on windows to create an image on the USB drive, I get this error:
 
ERROR - The user does not have write permission to the remote shared folder.
 
Here are my settings on Ubuntu:
Blkid shows:
/dev/sdd: UUID="a010a1a5-3b47-4757-9abf-3afaddf96008" TYPE="ext4"
 
At the fstab I wrote:
UUID=a010a1a5-3b47-4757-9abf-3afaddf96008  /media/USB_DRIVE  bind defaults,bind 0 0
 
And in smb.conf (same as I did with all other shares):
[USB]
comment = Backup Drive
browseable = yes
path = /media/USB_DRIVE/
printable = no
guest ok = yes
read only = no
create mask = 7777
 
On my Ubuntu I have user1 and on windows user2
The command line for the wbAdmin looks like:
Wbadmin  start backup  -backupTarget:\\serv\BACKUP  -include:C: -user:use1 -password:xxx -quiet
This runs under user2
 
 
What am I missing? How do I set the correct permissions?

---

### Post by daniel294 on 2015-08-10
[UPDATE]
when i create an image with the GUI that Windows provides,everything works fine with the exact same parameters...
i guess the problem is with Wbadmin command line.

---

### Post by daniel294 on 2015-08-12
Found the problem. 
Wbadmin needs a full samba name (the whole path) and not just the path to the mount point.

---

