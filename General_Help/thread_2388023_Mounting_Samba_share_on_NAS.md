---
title: "Mounting Samba share on NAS"
date: 2018-03-27
forum: General Help
---

### Post by gavinjb on 2018-03-27
Hi,

I am having some issues trying to mount a Samba share from my NAS, I have looked through the forums and found several posts but for some reason for each of the posts if I change it to use my IP Address I get an error, I am hoping someone can help.

The current syntax I am using is

```

mount //ipaddress/Backups -t cifs -o uid=1000,gid=1000,credentials=/etc/.smbcredentials /media/back

```

The .smbcredentials file contains
username=myusername
password=mypassword

I get back mount error(95) Operation not supported when I run the mount.

Also once I have this working and have changed this to work in my fstab does anyone know of a way to get Linux to mount the share when it becomes available e.g. I power on NAS after my machine is booted and the share is mounted.


Thanks,

---

### Post by gavinjb on 2018-03-27
Found the first issue, it seems that I need to add one of the following

sec=ntlm
vers=1.0

and it works

[https://unix.stackexchange.com/questions/70411/mount-t-cifs-operation-not-supported-but-can-connect-via-smbclient](https://unix.stackexchange.com/questions/70411/mount-t-cifs-operation-not-supported-but-can-connect-via-smbclient)

---

