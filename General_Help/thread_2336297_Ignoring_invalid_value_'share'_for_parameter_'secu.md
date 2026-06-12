---
title: "Ignoring invalid value 'share' for parameter 'security'"
date: 2016-09-06
forum: General Help
---

### Post by mcman56 on 2016-09-06
I can not print to a Canon MX860 connected to a windows box by usb.  I was able to load through Samba and system says it verified connection.  Job attributes for a stuck print file says :  Can't load /etc/samba/smb.conf - run testparm to debug.  (Complete attribute list in attachment.)

testparm produces
dan@dan-NE71B:~$ testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "syslog" option is deprecated
WARNING: Ignoring invalid value 'share' for parameter 'security'
Error loading services.


smb.config does not say much that I understand

```
[global]


    workgroup = workgroup

    server string = %h server (Samba, Ubuntu)



    dns proxy = no








    log file = /var/log/samba/log.%m

    max log size = 1000


    syslog = 0

    panic action = /usr/share/samba/panic-action %d






    obey pam restrictions = no

    unix password sync = yes

    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

    pam password change = yes

    map to guest = bad user





















    usershare allow guests = yes
    security = share
    guest ok = yes
    guest account = dan


[printers]
    comment = All Printers
    browseable = no
    path = /var/spool/samba
    printable = yes
    create mask = 0700

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
    writeable = yes
    guest ok = yes



[Documents]
    path = /home/dan/Documents
    writeable = yes
    guest ok = yes
```

---

### Post by bab1 on 2016-09-06
Use this in the smb.conf file:
security = user

Instead of:
security = share

There is no security = share anymore.

---

### Post by mcman56 on 2016-09-07
Thanks!!  That worked.  I have been struggling with this for a long time.  Although, I'm not sure why user worked in place of share.

---

