---
title: "flyback backup of my linux filesystem only 4.3 Mb?"
date: 2008-01-17
forum: General Help
---

### Post by realthor on 2008-01-17
Hi, I am trying to learn a few things about system-backups, as I am a windows convert for a few months and yesterday found flyback. Got it installed without errors even if on the flyback page it sais something about installing some dependancies: python python-glade2 python-gnome2 python-sqlite3 python-gconf rsync and from these "python-sqlite3" does not exist in ubutu repos.

But I,ve run a complete fylesystem backup and I got a 4.3 MB folder with 21744 items. As I understand it's a sort of Time Machine from OSX but that one does a full HDD backup on first run and then makes incremental backups. My first backup shouldn't have been similar?

My question: Is this ok for a flyback backup? I can see many folders that are empty. On a system restore what will be restored for those folders?

Thanks.

---

### Post by crmccreary on 2008-07-20
flyback is a nifty frontend to some aspects of rsync that replicate a Time Machine type of backup. As far as completely backing up your system, you will probably just want to back up your home directory. You should be able to navigate through the backup and verify that files you expect to be backed up are indeed backed up.

---

### Post by realthor on 2008-07-21
No, really I want to backup my whole ubuntu system + home folder first time run and then perhaps make incremental backups with whatever changed from first backup. I know what flyback is, don't need to copy/paste anything...so...any answer to my question?

Thanks.

---

