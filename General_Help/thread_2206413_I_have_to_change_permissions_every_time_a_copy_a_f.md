---
title: "I have to change permissions every time a copy a file"
date: 2014-02-18
forum: General Help
---

### Post by Mryusef1 on 2014-02-18
I have been using Ubuntu for a few years now but I continue to have an issue with permissions when I copy files on my network.  Example.  I make a video on my phone and send the video to my main computer.  I have to use "sudo Nautilus" to change the permissions from "nobody" before I can do anything to the video.  I then send the file to my server and have to do the same thing and change permissions again if I want to delete the video on my server.  Is there a way that I can make any file that is put in a folder have the same permission?


Thanks in advance for any help.

---

### Post by papibe on 2014-02-18
Hi Mryusef1.

It looks you are using samba to share a folder over the network. If that's the case, it may be possible to set a few options so that all files copied over the network are saved as your user instead nobody.

Could you open a terminal, run this command, and post back its results (you can copy paste the text):
```
testparm
```
Regards.

---

### Post by Mryusef1 on 2014-03-20
Sorry for the late response.  I thought I would get an email if there was a response.  Here is the testparm.  Thanks for your help

```
yusef@Office:~$ testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
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


[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    print ok = Yes
    browseable = No


[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
yusef@Office:~$
```

---

### Post by QIII on 2014-03-20
Hello!

If you want an email when there is another post, select "Subscribe to this Thread" under "Thread Tools".

Cheers!

---

### Post by papibe on 2014-03-20
Thanks.

It looks like you ran the command on a machine that does not have any share (thus I can't image this where you are copying the file).

Could you double check that, make sure this is the machine you are copying the files to, and if it's not, could you run it again on the recipient machine?

Regards.

---

### Post by Mryusef1 on 2014-03-20
Sorry about that.  Here it is from my server.  This where I copy the files to.

yusef@Media-Server:~$ testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
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


[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	print ok = Yes
	browseable = No


[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
yusef@Media-Server:~$

---

### Post by deadflowr on 2014-03-20
I usually add the line
```
force user = <my name here>
```
to the global section of the smb.conf file
```
sudo nano /etc/samba/smb.conf
```
or graphically
```
gksu gedit /etc/samba/smb.conf
```

save it and close.
restart samba
should be
```
sudo service smbd restart
```
or
```
sudo restart smbd
```

---

