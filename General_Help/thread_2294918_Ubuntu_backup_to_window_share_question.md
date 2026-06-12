---
title: "Ubuntu backup to window share question"
date: 2015-09-14
forum: General Help
---

### Post by AgentZ86 on 2015-09-14
I am backing up one Home folder from one ubuntu computer to a second ubuntu computer / folder on the network
This seems to be working as it should using the Ubuntu Backups

However, I may have some problem when trying to backup a few files from the second computer, back to the Home computer on the first ubuntu computer.
Will the backup from the first computer be able to handle backing up the files that I backed up from the second computer to the first ?

In otherwords thee is a main shared folder that I'm backing up from the first computer. However, the second computer has a few files such as thunderbird, and a few other python scripts in my home folder. So in this case I backup the second computer home files that I select to the Home folder of the first computer shared folder.

So in turn this backup from the second computer will get backed up again when the backup cron for the first computer runs again. And it will be backed up back to my backup location on the second computer.

Will this create problems for me to backup an already created backup.

Please advise
Thanks

---

### Post by mikewhatever on 2015-09-14
This is a messy setup. Why not backup both machines directly to the Samba server?

---

### Post by AgentZ86 on 2015-09-14
> **mikewhatever said:**
> This is a messy setup. Why not backup both machines directly to the Samba server?


I don't know what this means ? 
These are just desktop ubuntu machines.
Should I be setting up a samba server 

Please advise

---

### Post by mikewhatever on 2015-09-15
Sharing a folder on an Ubuntu machine, gets samba server installed. It's also known as Windows share.

---

