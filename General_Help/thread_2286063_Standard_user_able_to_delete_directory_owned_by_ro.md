---
title: "Standard user able to delete directory owned by root user and root group"
date: 2015-07-09
forum: General Help
---

### Post by peter1897 on 2015-07-09
I have one user with admin rights mark, and one user without admin rights bob. If i am logged in as mark and create directory docs in /home/bob/ the directory is owned by user root and group root. But if i login as bob and try to delete the directory with the command rm -r docs i just get a message: **rm: remove write-protected directory `/home/bob/docs/'?**
And if i type yes it deletes the directory. Why the standard user is able to delete the directory when it is owned by root user and group user?

Also, why when i am login as mark and create a directory in /home/mark the user owner and group owner are assigned to mark automatically. But when i create directory outside mark home directory the default user and group that are assigned to it are root user and root group?

---

### Post by Vladlenin5000 on 2015-07-09
Anything under /home/user is owned by user.

---

### Post by bab1 on 2015-07-09
> **peter1897 said:**
> I have one user with admin rights mark, and one user without admin rights bob. If i am logged in as mark and create directory docs in /home/bob/ the directory is owned by user root and group root. But if i login as bob and try to delete the directory with the command rm -r docs i just get a message: **rm: remove write-protected directory `/home/bob/docs/'?**
And if i type yes it deletes the directory. Why the standard user is able to delete the directory when it is owned by root user and group user?

The directory above is what gives the user the right to delete it.
> 

Also, why when i am login as mark and create a directory in /home/mark the user owner and group owner are assigned to mark automatically. But when i create directory outside mark home directory the default user and group that are assigned to it are root user and root group?
If you are using sudo then the ownership is root as you are root for that operation.

---

### Post by peter1897 on 2015-07-10
> **bab1 said:**
> The directory above is what gives the user the right to delete it.

You mean since the above directory /home/bob is owned by user bob and group bob that gives the permission to the standard user bob to delete the docs directory even if it is owned by user root and group root?

---

### Post by bab1 on 2015-07-10
> **peter1897 said:**
> You mean since the above directory /home/bob is owned by user bob and group bob that gives the permission to the standard user bob to delete the docs directory even if it is owned by user root and group root?
Yes I do.  The permissions for the user of the directory are read and write to that directory.  This means the user can read, write and therefore modify and delete a file or subdirectory.  The file or subdirectory ownership is not really the point.  Ownership is really just who created the file or directory along with that users permissions.  Ownership by itself does not give the user and specific permissions.

It's worth while noting that there are only 3 types of users on an Ubuntu host.  They are```

root user = uid 0
system users = uid 1 to 999
mortal users = 1000 to 65535

```The user *nobody* is always uid=65536 and is also a system user.  The root user of course has the ability to do anything with the system.  The other users do not have root powers at all.  The system user *does not* have interactive shell access or a home directory.  The mortal user has an interactive shell and a home directory.  Both the user bob and mark are mortal users.  The only difference is that the user mark has sudo access.  The sudo command allows a mortal user to switch to the root user on a per command basis or for a specific time ( i.e. **S**witch **U**ser and **Do**).  Sudo ultimately calls the command **su** (switch user), which when called with no argument defaults to the user *root*.  You can switch to other users too.  You can do this (as the user mark)```
su bob
```...if mark knows bobs password then mark will switch shells to the user bob.  Type exit to return to the original user.

No user other than root has root powers and root is always uid=0.  All other users can have differing UID's.

Linux users are not secured like Windows users.  There really is no "Admin User" in Linux.

---

### Post by papibe on 2015-07-10
> **peter1897 said:**
> You mean since the above directory /home/bob is owned by user bob and group bob that gives the permission to the standard user bob to delete the docs directory even if it is owned by user root and group root?
Yes.

This is a simple example:
```
$ ls -la
total 8
drwxr-xr-x 2 user user 4096 Jul 10 04:04 .
drwxrwxr-x 3 user user 4096 Jul  9 20:36 ..

$ sudo touch file

$ ls -la
total 8
drwxr-xr-x 2 user user 4096 Jul 10 04:05 .
drwxrwxr-x 3 user user 4096 Jul  9 20:36 ..
-rw-r--r-- 1 root  root     0 Jul 10 04:05 file

$ rm file 
rm: remove write-protected regular empty file ‘file’? y

$ ls -la
total 8
drwxr-xr-x 2 user user 4096 Jul 10 04:06 .
drwxrwxr-x 3 user user 4096 Jul  9 20:36 ..
```

---

### Post by peter1897 on 2015-07-10
Thanks! Useful information.

---

### Post by Skaperen on 2015-07-10
what is happening is that a link in /home/bob named "docs" is being removed.  it is the permissions of /home/bob that apply.  the reference count for /home/bob/docs is decremented ... when it reaches zero then it goes away.  for directories the decrement to zero is allowed only if that directory itself has no references _in_ it. * for many reasons a directory is only allowed to have just one link _to_ it although a regular file may have many* (limited by the system implementation ... generally at least close to 65535).  these are called "hardlinks".

*extra reading*:

[http://fsl.fmrib.ox.ac.uk/fslcourse/unix_intro/fstour.html](http://fsl.fmrib.ox.ac.uk/fslcourse/unix_intro/fstour.html)

---

