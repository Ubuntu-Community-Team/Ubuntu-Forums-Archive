---
title: "Network drive/shares not mounted at boot up"
date: 2018-01-23
forum: General Help
---

### Post by alain.roger on 2018-01-23
Hi,

My computer works on Ubuntu 17.10 with KDE 5.11.5.
At boot up computer should mount network/share drives from my NAS.

from time to time (today for example) when i'm logged in my share drives are not mounted and i must open a terminal and type: sudo mount -a

in my fstab i have the following mounting points:
```
[FONT=monospace][COLOR=#000000]//n4200eco/Work         /mnt/work       cifs comment=systemd.automount,vers=1.0,iocharset=utf8,credentials=/home/alain/.smbcredential[/COLOR]
s,uid=1000 0 0[/FONT]
```

my credential are correct, so what could be the problem ?

thx

---

### Post by deadflowr on 2018-01-23
I think most people find adding the _netdev option helps as that makes it so that fstab does not try to mount network drives until the networking connection has been established.
(and that's exactly how it's spelled by the way _netdev

---

### Post by alain.roger on 2018-01-23
i tried without success:
```
//n4200eco/Work		/mnt/work	cifs comment=systemd.automount,vers=1.0,iocharset=utf8,_netdev,credentials=/home/alain/.smbcredentials,uid=1000 0 0
```

---

### Post by deadflowr on 2018-01-23
Is home encrypted?

---

### Post by alain.roger on 2018-01-23
not at all

I mainly use wifi to connect to my NAS. Would wifi have a bigger impact than 1gb ethernet cable on the way network drives are mounted ?

in fact since i type _netdev in /etc/fstab, it's worse than before.
now in terminal none of my network shares is mounted and when i type in terminal, sudo mount -a, i get the following result:
```
[FONT=monospace][COLOR=#000000]mount error(16): Device or resource busy[/COLOR]
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
mount error(16): Device or resource busy
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
mount error(16): Device or resource busy
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)[/FONT]
```

while all ressources are available and once done, all network shares are mounted correctly.

---

### Post by alain.roger on 2018-01-25
In fact, on my desktop computer i have absolutely the same lines in my /etc/fstab that my laptop has and it works without any trouble.
So i would like to understand if my WIFI connection is not the root cause why shares mounted points are not connected at boot.

Is there a way to force wifi connection to start sooner than other services ?

---

### Post by alain.roger on 2018-01-26
For unknown reason when i disabke my firewall UFW, suddenly all shares connections were automounted in Dolphin.
It seems that at boot up, firewall blocks my shares connections till i log in and mount manually.

I discovered that on my desktop UFW is set to Office, while on laptop is set to Personal files. Could it have an impact on shares connections ?

---

### Post by alain.roger on 2018-01-26
so i tested a lot of different settings and while _netdev did not work for me i finally found a working setting as following:
[FONT=monospace][COLOR=#000000]//192.168.1.100/Storage /mnt/storage    cifs x-systemd.automount,x-systemd.device-timeout=60,vers=1.0,iocharset=utf8,credentials=/home/alain/.smbcredentials,uid=1000,gid=users,file_mode=0775,dir_mode=0775 0 0[/COLOR]

HTH those who like me use wifi connection on laptop to connect to NAS.

[/FONT]

---

### Post by jwbrown on 2018-10-12
> **alain.roger said:**
> so i tested a lot of different settings and while _netdev did not work for me i finally found a working setting as following:
[FONT=monospace][COLOR=#000000]//192.168.1.100/Storage /mnt/storage    cifs x-systemd.automount,x-systemd.device-timeout=60,vers=1.0,iocharset=utf8,credentials=/home/alain/.smbcredentials,uid=1000,gid=users,file_mode=0775,dir_mode=0775 0 0[/COLOR]

HTH those who like me use wifi connection on laptop to connect to NAS.

[/FONT]

Adding:

x-systemd.automount,x-systemd.device-timeout=60,vers=1.0,

to my samba share mount line after the "cifs" worked for me in Kubuntu 18.04,

Thanks

---

### Post by tcolley on 2019-03-07
I tried these options to solve the same problem on Ubuntu 18.04LTS:

[LIST]
[*]Insert "comment=systemd.automount" into the relevant mount statements in /etc/fstab. PROBLEM: This option produced multiple mounts of the same network shares when I tried to use it for two different network shares. 
[*]Insert "mount -a" into /etc/rc.local. PROBLEM:This seemed to have no effect! 
[*]As superuser, create a script with the following text in directory /etc/network/if-up.d/ and give it execute permissions: 
[/LIST]
          ```
#!/bin/sh
mount -a
```
The last solution works well. Scripts located in /etc/network/if-up.d/ run after a network connection is established. This script then mounts the network shares (and any other pending mounts) already stipulated in /etc/fstab.

---

