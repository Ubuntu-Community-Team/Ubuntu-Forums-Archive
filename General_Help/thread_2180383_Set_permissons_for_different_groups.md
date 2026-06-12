---
title: "Set permissons for different groups"
date: 2013-10-12
forum: General Help
---

### Post by BStrizzy on 2013-10-12
Hey guys,

I am trying to set up a simple file server and so far I have the following:

3 accounts: myaccount guestaccount storageaccount

right now I have all of the directories/files that I would like to share in the storage account. I have created softlinks from the storage account to my account and the guest account. I did it this way because I did not want to have all of the files in my account and have the users connecting thru my home directory to access the files so I placed them all in a storageaccount. 

Now I would like to set certain permissions so that the group that the userguest is in can only read and execute and for me obviously to have rwx. my main question is would I have to set the permission on the softlink or the actual directory that the softlink is pointing to and what is the syntax on adding permissions to certain groups and not just groups in general

Thanks guys!

---

### Post by bab1 on 2013-10-12
> **BStrizzy said:**
> Hey guys,

I am trying to set up a simple file server and so far I have the following:

3 accounts: myaccount guestaccount storageaccount

right now I have all of the directories/files that I would like to share in the storage account. I have created softlinks from the storage account to my account and the guest account. I did it this way because I did not want to have all of the files in my account and have the users connecting thru my home directory to access the files so I placed them all in a storageaccount. 

Now I would like to set certain permissions so that the group that the userguest is in can only read and execute and for me obviously to have rwx. my main question is would I have to set the permission on the softlink or the actual directory that the softlink is pointing to and what is the syntax on adding permissions to certain groups and not just groups in general

Thanks guys!

You are making this more complicated than need be.  You don't set permissions on soft-links.  The proper way is to have a shard folder that is not in any users /home directory.  This would be something like /data or /srv/data or /srv/share.  At this point you can place all the users in a common group and set the user/group ownership of the folder you are sharing.  At that point you will could have uesr=rw, group=rw,others=ro.  Which is just what you wanted in the first place.  In other words, don't share users directories.  Common data has a place somewhere else in the fi

How are you sharing the data to remote users (as the file server)?   The users on the other machines need to mount the share via some protocol (usually SMB or NFS).

---

### Post by BStrizzy on 2013-10-15
Thanks for the advice I def see what you are saying about placing it in a folder that does not reside in the /home directory. for future references tho, can you please describe me correct syntax for creating permissions to individual groups and not just groups in general?

Also, I have not mounted the folder nor do I intend to mount it for the people connecting. Security wise.. However, if I do decide to add one it will be via nfs or smb.

---

### Post by gleedadswell on 2013-10-15
I may be misinterpreting your intent.  But I think all you need to do is add the users to the group that will have ownership of this directory.  Then set the permissions for the folder using chmod.  If you don't know chmod, rather than me going on and on about it here, there are lots of tutorials on it.  Here's a link to one:

