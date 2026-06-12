---
title: "Samba configuration - only public directory accessible"
date: 2008-06-06
forum: General Help
---

### Post by antechinus on 2008-06-06
Using Hardy Heron headless server administered via putty.

I've ready the manual, trawled through countless webpages and not been able to work this out - though thats not saying much since i am new to this. Now I am finally resorting to asking you guys.

I have set up Samba on my server. From Windows XP the public directory is accessible - so thats all good. But when I try to log into the homes directory the XP login will not allow me.

After the first login attempt, the login window replaces 'User Name' *linuxlogin* with *XP_MACHINE_NAME/linuxlogin*, doesn't accept my linux password, and waits with the hourglass cursor until I cancel the login window.

So it must be something to do with permissions or passwords.
Please help. 

From >testparm -s
```

[global]
        workgroup = NAME_OF_MY_WORKGROUP
        server string = %h server (Samba, Ubuntu)
        map to guest = Bad User
        obey pam restrictions = Yes
        passdb backend = tdbsam
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        username map = /etc/samba/smbusers
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        printcap name = cups
        dns proxy = No
        wins support = Yes
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
        invalid users = root

[public]
        comment = Public Folder
        path = /home/public
        force user = nobody
        force group = nogroup
        read only = No
        create mask = 0777
        directory mask = 0777
        guest ok = Yes

[homes]
        comment = Home Directories
        path = /home/%S
        read only = No
        guest ok = Yes
```

---

### Post by lisati on 2008-06-06
I'm wondering if the "forceuser" option (or something similar) mentioned in the tutorial at [http://ubuntuforums.org/showthread.php?t=202605&highlight=network+troubleshooting](http://ubuntuforums.org/showthread.php?t=202605&highlight=network+troubleshooting) would be an option. I followed that guide to set up communication between my XP machine & my Ubuntu machine - accessing my Windows shared folders isn't a problem, and accessiing my Ubuntu shared folders from XP asks for my user & password and lets me through no sweat.

---

### Post by antechinus on 2008-06-07
That is a very helpful guide to setting up Samba, Lisati. Thanks. No luck though.
I completely rewrote the smb.conf file based on the one in your link. There are three shared directories setup and all appear in the XP network. Problem is that the login to [MyFiles] does not want to work. So I can access [home] and [public], but not [MyFiles].

I used this as well. Is this supposed to be your linux login? or windows, or doesn't it matter?
```

sudo smbpasswd -L -a your_username
sudo smbpasswd -L -e your_username

```
My smb.conf without global section:
```

[MyFiles]
	path = /home/samba/
	browseable = yes
	read only = no
	guest ok = no
	create mask = 0644
	directory mask = 0755
	force user = david
	force group = david

[homes]
	valid users = %S
	create mode = 0600
	directory mode = 0755
	browseable = no
	read only = no


[public]
	comment = Public Folder
	path = /home/public
	public = yes
	writable = yes
	create mask = 0777
	directory mask = 0777
	force user = nobody
	force group = nogroup
```

---

### Post by reef2dive on 2008-06-07
Hi
Sorry, simple question. Did you create yourself as a sambauser on the server with the command sudo smbpasswd -a yourself? You use the right command, and the user should be the user on linux server that access to the directory. The windows user, it must exist on the server if that is to used, else that user is of no interest.

---

### Post by antechinus on 2008-06-07
I used:
sudo smbpasswd -L -a my_linux_login
sudo smbpasswd -L -e my_linux_login
But the login does not work.

Is the windows login box supposed to display 
*XP_MACHINE_NAME/my_linux_login*
when I type in just
*my_linux_login*  ??

---

### Post by antechinus on 2008-06-07
Well, experimenting with the smb.conf I found login to [homes] on XP works well, but login to [MyFiles] does not work. If I add to [MyFiles]
valid users = %S and comment out the two force statements - problem remains.
If I write force user = %S - problem remains.

I can't work out what part of [MyFiles] is causing the problem. I think I will give up.

```
;MyFiles doesnt work
;[MyFiles]
;       path = /home/samba
;       browseable = yes
;       read only = no
;       guest ok = no
;       create mask = 0644
;       directory mask = 0755
;       force user = david
;       force group = david

[homes]
        valid users = %S
        create mode = 0600
        directory mode = 0755
        browseable = no
        read only = no

```

---

