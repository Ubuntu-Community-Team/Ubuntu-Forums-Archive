---
title: "Can i extend my lvm with a SMB or something else?"
date: 2016-06-23
forum: General Help
---

### Post by jonathan63 on 2016-06-23
Helllo, 

I'am wondering if i can extend my linux partition with space of a mounted SMB? I'm running a owncloud server on a VPS with  +- 40gb of disk space on ubuntu 14.04, and i want to add extra diskspace. In owncloud you can add external storage, but it doesn't add up to the total amount of diskspace off my owncloud server.  

What'ts the best/secure/easiest way to accomplish this? I was thinking maybe to mount a share over sshfs, but i dont know how to extend my LVM or how to span my owncloud folder over 2 drives.. In owncloud you can't just add a second data folder.. :/ 

Kind regards, and sry for the bad english.. ;) 

Sincerely, a *nix noob.. :)-

---

### Post by TheFu on 2016-06-23
Probably not. LVM needs PEs inside PVs inside VGs to be added to LVs.  For PEs, you need block storage - for network storage, that means iSCSI or AoE.  Those don't work securely over the internet.

However, you can mount remote storage using sshfs, if you like.  Just create a directory to use at the mount point.  It will be slow. It isn't 100% compatible with ext4, but most things normal people use do work.  Plus it uses the ssh config/port/security/keys you probably already have setup. No need for LVM to know anything about the sshfs added stuff.

Why not just pay for more storage from the VPS provider?

---

