---
title: "Problems with networking Win98 and Ubuntu"
date: 2005-09-19
forum: General Help
---

### Post by Turb0flat4 on 2005-09-19
Please help. I've tried to get my Ubuntu box talking perfectly with two Win98 boxes on my Linksys NAT router, but it's not 100 % successful.

I am able to view and edit the Windows shares from my Ubuntu box with no problems. I am also able to send messages from Ubuntu/Linpopup to Win98/Winpopup with no problems.

I am *not* able to :

1) Access my Ubuntu share (read/write) from the Windows PCs. I am able to see the PC name appearing in Windows Network Neighborhood but I get an error message on attempting to double click the icon.

2) I am *not* able to send messages from Winpopup on either Win PC to Linpopup on the Ubuntu box. When going by "name" (on winpopup), the message just doesn't get thru (with an error message). When going by "workgroup", a message announcing success appears on the Windows PC but nothing gets thru to the Ubuntu box.

It's not a firewall issue. Kerio (on Windows) and Firestarter/IPtables (on Ubuntu) are configured to allow all connections from internal IPs.

My Windows PCs are set to logon automatically without asking for Usernames/passwords, if that helps any. I'm sorry, I really can't remember whether there's any default user account name I configured into the Windows machines, and I've removed the 'Log off' option from the Start menu a long time ago. The Win98 PCs are able to "see" and "talk" to each other just fine. I have not added any specific user accounts into my Ubuntu box to correspond to the Windows machines, because I wouldn't know how to.

Here is the output of my smb.conf :

"# Samba config file created using SWAT
# from 127.0.0.1 (127.0.0.1)
# Date: 2005/09/18 20:44:55

# Global parameters
[global]
	workgroup = DUCHESS
	server string = %h server (Samba, Ubuntu)
	obey pam restrictions = Yes
	passdb backend = tdbsam, guest
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &
	panic action = /usr/share/samba/panic-action %d
	invalid users = root

[homes]
	comment = Home Directories
	create mask = 0700
	directory mask = 0700
	browseable = No

[printers]
	comment = All Printers
	path = /tmp
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[Documents]
	path = /home/deepak/documents
	read only = No
	guest ok = Yes"

Any ideas, please ? Thanks.  :smile:

---

### Post by Turb0flat4 on 2005-09-20
Bump. Please help.

---

### Post by ektich on 2005-09-20
set 'log level = 4' in your samba.conf file and look carefuly in the /var/log/samba directory. Especialy in the files log.*win_host_name* 

That should give you a clue what user name and passwords are used by Win98 boxes when they talking to the ubuntu box and why they're not allowed to do so.

---

### Post by reaganf2 on 2007-11-29
got the same issue here.. can send popup messages from my ubuntu box to windows box, but not vice versa..

---

