---
title: "Ubuntu 16.04 Autofs issues with Admin CIFS shares"
date: 2016-08-24
forum: General Help
---

### Post by darkice83 on 2016-08-24
Hi,
i've recently updated one of my systems from 14.04 to 16.04
i have auto.master using auto.smb to mount cifs shares to /cifs
i have a windows 7 system with several harddrives which i have set up to access via their drive letters \\canyon\D$ \\canyon\G$ etc..
the credentials for this system is in /etc/creds/canyon (as written in auto.smb)

running sudo /etc/auto.smb canyon returns the list with all the shares
 
shawngu@linuxvm:/cifs/canyon$ sudo /etc/auto.smb canyon
-fstype=cifs,uid=$UID,gid=$GID,credentials=/etc/creds/canyon \
         "/ADMIN$" "://canyon/ADMIN$" \
         "/C$" "://canyon/C$" \
         "/E$" "://canyon/E$" \
         "/F$" "://canyon/F$" \
         "/G$" "://canyon/G$" \
         "/N$" "://canyon/N$" \
         "/NETLOGON" "://canyon/NETLOGON" \
         "/O$" "://canyon/O$" \
         "/print$" "://canyon/print$" \
         "/Q$" "://canyon/Q$" \
         "/R$" "://canyon/R$" \
         "/S$" "://canyon/S$" \
         "/Shared Folders" "://canyon/Shared Folders" \
         "/SYSVOL" "://canyon/SYSVOL" \
         "/T$" "://canyon/T$" \
         "/U$" "://canyon/U$" \
         "/V$" "://canyon/V$" \
         "/W$" "://canyon/W$"

when I ls in /cifs/canyon/ i see all the mounts
shawngu@linuxvm:/cifs/canyon$ ls
ADMIN$  C$  E$  F$  G$  N$  NETLOGON  O$  print$  Q$  R$  S$  Shared Folders  SYSVOL  T$  U$  V$  W$

but, when i try to access any share with a $, i get an error
shawngu@linuxvm:/cifs/canyon$ cd E\$/
-bash: cd: E$/: No such file or directory

any non admin share ("Shared Folders") works without a hitch
shawngu@linuxvm:/cifs/canyon/Shared Folders$ ls
Company  Users


So i know a workaround would be to name all my shares (D$ -> D, E$ -> E) in the windows box, however i have several other vms running 14.04 that all point to these admin shares, which would all require their apps to have the mounts changed as well

Thanks for any help you can provide

---

### Post by darkice83 on 2016-09-16
Starting a fresh install of 16.04.1, installing autofs
```
sudo apt-get install autofs -y
sudo apt-get install smbclient -y
sudo apt-get install cifs-utils -y
```
adding this to /etc/auto.master
```
/cifs /etc/auto.smb --timeout=60
```
and creating the file /etc/creds/<servername>
containing
```

username=username
password=password

```
still causes this issue when accessing admin shares
does ubuntu keep a list of known bugs or a bugtracker i can submit this to?

---

