---
title: "Samba shares: Windows Users Can't Create/Delete Folders"
date: 2007-06-25
forum: General Help
---

### Post by crazycarlt on 2007-06-25
Hello. I've set up an Ubuntu box as a home server on our network. I've created two shares and I'm using SWAT (a flaky tool in my opinion) to manage them.

I can't figure out why, but users on the network cannot create or delete folders in the shared directories. They're logged in and they can view/copy files, but when it comes to folders nothing can be done.

My smb.conf:
```
# Samba config file created using SWAT
# from 192.168.1.25 (192.168.1.25)
# Date: 2007/06/15 18:49:02

[global]
	workgroup = FAMILY
	server string = %h server (Samba, Ubuntu)
	obey pam restrictions = Yes
	passdb backend = tdbsam
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	panic action = /usr/share/samba/panic-action %d
	invalid users = root

[share1]
	comment = Shared files
	path = /share
	valid users = thuringer
	read only = No

[usbdrive]
	comment = External USB Drive
	path = /mnt/usbdrive
	valid users = thuringer
	read only = No

```

---

### Post by DagMan on 2007-06-25
I can't tell you by looking at it but when I have trouble like that I go to this thread:
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)
Maybe that will help you too.

---

### Post by crazycarlt on 2007-06-25
On a whim I went down to my root directory and...
```

sudo chmod -R 777 share

```

Voila. It was a permissions issue.

---

