---
title: "Samba force group problem"
date: 2008-03-28
forum: General Help
---

### Post by morticae on 2008-03-28
Alright I'm running out of ideas.
I am trying to set up my www directory so that any files written over samba will be group www-data.  Simple enough.

Problem is, Samba works fine without "force group = www-data".  It works fine with other groups there as well, just not www-data.  With www-data there, it refuses to let me log in at all.  With +www-data, it lets me log in, but files are created with group "root"... hardly what I'd call "intended behavior".

I'm going to dump some info here.  If anyone can find anything wrong please tell me.

--------------------------------------------------------------------------------------------
bob@sandbox:~$ sudo testparm /etc/samba/smb.conf 
Load smb config files from /etc/samba/smb.conf
Processing section "[www]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        workgroup = [removed]
        server string = %h server smb
        interfaces = [removed], eth0
        bind interfaces only = Yes
        obey pam restrictions = Yes
        passdb backend = tdbsam
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        load printers = No
        printcap name = /dev/null
        disable spoolss = Yes
        dns proxy = No
        panic action = /usr/share/samba/panic-action %d
        invalid users = root

[www]
        comment = Web Directory
        path = /var/www
        valid users = bob
        force group = www-data
        read only = No
        force create mode = 0774
        force directory mode = 0775

bob@sandbox:/var$ sudo ls -la | grep www
drwxrwxr-x 12 www-data www-data  376 2008-03-28 15:56 www

bob@sandbox:/var/www$ groups
bob adm dialout cdrom floppy audio dip www-data video plugdev scanner lpadmin admin
--------------------------------------------------------------------------------------------

If I change that one line to "force group = admin" it works fine, everything created with group admin.  I thought it was maybe parsing the dash '-' in www-data as something, but I can't figure out what.

Ideas please!

---

### Post by SpaceTeddy on 2008-03-29
i have the same thing setup... strikes me very odd. I'll paste the essential parts from my smb.conf so you can compare... but i know that the - in the username does not matter. It really does work here for me... 

> [global]
        log file = /var/log/samba/log.%m
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssucce
ssfully* .
        socket options = TCP_NODELAY
        obey pam restrictions = yes
        interfaces = [removed]
        bind interfaces only = true
        encrypt passwords = true
        passwd program = /usr/bin/passwd %u
        passdb backend = tdbsam
        dns proxy = no
        netbios name = server
        server string = %h server
        invalid users = root
        workgroup = [removed]
        os level = 20
        socket address = [removed]
        security = user
        syslog = 0
        panic action = /usr/share/samba/panic-action %d
        max log size = 1000

       wins support = yes
       name resolve order = lmhosts host wins bcast
       guest account = nobody
       map to guest = Bad User

[http]
        browseable = yes
        writeable = yes
        path = /srv/www
        force group = www-data
        force user = www-data
        valid users = joe, john, @staff
        case sensitive = yes



maybe that helps (a little)

---

