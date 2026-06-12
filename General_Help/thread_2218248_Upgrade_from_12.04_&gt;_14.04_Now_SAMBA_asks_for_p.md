---
title: "Upgrade from 12.04 &gt; 14.04 Now SAMBA asks for password"
date: 2014-04-20
forum: General Help
---

### Post by ericpatch on 2014-04-20
My below SAMBA setup worked perfectly for a few years. I upgraded to 14.04 this morning and now my valid users protected folders ask for a password in windows. The weird part is the home folder still finds my user credentials and works.

The Xfer share is the one now asking for credentials after upgrading. I can view the other shares.

Did a sudo smbpasswd -a MYUSER to make sure I was in there.

**The only change is that I upgraded from 12.04 to 14.04.**

Thanks!

Here is my smb.conf:

[FONT=arial][global][/FONT]
[FONT=arial]        workgroup = MATRIX[/FONT]
[FONT=arial]        netbios name = MEDIA_SERVER[/FONT]
[FONT=arial]        server string = %h server (Samba, Ubuntu)[/FONT]
[FONT=arial]        map to guest = Bad User[/FONT]
[FONT=arial]        obey pam restrictions = Yes[/FONT]
[FONT=arial]        pam password change = Yes[/FONT]
[FONT=arial]        passwd program = /usr/bin/passwd %u[/FONT]
[FONT=arial]        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .[/FONT]
[FONT=arial]        unix password sync = Yes[/FONT]
[FONT=arial]	security = user[/FONT]
[FONT=arial]        syslog = 0[/FONT]
[FONT=arial]        log file = /var/log/samba/log.%m[/FONT]
[FONT=arial]        max log size = 1000[/FONT]
[FONT=arial]        dns proxy = No[/FONT]
[FONT=arial]        usershare allow guests = Yes[/FONT]
[FONT=arial]        panic action = /usr/share/samba/panic-action %d[/FONT]
[FONT=arial]        idmap config * : backend = tdb[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial][homes][/FONT]
[FONT=arial]        comment = Home Directories[/FONT]
[FONT=arial]        valid users = %S[/FONT]
[FONT=arial]        read only = No[/FONT]
[FONT=arial]        create mask = 0700[/FONT]
[FONT=arial]        directory mask = 0700[/FONT]
[FONT=arial]        browseable = No[/FONT]
[FONT=arial] [/FONT]
[FONT=arial][videos][/FONT]
[FONT=arial]        comment = Videos[/FONT]
[FONT=arial]        path = /home/media/video[/FONT]
[FONT=arial]        guest ok = Yes[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial][music][/FONT]
[FONT=arial]        comment = Music[/FONT]
[FONT=arial]        path = /home/media/music[/FONT]
[FONT=arial]        guest ok = Yes[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial][images][/FONT]
[FONT=arial]        comment = Images[/FONT]
[FONT=arial]        path = /home/media/image[/FONT]
[FONT=arial]        guest ok = Yes[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial][Media_Xfer][/FONT]
[FONT=arial]        comment = For transferring media[/FONT]
[FONT=arial]        path = /home/media[/FONT]
[FONT=arial]        valid users = MYUSER[/FONT]
[FONT=arial]        force user = root[/FONT]
[FONT=arial]        force group = root[/FONT]
[FONT=arial]        read only = No[/FONT]
[FONT=arial]        create mask = 0644[/FONT]
[FONT=arial]
[/FONT]

---

### Post by ericpatch on 2014-04-20
Forgot to mention. Even when I put in the proper credentials when prompted, it doesn't allow me access to the Xfer share.

The home share will open without being prompted, I have full access to it. So SAMBA is reading the username and pass just fine. Just not for the Xfer share.

Any ideas? Help greatly appreciated!

---

### Post by ericpatch on 2014-04-20
would it be related to this?: [http://ubuntuforums.org/showthread.php?t=2214042](http://ubuntuforums.org/showthread.php?t=2214042)

I get the memory leak error too.

---

### Post by frente69 on 2014-04-21
I also get the memory leak but that seems to say the solution to it is to disable linux to smb password sync which seems like a not great outcome if you use the password sync...

Anyhow I am also unable to connect to samba shares. I tried disabling password sync but it didn't fix the login issue.
I am unable to log in from a windows(8) pc or from smbclient onthe same server samba is hosted from

---

### Post by ericpatch on 2014-04-21
I'm thinking I'll just have to wait for a fix. I don't think I can fix this as it seems to be an issue with SMB password synchronization. :-(

---

### Post by ericpatch on 2014-04-22
Did I post this in the wrong forum? Or do I just have a puzzling problem?  Thank you

---

### Post by ericpatch on 2014-05-05
I found a way to get it working.  For anyone who may be having the same issue.  I put the force user = account into the valid users = list and it now works. This wasn't required before the upgrade to 14.04.

---

