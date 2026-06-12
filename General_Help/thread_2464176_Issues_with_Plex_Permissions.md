---
title: "Issues with Plex Permissions"
date: 2021-06-26
forum: General Help
---

### Post by bigun892 on 2021-06-26
I'm guessing this is a permissions issue.

I have a VM with Ubuntu installed.  Two drives, one for OS, one for data.

Data is where the video lives, and has 'ext4' filesystem on it.

I've created a mountpoint for the drive '/mnt/external', and the fstab entry for the drive is as follows:

```
/dev/sdb1       /mnt/external   ext4    defaults,auto,rw,nofail 0 0
```

Drive mounts fine, I have the permissions of the libraries in question set to:

```
drwxrwxr--   3 bigun users
```

I have the plex user in the 'users' group:

```
bigun@mediaserver:~$ groups plex
plex : plex video users render
```

So I add the library to Plex, and it sees the library as empty.   Typically a sign of a permissions issue.

To troubleshoot, I've set the owner and group to plex:plex, and set permissions to 777, same error.

Any help is appreciated.

---

### Post by deadflowr on 2021-06-26
Duplicate thread 
See other thread here: [https://ubuntuforums.org/showthread.php?t=2464174]("https://ubuntuforums.org/showthread.php?t=2464174")
closed

---

