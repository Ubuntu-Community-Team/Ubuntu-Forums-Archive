---
title: "Access samba shares without password from XP (Hardy)"
date: 2008-06-05
forum: General Help
---

### Post by ragendem on 2008-06-05
I have tried a few ways of doing this and nothing seems to work. I have tried sharing from nautalis, swat and samba-config. I've never had this problem before and nothing seems to work. A search on these forums came up with a lot of ways to do it with a password which wont work for me.

I need a way for windows machines to have read/write access to a samba share running on ubuntu 8.04. I'm having no problem with read access, my issue is write access.

Is there any way to do this?

My folder is on an ext3 drive with 777 permissions

Here my smb.conf

```
# Samba config file created using SWAT
# from 127.0.0.1 (127.0.0.1)
# Date: 2008/06/05 01:18:53

[global]
	workgroup = HOMENET
	server string = %h - samba %v
	security = SHARE
	encrypt passwords = No
	map to guest = Bad User
	null passwords = Yes
	obey pam restrictions = Yes
	passdb backend = tdbsam
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	invalid users = root
	guest ok = Yes

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[Media]
	path = /media/data
	read only = No
	browseable = Yes
```

Here is my testparm output:
```
# Samba config file created using SWAT
# from 127.0.0.1 (127.0.0.1)
# Date: 2008/06/05 01:18:53

[global]
	workgroup = HOMENET
	server string = %h - samba %v
	security = SHARE
	encrypt passwords = No
	map to guest = Bad User
	null passwords = Yes
	obey pam restrictions = Yes
	passdb backend = tdbsam
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	invalid users = root
	guest ok = Yes

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[Media]
	path = /media/data
	read only = No
	browseable = Yes
```

I don't know if it is related, but - even though xp can see ubuntu on the network - ubuntu can't see xp or itself.

Hope you can help, because I am close to giving up

---

### Post by spiderbatdad on 2008-06-05
I do it like so:
I run gksu nautilus.
Navigate to the folder I want to share.
Right click on the folder and select 'sharing options.'
Click all appropriate boxes, including 'allow guests without user accounts.'
Voila. It works.

The only thing that initially got in the way was ufw rules.

---

### Post by ragendem on 2008-06-05
> **spiderbatdad said:**
> I do it like so:
I run gksu nautilus.
Navigate to the folder I want to share.
Right click on the folder and select 'sharing options.'
Click all appropriate boxes, including 'allow guests without user accounts.'
Voila. It works.

The only thing that initially got in the way was ufw rules.

Thanks for the suggestion...
Unfortunately that doesn't work for me, I still don't have write access from the xp box.

ufw isn't the problem, it isn't running on this machine

---

### Post by Xiong Chiamiov on 2008-06-05
> **ragendem said:**
> Thanks for the suggestion...
Unfortunately that doesn't work for me, I still don't have write access from the xp box.

ufw isn't the problem, it isn't running on this machine
Do you have read access, just not write?  If so, it's a permissions issue.  You might not have applied them recursively.

---

### Post by spiderbatdad on 2008-06-05
Indeed it does sound like a permissions problem. chmod -R 766 should do fine.

---

### Post by ragendem on 2008-06-05
> **spiderbatdad said:**
> Indeed it does sound like a permissions problem. chmod -R 766 should do fine.

Thanks for the suggestion. After I tried that I rebooted and windows no longer had read permission.



so I moved my smb.conf to smb.conf.old (because I had made a bunch of changes by hand) and reinstalled samba and used swat to make a new smb.conf.



I tried to share the folder in nautilus and I couldn't check the "allow guests to change files" option.

I tried again with the "samba" tool under administration. It made some changes that were commented, so I uncommented them.

This is what my smb.conf looks like now
```

[global]
	workgroup = HOMENET
	security = SHARE
	guest ok = Yes

[data]
	path = /media/data
	read only = No
	available = Yes
```

And now I have rw access from xp to ubuntu... for now.
thanks for your help everyone

---

### Post by spiderbatdad on 2008-06-05
Just for clarification: when you chmod a directory or file, you don't have to reboot. The changes in permissions take effect immediately. When you want to use the graphical sharing options, run "gksu nautilus" and navigate to the files you want to share.

---

