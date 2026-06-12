---
title: "Problem with read-only backup"
date: 2013-05-14
forum: General Help
---

### Post by dan08 on 2013-05-14
I am trying to put together a bash script to backup a few NFS shares. I am still working through this and have been learning bash as I go. The shares are mounted as read-only. The script uses rsync to copy files from the NFS device to a Drobo mounted over iSCSI. I ran a test backup and it didn't really work, but now I can't get rid of the backup files because they are read-only. I have tried changing the permissions, but when i try:```
 rm -rf <directory>
```, I get a long print out of each file like: ```
cannot remove <file> read-only filesystem
```. Right now I just want to delete these backups, later I will worry about reworking my script. Does anyone have any advice?

---

### Post by arsenic23 on 2013-05-14
```
sudo rm -rf <directory>
```

---

### Post by dan08 on 2013-05-14
I did use sudo, I accidentally left that out in the post. But I actually figured out where the problem is. I had mounted the Drobo as read only, and therefore could not edit anything I put onto it. Thanks anyway.

---

### Post by dan08 on 2013-05-14
Hey I'm new to this forum. How do I mark this as solved? I don't want to waste anyone's time with my stupid mistake.

---

### Post by BlinkinCat on 2013-05-14
> **dan08 said:**
> Hey I'm new to this forum. How do I mark this as solved? I don't want to waste anyone's time with my stupid mistake.

Hi,

You mark as solved in your first post, as in -

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Cheers - :)

---

### Post by dan08 on 2013-05-14
Cool Thanks

---

