---
title: "RSnapshot with a remote share - SSH vs NFS"
date: 2020-03-11
forum: General Help
---

### Post by elsmandino2 on 2020-03-11
Hi there.

Have just been looking into RSnapshot and it seems like a great piece of software.

If I had the following set home network set up:

Linux PC 1, containing directory "Documents" and
Linux PC 2, containing directory "Backup of Documents"

and I want to run RSnapshot on Linux PC 2 to pull the data off "Documents" to back it up in "Backup of Documents", would it be better to do this via ssh or NFS?

From what I have been reading, both are possible.

---

### Post by TheFu on 2020-03-11
ssh, no doubt.

---

### Post by elsmandino2 on 2020-03-12
Thank you.

Out of interest, what are the benefits of ssh over using NFS?

---

### Post by TheFu on 2020-03-12
> **elsmandino2 said:**
>  Out of interest, what are the benefits of ssh over using NFS?

NFS allows anyone on the machine access to the storage.  Crypto-locker loves that. Usually, the NFS mount is there 100% of the time.  This is asking for the backups to be hacked, corrupted.  NFS usually is not encrypted at the network layer, though NFSv4 can be w/ Kerberos authentication.

With ssh, the backup tool would "pull" files over encrypted tunnels.  Almost all backup tools support the ssh connection method. That connection is only active during backups and with the ssh-keys setup for the purpose.

Both methods can support versioned backups. This is absolutely critical.  Most of my systems have at least 90 days of versioned backups. The higher risk systems get 180 days of versioned backups. Daily reports about the backups show when the changed data is larger than expected.  Last night one of my versioned backups grew by almost 1GB - that's crazy for the server involved.  Usually, only 20MB growth would be expected.  I haven't looked to see what changed to cause the increase .... just looked. Nothing bad. Just moved a directory to a new place.

BTW, rsnapshot uses hardlinks, which is fine for the data, but loses the metadata over time as changes are made. This could be bad.  rdiff-backup doesn't lose file metadata over time. It is tracked too, in the backup data.

---

