---
title: "[Samba] Why is there a folder refresh problem"
date: 2005-06-07
forum: General Help
---

### Post by nodil on 2005-06-07
Hi everyone,

I have a Ubuntu box with samba installed and a w2k/xp client connected. The
operation is good except for one thing. If I create a file on a unix box
also connected it won't appear in a viewed folder on the w2k client unless
the window is manually refreshed. Am I missing something in the config
that will push the new listing to the client?

[global]
        workgroup = ARCADIA

        server string = Samba Server %v
        netbios name = net

        invalid users = root
        preserve case = yes
        short preserve case = yes

        log file = /var/log/samba/log.%m
        max log size = 50

        security = user
        encrypt passwords = yes
        smb passwd file = /etc/samba/smbpasswd

        strict sync = yes
        sync always = yes
        socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
        change notify timeout = 30
        kernel change notify = Yes
        dns proxy = no


[shared]
        comment = shared directories
        path = /var/smb/shared
        valid users = +users +admin
        browseable = yes
        public = no
        writable = yes
        printable = no
        create mask = 0777
        directory mask = 0777

---

### Post by pdk001 on 2005-06-07
please read here before posting [http://www.ubuntuforums.org/showthread.php?t=22348](http://www.ubuntuforums.org/showthread.php?t=22348)

---

