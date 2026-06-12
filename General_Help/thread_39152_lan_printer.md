---
title: "lan printer"
date: 2005-06-03
forum: General Help
---

### Post by Xanthous on 2005-06-03
Hi,
I got an error when configuring my network printer (on a win2k box), and was told to run testparm.  
Here is the feedback I got.  Now, how do I fix this?

Thank you!

```
root@ubuntu:/home/dna # testparm
Load smb config files from /etc/samba/smb.conf
Can't find include file /etc/samba/dhcp.conf
Processing section "[homes]"
Processing section "[printers]"
Processing section "[print$]"
params.c:Section() - Badly formed line in configuration file: ]
params.c:pm_process() - Failed.  Error returned from params.c:parse().
Error loading services.

```

---

### Post by jjross on 2005-06-04
I just went through this same problem and what i did was to remove samba and smb in synaptic. when you mark it for removal choose "mark for complete removal" and this should remove all of it including the configuration files.after your done ,simply reload samba and smb and hopefully it will be fixed

iguess i should be more specific. the file names are:
samba
samba-common
samba-dbg
samba-doc
smbclient

---

