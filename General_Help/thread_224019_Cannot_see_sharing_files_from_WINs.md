---
title: "Cannot see sharing files from WINs"
date: 2006-07-27
forum: General Help
---

### Post by leeyee on 2006-07-27
Hi guys,
I've just setup a Samba server on ubuntu, and sharing files in local area network. It's fortunate for me that those Windows users can see my sharing files via samba and copy/browse them correctly. But that's odd I can't see their sharing files, I don't know how to figure it out, and it seems that most HOWTOs are focus on sharing Linux's files to Windows. Any idea? 
Thank you!

And here is my smb.conf:
```

[global]
    netbios name = Linux
    server string = leeyee's Dapper
    workgroup = MSHOME
    hosts allow = 192.168.0.
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

[Sharing]
    path = /media/samba/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755

```
And thanks for comments on my samba configuration file as well. :p

---

### Post by Paerez on 2006-07-27
does it help at all if you change wins support to no?

---

### Post by leeyee on 2006-07-28
Well, thank you! I will try it.
Any idea to this smb.conf? I'm not sure that if this is enough or bloated for using? Some options of it was just copied from [this]("http://www.ubuntuforums.org/showthread.php?t=202605") HowTo.
Thanks for your comments. Please!

---

