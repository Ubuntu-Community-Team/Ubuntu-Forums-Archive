---
title: "Accesing Lan Printer"
date: 2008-06-12
forum: General Help
---

### Post by barisint on 2008-06-12
I have a trouble with my lan printer. Yesterday i tried to connect printer in my lan which connected to Vista machine. I use Ubuntu 8.04. To access &#305; used printing configuration tools (system>Administriation>Configure Printers) I think i mess it up. This tool does not work anymore.  What should i do to conect printer and how can i fix printer configuration (Removing via synaptic does not work) 

this is output for testparm
> root@Linux:/home/linux# testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
ERROR: lock directory /var/run/samba does not exist
ERROR: pid directory /var/run/samba does not exist
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions
 
[global]
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
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

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

---

