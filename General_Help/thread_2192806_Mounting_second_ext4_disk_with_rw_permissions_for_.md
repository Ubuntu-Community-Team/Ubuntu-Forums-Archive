---
title: "Mounting second ext4 disk with rw permissions for all users."
date: 2013-12-09
forum: General Help
---

### Post by punk45rock on 2013-12-09
I would like to mount my second drive so all users have rw permissions for the entire disk, including files/folders created by one user to be modified by another.This is the line for the disk in fstab UUID=5320ff25-50fa-4581-ac7b-ec1bfe11be92 /mnt/media      ext4    defaults        0       2

---

### Post by bab1 on 2013-12-09
> **punk45rock said:**
> I would like to mount my second drive so all users have rw permissions for the entire disk, including files/folders created by one user to be modified by another.This is the line for the disk in fstab UUID=5320ff25-50fa-4581-ac7b-ec1bfe11be92 /mnt/media      ext4    defaults        0       2
Are these users remote to this machine or are they users of this machine?  In other words, is this a file server (NAS) or a computer used by more than one person.

---

### Post by jeanjd63 on 2013-12-10
Hello 
You can do this by the commande chmod:
**sudo  chmod  -R   a+w   /mnt/media**
 
That's all.
Bye

---

### Post by punk45rock on 2013-12-10
bab1: This is a computer used by more than one person, but I'm also using an NFS share so I can access files from my personal machine.

jeanjd63: Thanks, I will give that a try. Is the "a+w" the equivalent to 777? Because if a new folder/file is created by one user, it is inaccessable to another. 

Thanks

---

### Post by bab1 on 2013-12-10
> **punk45rock said:**
> ...jeanjd63: Thanks, I will give that a try. Is the "a+w" the equivalent to 777? 
This will give you 0666 as the permissions.  No one will be able to get past this directory.  The directory needs to have a+X for users to access.  It should be at the very least 0775. 
> Because if a new folder/file is created by one user, it is inaccessible to another. 

This is the heart of the problem.  What needs to happen is for you to create a common group for all the users that are going to access the directory and it's subdirectories.  This will work for both remote users and local users.

At the root directory for the share (i.e /srv/samba) you set change the group ownership.  If you trust these users then I would just add them (and you) all to the user group named ***users ***```
 sudo chgrp users /srv/samba
```  Then you set the group id bit (sgid) with this```
sudo chmod 2775
```  This allows rw on all files and the ability to access the directory by all users.  The group ***users ***will always be the group on all subsequent files and directories created at or below /srv/samba.  

Then all you need to do is create the Linux user and add it to the ***users*** group.  Then create a Samba user with the same login and password (smbpasswd -a <user> (where <user> is the actual user name.  lastly you create the share at /srv/samba.  Note:  The /srv directory is for just this kind of thing.  Also, I mount a separate 1TB partition at /srv/samba so the data is on it's own HDD.

Ask questions if you don't understand all of this.

---

