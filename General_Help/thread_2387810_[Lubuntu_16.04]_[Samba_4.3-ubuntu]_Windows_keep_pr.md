---
title: "[Lubuntu 16.04] [Samba 4.3-ubuntu] Windows keep prompting no permission when correct"
date: 2018-03-24
forum: General Help
---

### Post by iamttl on 2018-03-24
I've googled everywhere and tried everything regarding this problem, seems like a lot has the same issue and managed to get them fixed but applying their steps doesn't help me at all.

So to give a little background first before going into my problem, my current set up is as follows (This has not yet been hardened):

```
A laptop running (uname -a) : Linux TnayHome 4.4.0-116-generic #140-Ubuntu SMP Mon Feb 12 21:22:43 UTC 2018 i686 i686 i686 GNU/Linux
Samba version (samba --version) : Version 4.3.11-Ubuntu
```

```
Samba shared directory [and subdirs] (ls -la /media):
'sudoer'@TnayHome:~$ ls -la /media
total 24
drwxrwxrwx  6 root root 4096 Mar 19 17:24 .
drwxr-xr-x 23 root root 4096 Mar 22 21:42 ..
drwxrwx---  2 root root 4096 Mar 12 00:13 cdrom
drwxrwx--- 13 tnay tnay 4096 Feb 12 05:54 TCloud
drwxrwx--- 56 tnay tnay 4096 Feb 19 04:35 TPhoto
```


```

Within TCloud (ls -ltra /media/TCloud) :
drwxrwx---  2 tnay tnay 16384 Dec 19  2016 lost+found
drwxrwx--- 13 tnay tnay  4096 Feb 12 05:54 .
drwxrwx---  5 tnay tnay  4096 Feb 12 06:33 TShare
drwxrwxrwx  6 root root  4096 Mar 19 17:24 ..
drwxrwx--- 16 tl   tl  4096 Mar 20 21:35 tl

```

```
Mounted external drive:
UUID=d7585cb...202       /media/TPhoto   ext4    defaults        0       0
UUID=66c3b7...094       /media/TCloud   ext4    defaults        0       0
```

```
Overseer user (sudo grep tnay /etc/passwd) : tnay:x:1002:1002::/home/tnay:/usr/sbin/nologin
Overseer user groups (id tnay) : uid=1002(tnay) gid=1002(tnay) groups=1002(tnay),1001(tl)
```

```
Normal user (sudo grep tl /etc/passwd) : tl:x:1001:1002::/media/TCloud/tl/:/bin/bash
Normal user groups (id tl) : uid=1001(tl) gid=1002(tnay) groups=1002(tnay),1001(tl)
(sudo pdbedit -L -v) :
---------------
Unix username:        tl
NT username:
Account Flags:        [U          ]
User SID:             S-1-5-21-1532872101-1551232975-3276755176-1003
Primary Group SID:    S-1-5-21-1532872101-1551232975-3276755176-513
Full Name:
Home Directory:       \\tnayhome\tl
HomeDir Drive:
Logon Script:
Profile Path:         \\tnayhome\tl\profile
Domain:               TNAYHOME
Account desc:
Workstations:
Munged dial:
Logon time:           0
Logoff time:          never
Kickoff time:         never
Password last set:    Sat, 24 Mar 2018 00:15:20 +08
Password can change:  Sat, 24 Mar 2018 00:15:20 +08
Password must change: never
Last bad password   : 0
Bad password count  : 0
Logon hours         : FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF
```

```
Samba config (testparm):
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "syslog" option is deprecated
Processing section "[TnayHome]"
Loaded services file OK.
Server role: ROLE_STANDALONE

Press enter to see a dump of your service definitions

# Global parameters
[global]
        workgroup = TNAY
        server string = %h server (Samba, Ubuntu)
        server role = standalone server
        security = USER
        map to guest = Bad User
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        server max protocol = SMB2
        max protocol = SMB2
        protocol = SMB2
        server min protocol = SMB2
        min protocol = SMB2
        client max protocol = SMB2
        client min protocol = SMB2
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
        idmap config * : backend = tdb


[TnayHome]
        comment = Public Share
        path = /media
        read only = No
        create mask = 0777
        directory mask = 0777
        directory mode = 0777
```

################################################ Problem #####################################################

When I accessed this samba server, i'm prompted to login after keying in the IP address, which i did with the tl account.
But right when i double clicks on [TnayHome] shared folder, I'm greeted with :

> "You do not have permission to access \\(IP)\TnayHome. Contact your network administrator to request access."

"su - tl" i'm able to traverse to any part of TCloud.

Looking at the folder permissions gave me this (picture below):

[https://scontent.fsin1-1.fna.fbcdn.net/v/t1.0-9/29511674_10160114471685721_6695228279981914140_n.jpg?_nc_cat=0&oh=eedef66f6f288dc357ab7949ff3fd603&oe=5B276CF0](https://scontent.fsin1-1.fna.fbcdn.net/v/t1.0-9/29511674_10160114471685721_6695228279981914140_n.jpg?_nc_cat=0&oh=eedef66f6f288dc357ab7949ff3fd603&oe=5B276CF0)

What's wrong?

---

### Post by coffeecat on 2018-03-26
Not a tutorial. *Thread moved to **General Help**.*

Please be respectful of those with limited bandwidth or who are using mobile devices to view the forum by not embedding oversized images in posts. I have reduced your image to a hyperlink so that it is still visible to those who wish to do so. You can upload an image to the forum by using the paperclip icon in the advanced editor toolbar - this will produce a clickable thumbnail.

---

### Post by iamttl on 2018-03-30
thanks for the note

and bump

---

