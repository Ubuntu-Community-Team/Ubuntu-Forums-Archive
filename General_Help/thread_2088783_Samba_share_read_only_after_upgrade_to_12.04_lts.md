---
title: "Samba share read only after upgrade to 12.04 lts"
date: 2012-11-27
forum: General Help
---

### Post by phil1948 on 2012-11-27
I recently upgraded from 10.04.1 LTS to 12.04.1 LTS.  I have multiple samba shares.  I have the shares mapped to network drives in both Windows XP and Win 7.  One of the shares became read only after the upgrade.  I can still write to the other shares. The behavior is the same in both version of windows.  I could write to all shares before the upgrade.  Output of testparm and ls -l follow.  Entries for zz and x appear to be identical, but I can no longer write to zz, but can write to x.

Output of testparm:

[global]
    workgroup = MSHOME
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    username map = /etc/samba/smbusers
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    name resolve order = lmhosts host wins bcast
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb

[homes]
    comment = Home Directories
    read only = No
    create mask = 0775
    directory mask = 0775
    browseable = No

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    print ok = Yes
    browseable = No

[zz]
    path = /media/Raid5/ZZ
    valid users = phil
    read only = No
    create mask = 0770

[x]
    path = /media/Raid5/xxx
    valid users = phil, media
    read only = No
    create mask = 0770

[Share]
    path = /media/Raid5/Share
    valid users = phil, media
    read only = No
    create mask = 0770

[backups]
    path = /media/Raid5/pc-backups
    valid users = phil, media
    read only = No
    create mask = 0770

[W]
    path = /media/SD/WW
    valid users = phil
    read only = No
    create mask = 0770

Output of ls -l //media/Raid5

total 32
drwx------  2 root root  16384 Dec  6  2010 lost+found
drwxr-x--- 32 phil phil   4096 Sep  3 09:43 ZZ
drwxrwxr-x 12 phil media  4096 Jun 11 09:58 pc-backups
drwxrwxr-x 12 phil media  4096 Nov 27 01:00 Share
drwxr-x--- 14 phil phil   4096 Nov 27 11:06 xxx

---

### Post by zero2xiii on 2012-11-27
> **phil1948 said:**
>  Entries for zz and x appear to be identical, but I can no longer write to zz, but can write to x.



[zz]
    path = /media/Raid5/ZZ
    valid users = phil
    read only = No
    create mask = 0770

[x]
    path = /media/Raid5/xxx
    valid users = phil, media
    read only = No
    create mask = 0770



Hay,

Just for testing purposes, check what happens if you add user media to the zz path. Also create a file in the x folder and see who owns it? Might give you a hint if it a user issue or somewhere more complex.

Also check the local owners of the folders. x might be owned by user A and zz might be owned by say 'samba' or 'share' without the correct permissions set.

Regards

---

### Post by phil1948 on 2012-11-28
I added media to the valid users list,  No change in behavior. 

I moved a file from my win 7 pc to xxx.  It has permission "-rwxrw----", not consistent with create mask "0770" specified in the smb.conf file.  It is owned by phil, group phil.

During the upgrade, I received a message about saving the old smb.conf file.  I didn't understand the significance, so I simply hit the "forward" button.  It replied with a message box filled with rectangles instead of characters, which I closed.

This was similar to the message boxes I received each time the upgrade was going to restart a service.  I simply hit the "forward" button.  When I noticed the check box to restart services automatically, I checked that box.  It replied with a message box full of rectangles instead of characters.  When I closed the message box, it proceeded without pausing to ask about restarting services again.

testparm shows the changes I make to /etc/samba/smb.conf, but I'm wondering if another configuration file is in play.

---

