---
title: "Problems with folder and file permission"
date: 2015-07-12
forum: General Help
---

### Post by gundybandy on 2015-07-12
Hi,
I would like to have a folder where all users of a group can read, write, execute, delete, change, create all subfolders and subfiles and they should be able to copy files and folders from their home to this folder while the other users of the group can also can read, write, execute, delete and change them.

At the moment I have a group:
sharedudes

Members of the groups are:
sharerone, sharertwo, sharerthree

The folder which should be share is named:
shared

How can I achieve this? I am using Ubuntu 14.04. Thank you very much!

---

### Post by dino99 on 2015-07-12
[http://askubuntu.com/questions/488485/allowing-a-group-read-write-access-to-a-directory](http://askubuntu.com/questions/488485/allowing-a-group-read-write-access-to-a-directory)

---

### Post by gundybandy on 2015-07-12
Hi,
I allready did that. 

I still have the problem that user A cannot delete, change folders and files of user B when user B copied folders from his /home folder to the shared folder.

EDIT:
I think I have manged it with umask.

---

### Post by bab1 on 2015-07-12
> **gundybandy said:**
> Hi,
I allready did that. 

I still have the problem that user A cannot delete, change folders and files of user B when user B copied folders from his /home folder to the shared folder.
This is because you need to force group inheritance on The top directory that you want a common group.  This is done by using the SGID bit. As you see, by default all files and directories are created with ownership of *user:usersgroup*.  You want this to be *[ user:B]sharedudes[/B]*.

Here is the information on the SGID bit: [http://www.zzee.com/solutions/unix-permissions.shtml#setuid]("http://www.zzee.com/solutions/unix-permissions.shtml#setuid")

---

