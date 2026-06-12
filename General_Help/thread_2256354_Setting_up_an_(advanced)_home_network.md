---
title: "Setting up an (advanced) home network"
date: 2014-12-11
forum: General Help
---

### Post by Amon_Re on 2014-12-11
Here's the situation: I'm an amateur photographer and I'm very productive in that field which results in a huge dataset (currently over 4TB combined with all the other data). As such I need an easy way to manage all that data and backups.
Currently, everything is contained within a desktop computer with 2 disks (combined with btrfs). Lately however, this setup has been showing it's limits. My backup application (crashplan) is eating more & more cpu cycles and the machine is getting more & more sluggish (especially at boot). I also have a mame type setup and that too needs storage.

I've been considering of doing the following:
1 itx 'mini' computer with 3 old school drives and 1 ssd to serve the data to the desktop and emulation station from which I want to serve my home folder to my desktop and a sub folder of that to the emulation station. On this machine I want to run Crashplan and monitoring/alerting software to keep an eye on the backups & disks.

I have a pretty good idea on the monitoring and alerting aspect but I'm not too sure on how to handle the file sharing part. The obvious choice for this is NFS as I only run linux systems but that's where it gets a bit hairy. NFS uses linux uids so these have to match on all systems. Since I have more than just these few systems keeping all these uids lined up seems like a messy arrangement so I need to figure out how solve this. How would you guys advance from here?

---

### Post by TheFu on 2014-12-11
It really isn't an issue to match userids and groupids for a small business on each system. It isn't like there are 50+ users and people coming and going all the time.  Manually matching the uid/gid is fairly trivial.  If you have more than 5 machines, check out using Ansible to manage the files.  Be careful copying files - you really want to tell ansible to add new userids/groups so it will use the system commands. This will handle the shadow files too. If you have lots of userids and lots of systems, that is what LDAP and kerberos are about.  For less than 50 people, I'd manually do it.  If you don't care about security, you could use NIS, but that is just scary insecure.

NFS is the correct answer.

Hopefully, you are following the 3-2-1 backup methodology. A mirror is not enough.

---

