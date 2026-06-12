---
title: "Samba &lt;-&gt; Unix password sync not working as expected"
date: 2013-05-22
forum: General Help
---

### Post by SaturnusDJ on 2013-05-22
Libpam-smbpass is installed.

Smb config:
```


[global]
	workgroup = WORK
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	load printers = No
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	idmap config * : backend = tdb

[homes]
	comment = Home Directories
	read only = No


```

I also tried 'pam password change = No' which should use the command of 'passwd program.'


After rebooting the Unix password was synced to the Samba password. But this is supposed to happen live, right?

---

### Post by linuxtechguy on 2013-05-22
There is never a need to reboot unless you are doing a kernel update. Try to restart the program instead.

---

### Post by SaturnusDJ on 2013-05-22
True, but
```
service smbd restart
```
doesn't work either. Still no sync.

---

### Post by SaturnusDJ on 2013-05-25
Kick!

Log out + log in works for resync. Not live enough though.

---

