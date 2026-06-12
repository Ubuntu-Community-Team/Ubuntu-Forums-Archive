---
title: "Backtup to NAS won't work"
date: 2024-02-16
forum: General Help
---

### Post by impy101 on 2024-02-16
For the past few days I've been trying to create a backup of my Ubuntu system and have it sent to my NAS. In the desktop environment the machine does see and successfully connect to my NAS, but when I start the backup it endlessly waits for a network connection.

The settings I've used are: smb://backupnas.local/public/

Any help is welcome!

---

### Post by TheFu on 2024-02-16
[LIST=1]
[*]Which backup tool?
[*]What file system does the NAS support?
[*]Are you running the backup with sudo?
[*]What OS for the client and the server?
[*]What NAS device?
[/LIST]

Different backup tools have different limitations. Some won't work correctly with CIFS/SMB and require native Linux file systems on the target.

If the NAS supports NFS, that would be preferred, pretty much always, from a Linux/Unix client.  SMB is a distant, not-to-great, option for nearly all Linux backup tools.  Plus, if the client can mount the backup storage, that means malware can see it too.  There is a common crypto-ware attack that encrypts not just local, but any network mounted storage.  This is why "Pull"ed backups are better than "Pushed" backups.  However, pushed is better than nothing, by far.

If you are backing up files that aren't owned by your userid, then it is required to use sudo/root for the backup tool run.  This complicates remote storage access since it means that the connection, if authenticated by a userid (like CIFS does), would prevent access under sudo/root.  

Additionally, by default, with NFS, a local root account has ZERO privileges on the NFS server. This is by design. There are work arounds and the defaults may be different on a commercial NAS device.

Anyway, nobody can help without that data at a minimum, the Ubuntu Release and the exact NAS model would be helpful to know as well - though many commercial NAS devices have better "how-to" guides than I'd know about.

I think that's it, at least until more details are provided.

---

### Post by impy101 on 2024-02-16
I'm using the default backup tool that comes with Ubuntu; deja dup.  I am using a QNAP TS251+

---

### Post by TheFu on 2024-02-16
> **impy101 said:**
> I'm using the default backup tool that comes with Ubuntu; deja dup.  I am using a QNAP TS251+

and the answers to the other questions?  I don't want to be an explorer digging.

---

### Post by impy101 on 2024-02-16
The NAS does support NFS. I am on Ubuntu 22.04 LTS

---

