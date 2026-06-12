---
title: "Windows Shares in FSTAB,"
date: 2012-12-31
forum: General Help
---

### Post by ylafont on 2012-12-31
I map a few windows shares in fstab with the following syntax,  
“//server/share /mnt/mountname cifs username=server_user,password=user_password,iocharset=utf8,mode=0777,dir_mode=0777 0 0”  

The Shares mount fine  and I am able to move in around with a remote connection via ssh.  I also have a Samba share to the root (“/”) of the Ubuntu (12.10) box on another windows client.  When  go to those mounted shares within windows explorer the mounted folders are labeled as files and I cannot  navigate within them.   Is there a solution to this?  Thank you.

---

### Post by dino99 on 2012-12-31
make things simple

[http://www.noobslab.com/2012/03/configure-samba-sharing-between-ubuntu.html](http://www.noobslab.com/2012/03/configure-samba-sharing-between-ubuntu.html)

---

### Post by Morbius1 on 2012-12-31
> I also have a Samba share to the root (“/”) of the Ubuntu (12.10) box  on another windows client.  When  go to those mounted shares within  windows explorer the mounted folders are labeled as files and I cannot   navigate within them.I don't think I've ever seen that kind of thing before. Why not post the output of the following commands so the folks here can see how you are set up:
```
testparm -s
``````
net usershare info --long
```

---

### Post by ylafont on 2012-12-31
```
testparm -s
```


[global]
 workgroup = ECLIPSE
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
 name resolve order = wins lmhost hosts bcast
 dns proxy = No
 wins support = Yes
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

[root]
 comment = Ubuntu Root share
 path = /
 username = xbmc
 valid users = xbmc
 read list = xbmc
 write list = xbmc
 force user = root
 read only = No
 acl check permissions = No
 only user = Yes


```
net usershare info --long
```

This command does not produce any results.

---

