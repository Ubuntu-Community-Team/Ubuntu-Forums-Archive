---
title: "smb"
date: 2007-03-14
forum: General Help
---

### Post by helpdeskdan on 2007-03-14
Why on earth would smbmount work fine, but the server/shares are not visible from within places->windows network->Network servers?  Yes, I am using swat - I don't want to think that hard.  I've stopped and restarted everything.  

# Samba config file created using SWAT
# from 127.0.0.1 (127.0.0.1)
# Date: 2007/03/13 23:54:05

[global]
        workgroup = MSHOME
        netbios name = DAN
        server string = %h server (Samba, Ubuntu)
        obey pam restrictions = Yes
        passdb backend = tdbsam
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        panic action = /usr/share/samba/panic-action %d
        invalid users = root

[pictures]
        path = /media/sda4/Pics
        read only = No

cat /etc/fstab
UUID=F89C-3D8A  /media/sda1     vfat    defaults,utf8,umask=000,gid=46 0       1
# /dev/sda4

---

