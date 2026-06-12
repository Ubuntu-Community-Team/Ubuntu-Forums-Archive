---
title: "Samba guest-share working from windows but not ubuntu"
date: 2007-09-17
forum: General Help
---

### Post by Helmi on 2007-09-17
Hi,

i just setup a local testing webserver with samba to have comfortable access to the web root. This is working great so far - i can access the guest level share from windows without login credentials - this is as it should be.

I also mounted the share from within ubuntu with the following line in /etc/fstab:

```
//192.168.x.y/www     /net/www        cifs    guest,rw,iocharset=utf8,file_mode=0644,dir_mode=0755,auto       0       0
```

The mount works at first but i don't have write access to it. I mounted several other shares from my local network without problems but none of them are guest-level.

the corresponding smb.conf looks like this:

```

[www]
    comment = Web Directories
    path = /srv/www
    browseable = yes
    read only = no
    guest ok = yes
    guest account = www-data
    writeable = yes
    public = yes
    create mask = 0644
    directory mask = 0755
    force user = www-data
    force group = www-data

```

security in global section is set to 'share'.

Thanks for any help

---

