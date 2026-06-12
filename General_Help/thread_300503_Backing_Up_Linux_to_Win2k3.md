---
title: "Backing Up Linux to Win2k3"
date: 2006-11-15
forum: General Help
---

### Post by treydock on 2006-11-15
I have a network setup that consists of Clark Connect Linux Gateway, two Windows 2003 servers , and many windows XP clients.  Also of course a Ubuntu x64 server.  Is it possible for me to backup my linux server's files onto my Windows2003 file server which also has tape drives?

The Ubuntu linux server is my primary web server and mysql server so it's most important to meto back this up.

Thanks

---

### Post by PilotJLR on 2006-11-15
Sure. The exact setup would depend on your backup software... for most, you could export the directories or filesystems you want to backup using Samba. Then mount the SMB share to a unique drive letter on the Windows server. Then setup your backup software to backup that new drive letter.
This would allow you to now need to install an agent (with some backup apps). I know it works on a one or two version old Retrospect at least...

Or - if you have Sym/Veritas BackupExec, then purchase a Linux agent.

---

