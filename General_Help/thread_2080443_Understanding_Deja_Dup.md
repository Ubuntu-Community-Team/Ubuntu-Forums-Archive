---
title: "Understanding Deja Dup"
date: 2012-11-04
forum: General Help
---

### Post by hbj on 2012-11-04
Hello,

I would appreciate it if somebody could explain to me a little more about Deja Dup (duplicity) for backups.  My system:

fs01 : file server running 12.04 server
ws01 : workstation running 12.04 desktop, NFS-mounted home

I would like to make backups to an external USB hard drive formatted with ext4.  Home directories can be reached at /h/(USER) on each system.  The backups external drive will be at /mnt/backups on fs01.

If I set up deja dup, what computer does it run on - the fileserver or the workstation?  It seems like it should be running on the fileserver, with the external USB drive also plugged into the fileserver.

If deja-dup runs on the workstation, it will pull all the home directory data over the network.  And, if the external hard drive is on the fileserver, home directory backups will have to send data from fs01 to ws01 and then back to the external drive on fs01.

So, what system (fs01 or ws01) will be running deja-dup after I set it up?

Thanks

---

### Post by timgood on 2012-11-04
AFAIK it should run on the computer on which it was started. Once you have set your preferences you can automatically back up your folders to a specified location.

---

### Post by hbj on 2012-11-04
I still don't think it's clear what happens with NFS mounted home directories.  What if I log in to a couple different workstations?  The backup should be running on the fileserver, not the individual workstations.

Does using something simple like Deja Dup not make sense for NFS-mounted home directories and multiple workstations?

---

### Post by timgood on 2012-11-05
> **hbj said:**
> I still don't think it's clear what happens with NFS mounted home directories.  What if I log in to a couple different workstations?  The backup should be running on the fileserver, not the individual workstations.

Does using something simple like Deja Dup not make sense for NFS-mounted home directories and multiple workstations?

If you want it to run on the fileserver, start it on the fileserver. Or am I missing something here?

---

### Post by hbj on 2012-11-05
The thing is that normally you don't log on to the fileserver - just the workstation.  When I tried to do this before, I would get errors when I logged in to the workstation about the backup software not finding the path to the backup drive.  So it seemed like it was trying to run something periodically on the workstation.  Which is the source of the confusion.

---

