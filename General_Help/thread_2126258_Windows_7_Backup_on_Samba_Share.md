---
title: "Windows 7 Backup on Samba Share"
date: 2013-03-16
forum: General Help
---

### Post by Dumpfheimer on 2013-03-16
Dear Ubuntu Community,

I recently tried to perform a windows 7 Backup onto my samba drive. I was able to select the drive with username and password. But after finishing, when windows actually starts to backup i get this error:

[FONT=arial]The specified network name is no longer available. ([/FONT]*0x80070040*[FONT=arial])

I am using a Ubuntu 12.04 desktop version and windows 7 professional.

Both connected via LAN.

Here is my smb.conf

[/FONT][global]


    workgroup = workgroup
    server string = %h server (Samba, Ubuntu)
    dns proxy = no
    log file = /var/log/samba/log.%m
    max log size = 1000
    syslog = 0
    panic action = /usr/share/samba/panic-action %d
    unix password sync = yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    pam password change = yes
    map to guest = bad user


[BackupStorage]
    comment = System Backup Directory
    path = /mnt/raid/sysbackup/smb
    writeable = yes
    browseable = no
    public = yes
    valid users = BackupService, Trisha, chris
    guest account  = BackupService
    force user = BackupService

Thank you for your help in advance,

chris

---

### Post by Dumpfheimer on 2013-03-16
By the way, accessing the shares normally works without any problem.

And i got the same error on two different pcs:

one windows 7 professional
and one windows 8 professional

thank you

---

