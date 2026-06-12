---
title: "SSHFS Permissions Issue"
date: 2019-08-15
forum: General Help
---

### Post by ndstate on 2019-08-15
Hi,

I am mounting my Ubuntu server via sshfs (IE: [email]user@104.xxx.xxx.xxx[/email]) and running a backup program on that mounted folder. The problem I am running into is that the server user I am logging in with does not have access to some of the folders on the server. I would normally just use the sudo command to access these folders. Is there some way I can do this via sshfs or otherwise make the folders available? I assume I don't just want to give read permissions for everything to that user...?

Thanks!

---

### Post by TheFu on 2019-08-15
sshfs provides the permissions of the userid used in the connection.  That's the rules.  If the userid you connect as doesn't have the required permissions, sorry. Pick a better userid.

Perhaps using a better backup tool that works over ssh, not sshfs?  Any of them based on librsync work that way.  I'd use rsync for a single time, single directory structure mirror requirement. For backups, I use rdiff-backup, which uses a client/server model over ssh.

In general, for system-level backups, a root or root-equiv account must be used.  If you are just backing up a single HOME directory, then the userid for the HOME you want should be fine.

---

