---
title: "Copying data between machines on LAN"
date: 2014-03-26
forum: General Help
---

### Post by m-dw on 2014-03-26
I have a lot of data (well a fair amount but less than 1 TByte) to copy from a consumer NAS to a new home server (to be built on Ubuntu Server 14.04 LTS).  While I'm waiting for the server case to be delivered I've been doing some experimentation to see what the fastest way of copying the data is going to be using my workstation (Ubuntu 13.10) as the target.  NAS and workstation are on the same gigabit switch with jumbo frames enabled.

cp from an NFS share to a local disc got me the best speed (30MBytes/s) while not stressing the NAS in the slightest.
rsync (pulling to the workstation from a remote rsync daemon) performed significantly worse (approx 4MBytes/s) with the NAS working flat out.
tar over ssh also worked but was the slowest of the lot at about 1.5MBytes/s because of the encryption overhead.

Obviously I would prefer to use NFS to transfer the files because of the speed, but I need to preserve permissions on the files (and some of them aren't owned by my user account).

Would the following work on Ubuntu?
```

sudo mnt <remote_NFS_drive> /temporary_mount_point>
sudo su
cp -a /temporary_mount_point/* /directory_to_be_shared

```

Or will that lead to potential problems?

---

### Post by TheFu on 2014-03-26
If you need to maintain permissions, then the same users and groups need to exist on the new server, period.  You'll want to run the copy/rsync as root - other userids cannot maintain permissions.  **cp -rp source target**.  The cp command isn't smart about special files - links. That's where rsync and tar are better used.  I don't know of any copy solution that handled hardlinked files correctly - for those something like **fsarchive** or **dd** is needed.

Also - rsync uses ssh by default, unless you disable it.  NFS will be faster than rsync, unless many of the file files are already on the new storage and rsync recognizes it.

So - I would use NFS with cp -rp for the first copy, then use rsync for the remaining to pick up and changed files since the prior copies/rsync's.

Why do people use **sudo su**?

* Use **sudo -s** - if you want to retain YOUR environment. Nicer for running a few CLI programs based off YOUR real userid HOME. Avoid GUIs to prevent root-owned files in your HOME.
* Use **sudo -i** - if you want to get a fresh "root" environment. Better if a GUI program is used, so ~root/ will get the saved settings.

The sudo design guys are really, really smart.
Am I missing something?

---

### Post by m-dw on 2014-03-26
> **TheFu said:**
> 

Why do people use **sudo su**?

* Use **sudo -s** - if you want to retain YOUR environment. Nicer for running a few CLI programs based off YOUR real userid HOME. Avoid GUIs to prevent root-owned files in your HOME.
* Use **sudo -i** - if you want to get a fresh "root" environment. Better if a GUI program is used, so ~root/ will get the saved settings.

The sudo design guys are really, really smart.
Am I missing something?

1)  Thanks for the advice.  I think cp -a is about the same as cp -rp.  Most of my stuff is owned by me:me or me:users, and as far as I can tell I have no links between files on the NAS.  I've recently gone through an exercise of tidying up my home directory (about 2 years after migrating from openSuSE 11, and there were a few user/group oddities now fixed.  I'll just need to make sure I have the same UIDs and GIDs on the server.  I'll be the only user initially so not too much complexity really.

2)  Was getting cp confused with cd  :confused:.  Yes don't need sudo for cp, but you do to change to a directory owned by root.  My bad.

---

### Post by thedork012 on 2014-03-26
> **m-dw said:**
> 1)  Thanks for the advice.  I think cp -a is about the same as cp -rp.  Most of my stuff is owned by me:me or me:users, and as far as I can tell I have no links between files on the NAS.  I've recently gone through an exercise of tidying up my home directory (about 2 years after migrating from openSuSE 11, and there were a few user/group oddities now fixed.  I'll just need to make sure I have the same UIDs and GIDs on the server.  I'll be the only user initially so not too much complexity really.

2)  Was getting cp confused with cd  :confused:.  Yes don't need sudo for cp, but you do to change to a directory owned by root.  My bad.

That actually depends on the permissions of said directory.  To cd into a directory you must have execute permission.

Say you have two directories:
 ```
drwxr-xr-- 2 root root dir1
drwxr-x--x 2 root root dir2
```
Users who are not root cannot cd into dir1, but they can list its contents (ls /path/to/dir1).
Users who are not root can cd into dir2, but they cannot list its contents.

---

### Post by TheFu on 2014-03-26
You DO need sudo for cp to retain permissions for other users/grps.

I've read the man pg for cp - I don't think **cp -a** and **cp -rp** are the same. There are differences.
root owning a directory doesn't necessarily mean other users cannot cd into it.  Directory and file permissions are a critical aspect of UNIX security - best to review these.

---

### Post by m-dw on 2014-03-27
> **TheFu said:**
> You DO need sudo for cp to retain permissions for other users/grps.


Sorry, yes I meant to write:
"You need sudo **su** to ender a directory to which you don't have permissions" because:

```
david@linux:~$ sudo cd /root[sudo] password for david: 
sudo: cd: command not found

```

You **don't** need sudo su for the copy command (which ever one)

I said "about the same"

From the man page:
-a, --archive
	      same as -dR --preserve=all


-R, -r, --recursive
	      copy directories recursively


-d     same as --no-dereference --preserve=link


-p     same as --preserve=mode,ownership,timestamps
So the only difference is that cp -rp doesn't dereference links.

---

### Post by TheFu on 2014-03-27
And I wouldn't want links to be deref'd - there are other attributes too. context, links, xattr that I don't want.

Also the **cd: command not found** thing is because cd is built-in to the shell, it is not a command to be called. Also - after running a cd with sudo, the program returns and goes back the the original CWD. Nothing to see, even if it were a command in the path. The permissions on the specific directories and files matter for how other users can access them.

So ... I would still use **sudo cp -rp**.

---

### Post by m-dw on 2014-03-27
And I will take your advice, thank you.

---

