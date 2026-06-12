---
title: "cannot write on a disk"
date: 2021-12-09
forum: General Help
---

### Post by fabio61 on 2021-12-09
Anybody can help me with something I never faced?

Suddenly, while I was working as usual on my system, without having done any change, I can no longer write on one of the HDs: I receive the message that the disk is write protected.

Actually, the folder on that disk, on the "File" application, have a little lock on. However, if I check the permissions, I have the impression that everything is ok:

```
ls /home/fabio
drwxrwx---   1 root plugdev       4096 nov 12 16:11 data-storage
```

data-storage is the HD
I also checked to be in the plugdev group:

```
id fabio
uid=1000(fabio) gid=1000(fabio) gruppi=1000(fabio),4(adm),7(lp),24(cdrom),27(sudo),30(dip),46(plugdev),120(lpadmin),131(lxd),132(sambashare)
```

I am puzzled

---

### Post by ajgreeny on 2021-12-09
```
ls /home/fabio
drwxrwx---   1 [COLOR="#FF0000"]root plugdev[/COLOR]       4096 nov 12 16:11 data-storage
```
The problem is shown in red in my quote from your post; the folder is owned by the user **root** and the group **plugdev** but for you to be able to write to it should be owned by you as user, and by your group, which is the normal and required permissions for your /home folder or partition.

I also see that this appears to be your /home folder or partition; do you have any problems logging in to your system as user fabio?
You may be a member of the **plugdev** group but you are most definitely not user **root**

Have you done anything that could possibly have changed the permissions of that mountpoint to the way it is showing?

---

### Post by KBar on 2021-12-09
ajgreeny, correct me if I'm wrong, but shouldn't that also mean they won't be able to access their home directory as long as that device is mounted inside their home directory?

---

### Post by ajgreeny on 2021-12-09
Yes, absolutely correct!
Hence my query about whether or not it was possible for fabio to login as user on the machine.

There is obviously something very strange going on here which I do not understand and we need a great deal more information before we can figure out what is wrong.

For a user folder in /home to be owned by root is as you say, very, very wrong; I just want to figure out how or why it happened while he was apparently working as usual on the system.
Mountpoints of external disk partitions do not change without some action by a user or potentially (maybe?) a hardware problem of some kind, though I have no idea what that could be.

---

### Post by fabio61 on 2021-12-09
> **ajgreeny said:**
> ```
ls /home/fabio
drwxrwx---   1 [COLOR="#FF0000"]root plugdev[/COLOR]       4096 nov 12 16:11 data-storage
```
The problem is shown in red in my quote from your post; the folder is owned by the user **root** and the group **plugdev** but for you to be able to write to it should be owned by you as user, and by your group, which is the normal and required permissions for your /home folder or partition.

I am sorry for my mistake: I wrongly wrote "/home/data-storage" but it is actually "/data-storage"

The disk "data-storage" is a mechanical HD, that includes several folders; those folders are actually listed with me as owner and group:

```
lrwxrwxrwx  1 fabio fabio        23 feb  5  2021  Documenti -> /data-storage/Documenti

```

they are links to the folder in the "data-storage"

All the root directories have "root" as owner (including "data-storage", and all the /home directories have "fabio" as owner.

Should I chown "data-storage"?

> Have you done anything that could possibly have changed the permissions of that mountpoint to the way it is showing?

I have not done anything. I downloaded a .pdf file from Dropbox, while working and I realized the problem.

One odd thing  happened a bit earlier: by mistake, I booted the system holding the Esc key: I went into >grub, then I wrote >exit and windows started. Could it have been the problem?

Please also note:

```
mount | grep data-storage
/dev/sda2 on /data-storage type fuseblk (ro,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096)

```

so it is mounted read-only. It will be enough to chown it or should I remount it?

The disk is formatted NTFS and it is shared with windows: it is possible that that anomalous reboot freezed in read-only mode

---

### Post by ajgreeny on 2021-12-09
OK, thanks for that information which helps diagnose your problem a little more but I am still utterly confused.

If your data-storage disk is an internal disk the easiest way to make it available to you as **fabio** is firstly to mount it automatically at boot with an entry in /etc/fstab [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) and once that is done recursively change ownership of the mountpoint, (which you will have to create first with ***sudo mkdir /data-storage***), to fabio with command ```
sudo chown -R fabio:fabio /data-storage
```
You can then create symbolic links to the main folders in that disk back to your /home folder in the OS, similarly to the way in which I link my /home folders in Xubuntu 20.04 to a new test installation of the development version, Xubuntu 22.04.

I hope that helps but if you are still confused, which I am a little, come back with more questions and as much information as you can; if I am not able to help I'm sure others will be around who can.

---

### Post by fabio61 on 2021-12-09
Actually, you did clarify a lot:

> **ajgreeny said:**
> OK, thanks for that information which helps diagnose your problem a little more but I am still utterly confused.

If your data-storage disk is an internal disk the easiest way to make it available to you as **fabio** is firstly to mount it automatically at boot with an entry in /etc/fstab 

That is exactly how it was supposed to be, and it was. When I installed the system I mounted it as /data-storage, then I simply created symbolic links to the main folders, as you suggested.

The point, here, is that most likely when I erroneously started the grub prompt, and then "exit" it, for some reason a windows process started and must have changed something making it read-only.

My doubt, now, is the following: on a read-only folder (now owned by root) could I simply change the owner with 
```
sudo chown -R fabio:fabio /data_storage
```

or is it necessary to remount the disk?

As a matter of fact the chown is ineffective because the file system is read-only (I tried)

---

### Post by fabio61 on 2021-12-09
Actually, I think to have solved the problem.
When I erroneously got exited the grub prompt and windows started I simply shut-off the computer; of course Windows did not like the move and freezed the disk into read-only mode.
It was enough starting Windows again and allow it to close correctly: everything went back to normal!!!

---

### Post by ajgreeny on 2021-12-09
Brilliant!
I know very little about Windows now not really having used it since XP, but I'm aware that dual boots with it and Linux can cause all sorts of problems particularly when Windows carries out major updates to the OS or, I believe, if it crashes.  This problem seems to be a one that I've never heard of before.

Thanks also for marking as **SOLVED**.

---

