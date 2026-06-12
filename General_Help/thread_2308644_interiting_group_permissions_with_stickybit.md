---
title: "interiting group permissions with stickybit"
date: 2016-01-04
forum: General Help
---

### Post by NotQuiteSU on 2016-01-04
Running Ubuntu Server 14 LTS, I created a folder called media

> 
drwxrwsr-x 4 root htpc  4096 Jan  4 19:52 media/


My understanding is that with the stickybit (granted write and stickybit)
```

sudo chmod g+ws media/

```
all subsequent subfolders would have the same group as the parent folder.

> 
:/media/disk1/media/movies$ ll
total 12
drwxrwsr-x 3 htpc htpc 4096 Jan  4 20:23 ./
drwxrwsr-x 4 root htpc 4096 Jan  4 19:52 ../
drwxr-sr-x 2 bob  htpc 4096 Jan  4 20:23 test/


The test folder didn't inherit the write access.

---

### Post by bab1 on 2016-01-05
> **NotQuiteSU said:**
> Running Ubuntu Server 14 LTS, I created a folder called media
```
drwxrwsr-x 4 root htpc 4096 Jan 4 19:52 media/ 
```

My understanding is that with the stickybit (granted write and stickybit)
```

sudo chmod g+ws media/

```
all subsequent subfolders would have the same group as the parent folder.
```
drwxrwsr-x 3 htpc htpc 4096 Jan 4 20:23 ./
drwxrwsr-x 4 root htpc 4096 Jan 4 19:52 ../
drwxr-sr-x 2 bob htpc 4096 Jan 4 20:23 test/ 
```

The bit you are referring to is not the *sticky bit*.  It is the sgid bit.  See [**here**]("https://en.wikipedia.org/wiki/File_system_permissions#Changing_permission_behavior_with_setuid.2C_setgid.2C_and_sticky_bits") for the difference between the *sticky* bit and the **sgid** and **suid** bits.  When you set the *sgid* bit on a directory, all the subsequent directory and file _creation_ below that directory is done with the group ID set with that *sgid* bit.
> 
The test folder didn't inherit the write access.
The sgid bit does not address the permissions on any directories or files that are created.  The write ability is a permission.  The permissions are controlled by *umask*  The default umask is a filter that acts on the created directory and file permissions.  The created permissions for the directory/files (D/F) on a Ubuntu system is 777/666.  he umask sets the default working permissions for the D/F.  For the regular user this would be 775/664 (rwxrwxr-x / rw-rw-r--).  The umask is 002.  If you subtract the umask from the created permissions (777 -002 /666 -002) you get the default.  

The root user's default permissions are a little different.  The umask is 022.  The result is the created D/F permissions (777/666) end up with these defaults 755/644 (rwxr-xr-x/rw-r--r--).

Looking at the permissions of your directory *test*, my guess is you made it as root (sudo).  The permissions look correct for that scenario.  What is the umask setting?  Post the output of this (as a regular user)```
umask
```

---

### Post by NotQuiteSU on 2016-01-05
You are correct. I did make that as root, and changed the group. I believe everything is working correctly, except the only thing I found is that when a folder is created via SMB share (eg - from a windows PC), it doesn't inherit the group write permission. Is there a way to fix that?

---

### Post by HermanAB on 2016-01-05
You got to edit smb.conf and add the masks in there.

---

### Post by bab1 on 2016-01-05
> **NotQuiteSU said:**
> You are correct. I did make that as root, and changed the group. I believe everything is working correctly, except the only thing I found is that when a folder is created via SMB share (eg - from a windows PC), it doesn't inherit the group write permission. Is there a way to fix that?
Ownership is inherited.  Permissions are not.  As @HermanAB indicated, you should set the Samba umask in the share  configuration using ```
   create mask = 0664
   directory mask = 0775
```

---

