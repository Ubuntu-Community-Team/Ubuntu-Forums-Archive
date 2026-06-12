---
title: "I need help with file permissions in Ubuntu 18"
date: 2020-03-17
forum: General Help
---

### Post by cag1999 on 2020-03-17
I am running Ubuntu 18.04 LTS.

I had an SSD that failed while running Ubuntu 16.04 LTS.  I was able to recover the files I cared to recover and saved them to my Desktop (/home/Administrator/Ubuntu16_Recovery_Folder).

The owner of this Recovery Folder is "Me" (Administrator).  I can traverse the folders and open the files in this recovery folder.  I can create new files.  However, I cannot move them to a network location, though.  I've tried chmod to various permission levels (644, 777, 755, ...).  Currently, a child file in this folder appears to allow r/w for owner, group, and others.  I still cannot copy or move the file to another location.  The error is "Could not write to {destination folder}"

At the top level, if I right click the file then properties then change permissions for enclosed files, owner and group can r/w create/delete; others can only read and access.  I can't get anything else to "stick".

Is it folder permissions related maybe?  Any thoughts?

-Adam

---

### Post by TheFu on 2020-03-17
What type of network folder?   CIFS, NFS, something else?

In general, CIFS ignores any Unix permissions.
NFS doesn't allow uid (0) access, but does honor Unix permissions. The uid on the NFS server and client need to match, however.

---

### Post by cag1999 on 2020-03-18
My local machine running Ubuntu 18.04 is on an ext4 partition.

The folder I want to move it to is on a networked Western Digital MyCloudEX2.  I assume the access is via an SMB share (I'm just navigating to it through "Files" -> "+ Other Locations" -> "Windows Network" -> "WORKGROUP" -> "Fileserver" -> "Backup").

I just tested writing it to a USB drive and it worked (I could swear it failed in the past, but it could have been due to the permissions of the Recover Folder at that time).

Side note: I believe I should be able to directly mount the "Backup" folder using an NFS mount, but I've been deferring that problem to another day (each user has their own folder, some of which are password protected which I would need to address).  If getting that resolved would fix my initial file sharing problem, then I could change my request for help to be how to create an fstab mount for each logged in user.


-Adam

---

### Post by TheFu on 2020-03-18
CiFS is userid to server.  Each userid has credentials for their own server connection.

NFS is server to server.  1 mount shared by all users.  File permissions control access. Local or remote permissions are the same, except for local root, which has zero permissions on NFS mounted storage.

---

### Post by coffeecat on 2020-03-18
*Moved to **General Help** sub-forum.*

---

