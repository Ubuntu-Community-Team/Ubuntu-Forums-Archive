---
title: "Error while trying to mount external Drive via NFS"
date: 2015-05-07
forum: General Help
---

### Post by blackbadger on 2015-05-07
I have 2 mc's both running 14.04. I want to get NFS running instead of samba to share files. 


  I've installed nfs server on mc1 and the client on mc2.


  Managed to share the 'home' folder on mc1 but, when trying to share  an external disk drive called 'Buffalo' on mc1, I get the following:


  user@machine2:~$ sudo mount 192.168.1.37:/Buffalo /mnt/nfs/Buffalo mount.nfs: access denied by server while mounting 192.168.1.37:/Buffalo


  I've created the necessary directory, called Buffalo,  on mc2.


  Here's the exports file on mc1:


  /home 192.168.1.0/24(rw,async,insecure,no_subtree_check,nohide) 
/media/user/Buffalo 192.168.1.0/24(rw,async,no_subtree_check,nohide)


  any ideas what I'm missing? Thanks

---

### Post by SeijiSensei on 2015-05-07
What are the ownerships and permissions on /media/user/Buffalo?  Is the device formatted with a Linux filesystem like ext4?  If the device has an NTFS-formatted drive, or worse, one formatted with FAT32, you may have problems since these filesystems have no equivalents for Unix permissions and ownerships.

What do you see in the server's /var/log/syslog when you try to mount the share?

---

### Post by blackbadger on 2015-05-07
File system shows as ext3/ext4

Permissions are:

Owner: Me (no idea who 'Me' is)
Access: Create and delete files

Group: mark (my user name on that machine)
Access: Create and delete files

others
Access: create and delete files

log on server shows nothing. log on machine which is trying to mount shows messages
which i cant seem to

---

### Post by SeijiSensei on 2015-05-07
> **blackbadger said:**
> log on server shows nothing.
There is no corresponding entry on the server to this client-side error?
```
user@machine2:~$ sudo mount 192.168.1.37:/Buffalo /mnt/nfs/Buffalo mount.nfs: access denied by server while mounting 192.168.1.37:/Buffalo
```

I find NFS works best when root owns the top-level directories and access to the NFS shares is controlled by ordinary Unix permissions.  So my NFS server has an entry for me in its /etc/passwd with UID 1000, and my client machines all have entries in their /etc/passwd files for me with the same UID.  I have a large ext4 filesystem on the server mounted by root with 777 permissions.  

```
$ ls -l /media
drwxrwxrwx   8 root root 4096 May  4 16:41 storage

```

The directories below the mount point have a variety of owners and more limited permissions.  The NFS mount point on the client is owned by root with 777 permissions as well. After the NFS share is mounted, the ownerships and permissions of the directories below the mount point are identical to those on the server.

You can do this with 775 or 755 permissions as well, I believe. Since I and my daughter are the only users, I don't really care much about security.

---

### Post by blackbadger on 2015-05-08
Sorry, had someproblems with pc last night and couldn't seem to post here.

only thing i could see in syslog  on client m/c is

RPC: AUTH GSS upcall failed. Please check user daemon is running

---

