---
title: "BackupPC Restoring though command?"
date: 2018-03-11
forum: General Help
---

### Post by albert41 on 2018-03-11
Hi,
I was wondering if someone could shed some light, currently running backupPC on ubuntu 16.04 and working well. I have the backup directory on a USB external hardrive with EXT4, What I was wondering how can i use that usb on another Host that has BackupPC to extract the backups, I saw options to restore though commands but did not understand.

This is what i know:

the Backuppc_tarCreate is located in 

```
/usr/share/backuppc/bin/Backuppc_tarCreate
```

and my usb is mounted on 

```
/media/usb0/
```

so im guessing i would need to cd the mounted USB

then maybe run this command?

```
/usr/share/backuppc/bin/Backuppc_tarCreate -h 192.168.3.12 -n 0 -s /root > restore.tar
```

Thank you

---

