---
title: "To make a backup can i just copy and paste everything on my hdd to an external drive?"
date: 2016-09-25
forum: General Help
---

### Post by 5hutd0wn on 2016-09-25
Im using Ubuntu 16.04 having had many... problems with my BIOS can I just copy everything in the hdd to an external drive?  Would the boot loader still work?  If not could i manually reinstall boot loader?  If its not possible is their another way to store an app backup?   I backup my files to another partition but cant fine a way to do that with apps.

---

### Post by TheFu on 2016-09-25
No.

Backups need to maintain ownership, groups, permissions and ACLs.  Also, hardlinks and symbolic links need to be maintained.

If the things you want to backup are just owned by your userid, stored in your HOME, and not programs, then yes, you can just copy those things off.

There are 500 different ways to do backups.  The problem with point-n-click solutions is they cannot easily be automated to run daily, when you aren't on the PC, perhaps at 1am.  While I don't agree with the tool selection, here's a few links to reputable Ubuntu pages about it: 
* [https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
* [https://help.ubuntu.com/lts/serverguide/backups.html](https://help.ubuntu.com/lts/serverguide/backups.html)
* [http://askubuntu.com/questions/2596/comparison-of-backup-tools](http://askubuntu.com/questions/2596/comparison-of-backup-tools)
* [http://askubuntu.com/questions/7809/how-to-back-up-my-entire-system](http://askubuntu.com/questions/7809/how-to-back-up-my-entire-system)

I use rdiff-backup and have for about 7 yrs. Works very similar to **rsync**, which is a tool that everyone should know and understand almost as much as **ssh**, IMHO. 

Anyway, that's a little reading to get you started.  Don't use tar. There are reasons this is NOT a good way to backup a system.  tar with compression is sorta like ZIP. Size is the real issue for tar-based backups. After about 500MB, it becomes less and less useful, really quickly.

---