[http://www.linux.org/threads/file-permissions-chmod.4094/](http://www.linux.org/threads/file-permissions-chmod.4094/)

Cheers!

---

### Post by bab1 on 2013-10-16
> **BStrizzy said:**
> Thanks for the advice I def see what you are saying about placing it in a folder that does not reside in the /home directory. for future references tho, can you please describe me correct syntax for creating permissions to individual groups and not just groups in general?

Also, I have not mounted the folder nor do I intend to mount it for the people connecting. Security wise.. However, if I do decide to add one it will be via nfs or smb.

Building on @gleedadswell's comments: Linux provides for only 1 owner and 1 group owner per file or directory object.  Linux is not Windows.  Window style Access Control Lists are not built in to the the system.  You can effectively manage using owner : group : others ownership and setting the permissions correctly.

First you change the ownership of the root directory of the file system you wish to share (i.e. /data)```

sudo chown root:users /data
```...The directory now looks like this```
drwxrwxr-x 2 root users 4096 Jul 25 13:55 /data
```...the permissions on the directory at this time are 0775.

Everything below /data needs to inherit the group ownership (e.g. *users*).  You do that by set group ID bit (sgid).  This is done using the extended permissions.  See [[COLOR="#0000FF"]**_here_**[/COLOR]]("http://www.zzee.com/solutions/unix-permissions.shtml#setuid") for info.  You set the sgid bit using chmod```

sudo chmod [COLOR="#FF0000"]**2**[/COLOR]775 /data

```...now the listing looks like this ```

drwxrw[COLOR="#FF0000"]**s**[/COLOR]r-x 2 root users 4096 Jul 25 13:55 /data

```...The red is the sgid bit and it provides the inheritance you need in a shared user environment.  All directories and files below /data will now have the user group *users* upon creation.

If you already have data in the directory /data you will need to set the ownership and permissions below /data to  Ownership is done with this ```
sudo chgrp -R users /data/*
```...you should set the permissions like this```
chmod -R u=rwX,g=rwX,o=rX /data/*
```...this sets the permissions to 2775 on all the directories below /data (i.e. /data/<some_dir>).  It will also set the permissions on all files to 0664 which is what you want (rw for user and group and ro for others).

If you want to have exceptions to this it will get messy, but it can be done.  There are Linux ACL's that will allow you to add multiple user or groups.  I find I don't need ACL's but they are available.  If you user them make it an exception and document what you do for later when you have forgotten what you did.  ;-)

A summary of all of this can be found [**[COLOR="#0000FF"]_here_[/COLOR]**]("http://blog.jgriffiths.org/?p=126").

---

### Post by BStrizzy on 2013-10-24
exactly the tutorial I was looking for. thanks alot. is there anyway you can tell me how I can change permissions on a device that was mounted externally? for some reason I go to the directory I actually mounted it to and changed the permission such as 
> 
sudo chmod 755 crypt 

and when I run that i get 

> drwxrwxrwx 1 root root     0 2013-07-24 19:21 downloads
drwxrwxrwx 1 root root     0 2013-02-16 17:33 yehaw
drwxrwxrwx 1 root root     0 2013-10-21 23:49 happy
drwxrwxrwx 1 root root     0 2013-02-20 14:44 things
drwxrwxrwx 1 root root     0 2013-10-23 20:38 hi
drwxrwxrwx 1 root root 20480 2013-10-23 20:28 man
drwxrwxrwx 1 root root  4096 2013-04-29 19:34 school
drwxrwxrwx 1 root root  4096 2012-05-14 17:40 WD


 ^ those are all directories

I would only like me the owner and possibly a few other to be able to write to these directories.

any suggestions?

---

### Post by bab1 on 2013-10-24
> **BStrizzy said:**
> exactly the tutorial I was looking for. thanks alot. is there anyway you can tell me how I can change permissions on a device that was mounted externally? for some reason I go to the directory I actually mounted it to and changed the permission such as 
 

and when I run that i get 


 ^ those are all directories

I would only like me the owner and possibly a few other to be able to write to these directories.

any suggestions?

Is this a USB connected HDD or a flash drive?  How did you mount the device?

---

### Post by BStrizzy on 2013-10-25
yup this is a usb HDD connected via 

> sudo mount -t ntfs /dev/sdc1 crypt

---

### Post by bab1 on 2013-10-25
> **BStrizzy said:**
> yup this is a usb HDD connected via```
sudo mount -t ntfs /dev/sdc1 crypt
```

You can't change the ownership or permissions at the CLI after the file system is mounted.  The basic reason you can't change the permissions is because NTFS file systems carries no method of assigning permissions at all.  The permissions are set at mount time via the ntfs-3g driver.  Since you mounted the partition as root (using sudo) and did not explicitly set a user or group owner or their permissions the default was used.

Why are you mounting this via a CLI mount command anyway?  If you absolutely need to mount it this way you should mount it correctly.  Something similar to this  ```

sudo mount -t ntfs UUID /path/to/mount/point o- uid=nnnn,gid=nnnn,dmask=007,fmask=006

```...see ```
man mount.ntfs

man mount
```
You set the owner and permissions in the above statement.

OTH, it you just plug it in or boot with it in, the partition should just auto mount with you as the owner.

---

### Post by BStrizzy on 2013-10-31
Exactly what I needed. Thanks BAB1. Sorry for the late reply!! thread closed =)

---

