---
title: "can't access samba shares"
date: 2013-02-12
forum: General Help
---

### Post by clarknova on 2013-02-12
I have a file server on the local network with the samba package installed. Until yesterday I was able to access several shares on the server from other hosts on the network. Today I'm not sure why I can't. The smbd service is running, port 445 is open and accessible on the server, the file and directory permissions look correct to me, and I have tried multiple smbd.conf examples from multiple sites.

```
# testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[Movies]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
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
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	idmap config * : backend = tdb

[Movies]
	comment = The Movie Mill
	path = /mnt/2tb/a_v/movies
	create mask = 0755
	guest ok = Yes

```

```
# ls -lah /mnt/2tb/a_v/movies/
total 20G
drwxrwxr-x 48 david david 8.0K Feb 11 23:58 .
drwxr-xr-x  5 david david   41 Dec 30 22:35 ..
drwxrwxr-x 10 david david 4.0K Feb 11 17:15 3D
drwxrwxr-x 18 david david 4.0K Feb 12 06:54 children
drwxrwxr-x  9 david david 4.0K Dec 24 12:11 christmas
```

When I attempt to connect to the server I see the Movies share, but when I attempt to open it I get "access denied". I've tried from both Android and Windows clients, which worked previously.

I'm able to access the same directories via nfs no problem.

---

### Post by kgr132 on 2013-03-06
I'll bump this for you. I have the same problem since upgrading to 12.10. Formerly working shares stopped and now either "login failed" or "access denied" are all get.

---

### Post by luvshines on 2013-03-09
Is this an external HDD mounted to be shared ?

---

