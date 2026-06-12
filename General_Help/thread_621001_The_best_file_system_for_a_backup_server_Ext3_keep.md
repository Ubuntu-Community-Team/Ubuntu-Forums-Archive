---
title: "The best file system for a backup server? Ext3 keeps on falling over?"
date: 2007-11-23
forum: General Help
---

### Post by RudolfMDLT on 2007-11-23
Hi there,

I have a backup server running in the house, it has two 500gb hdd. I use the one to  backup data to, and then the second to act as a mirror once weekly to the first. Every 2nd or 3rd boot, the machine would not boot and tell me that it needs to start a maintainance session. I then give the root password and run fsck. fsck then finds a whole host of things wrong with the files system. After the check all the data appears to be fine.

Now, the title of this post assumes that the file system is to blame, as the hard drive had no corrupt sectors(assuming fsck checks for this), but I'm open for any other options or advice?

Anyway, is ext3 fine for running a larger file server that handles a lot of data each week or will I be better off with something else?

The box is still running Edgy.

Any help will be appreciated,

Thanks,

Rudolf

Edit: as a bonus, is it possible to view these maintainance sessions over ssh as this box doesn't have a monitor or keyboard and mouse plugged in? When I try ssh, I just get a connection refused error so the machine does have some of it's networking up already?

---

### Post by PmDematagoda on 2007-11-23
It could be that your hard disk drive is failing since the filesystem ext3 is the most reliable and safest of all other file systems. And ext3 would be good enough to run a large file system since it can handle large files and as said before is very reliable, though if you want something faster though less reliable, you can try JFS.

The reason ssh may not work is because such system services and modules are disabled in the maintenance shell which runs the necessary modules and services only for recovering your PC, not for remote logins.

---

