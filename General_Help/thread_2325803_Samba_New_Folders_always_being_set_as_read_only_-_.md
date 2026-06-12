---
title: "Samba New Folders always being set as read only - 0755"
date: 2016-05-25
forum: General Help
---

### Post by alka5eltzer on 2016-05-25
Hi All,

I have a Windows share called "Pauls Drawings" on my Ubuntu Server

Any time a user creates a new folder - they can save to it, but other users can't. Its being set as 0755.

This is from my conf file:

[global]
	log file = /var/log/samba/log.%m
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	obey pam restrictions = yes
	force directory mode = 777
	map to guest = bad user
	passwd program = /usr/bin/passwd %u
	passdb backend = tdbsam
	dns proxy = no
	netbios name = fileserver
	server string = Linux Fileserver
	path = /home
	unix password sync = yes
	force create mode = 777
	workgroup = WORKGROUP
	os level = 20
	create mode = 777
	syslog = 0
	security = user
	panic action = /usr/share/samba/panic-action %d
	usershare allow guests = yes
	max log size = 1000
	directory mode = 777
	pam password change = yes


[PaulsDrawings]
	writeable = yes
	path = /home/PaulsDrawings
	write list = shay,Paul,Brian,Eamonn,Joe,Trevor,Tracy,Colin,carol,David,Mark,PaulS,Terry,@users
	force directory mode = 777
	force create mode = 777
	valid users = shay,Paul,Brian,Eamonn,Joe,Trevor,Tracy,Colin,carol,David,Mark,PaulS,Terry,@users
	create mode = 777
	directory mode = 777

Where am I going wrong?

The users are valid and also in the correct group?

Thanks

---

