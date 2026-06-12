---
title: "mount network files...."
date: 2007-02-27
forum: General Help
---

### Post by Mia_tech on 2007-02-27
guys, I have shares on a network server that should be mapped when my box boots up
I have my /etc/fstab file pointing to the network servers and also created the mount points, with the /root/.smbcredentials files to pass along during the mapping process, but I get an error

cli_negprot: SMB signing is mandatory and we have disabled it.
23705: protocol negotiation failed
SMB connection failed

it happens also when I try to mount the remote folder manually.
any help will be appreciated
thanks

---

### Post by inCursorated on 2007-02-27
what OS version is the server? try CIFS to mount...

---

### Post by Mia_tech on 2007-02-28
> **inCursorated said:**
> what OS version is the server? try CIFS to mount...

is a Windows 2003 server

---

### Post by Mia_tech on 2007-02-28
> **inCursorated said:**
> what OS version is the server? try CIFS to mount...

I have tried it, using automatic mount during logon with /etc/fstab and it didn't work

---

