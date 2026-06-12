---
title: "Share write permissions"
date: 2019-06-07
forum: General Help
---

### Post by jadechessink on 2019-06-07
been trying to make a anonymous share for my internal networking and ive been having some issues setting it so that everybody can write to it. its visible just fine, but it seems like root is the only one able to write to it, can somebody point me in the WRITE direction? ;) 

i havent changed much in the global section since i wasnt sure if i needed to, but this is mostly defaults here. 

samba share testparm:
[global]
    dns proxy = No
    log file = /var/log/samba/log.%m
    map to guest = Bad User
    max log size = 1000
    netbios name = HOMESERV
    obey pam restrictions = Yes
    pam password change = Yes
    panic action = /usr/share/samba/panic-action %d
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    passwd program = /usr/bin/passwd %u
    server role = standalone server
    server string = %h server (Samba, Ubuntu)
    syslog = 0
    unix password sync = Yes
    usershare allow guests = Yes
    idmap config * : backend = tdb
    create mask = 0777
    directory mask = 0777


[Share]
    comment = Plex Share
    guest ok = Yes
    path = /data/
    read only = No



server fstab entry:
//192.168.1.2/Share/ /data/ cifs rw,guest,iocharset=utf8,sec=ntlm,nosetuids,noperm       0 0

---

### Post by jadechessink on 2019-06-07
i also tried a very basic version as follows with no change:
# Global parameters
[global]
    log file = /var/log/samba/%m
    map to guest = Bad User
    idmap config * : backend = tdb


[Share]
    force create mode = 0777
    force directory mode = 0777
    guest ok = Yes
    path = /data/
    read only = No

---

### Post by Morbius1 on 2019-06-07
I'm a little confused by your post.

Does each client user from his own machine access this server with the same fstab statement:
> //192.168.1.2/Share/ /data/ cifs rw,guest,iocharset=utf8,sec=ntlm,nosetuids,noperm       0 0         
If so you need to take possession of the mounted share by specifying the owner:
> //192.168.1.2/Share/ /data/ cifs rw,guest,iocharset=utf8,sec=ntlm,nosetuids,noperm[COLOR=#0000cd]**,uid=XXXX **[/COLOR]      0 0         

XXXX can be a username like "uid=morbius" or it can be the actual uid number which in my case would be "uid=1000"

---

### Post by jadechessink on 2019-06-07
Hello Morbius, 

all clients have that, i removed UID since its anon and didn't change functionality when testing.

---

### Post by Morbius1 on 2019-06-07
I don't understand your post. The uid on the client side cifs mount has nothing to do with the it being a guest share or not. Cifs is a virtual filesystem. Without specifying the uid or using something like dir_mode / file_mode a cifs mount with have owner = root and permissions of 755. Writeable only to root.

---

### Post by jadechessink on 2019-06-07
Changed the Fstab to have a UID and GUID and i still only get read/executable permissions:

//192.168.1.2/Share/ /data/ cifs rw,guest,uid=1000,gid=1000       0 0 

    0 drwxr-xr-x 2 james james        0 Mar 16 17:44 'Web Development'

---

### Post by Morbius1 on 2019-06-07
> Changed the Fstab to have a UID and GUID and i still only get read/executable permissions:
Not to james.


"nobody" does have write permissions on the /data folder on the server, right? I'm talking about Linux permissions here.

On the server run the following command:
```
ls -dl /data
```

When this is executed on the client:
>  //192.168.1.2/Share/ /data/ cifs rw,guest,uid=1000,gid=1000       0 0 
The only user the server sees is the guest account which is literally "nobody" on the server. So the Linux permissions on the server has to be 777 in order for an actual write to take place.

---

