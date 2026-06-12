---
title: "Locked Update - Somebody please help"
date: 2007-07-21
forum: General Help
---

### Post by jgordon510 on 2007-07-21
I'm getting the following error from apt-get dist-upgrade on a friend's computer:

E: Could not open lock file /var/cache/apt/archives/lock - open (13 Permission denied)
E: Unable to lock the download directory

His computer crashed at some point (I wasn't there) creating the file.  Update isn't actually running but that file tells update that an update process is already running "locking" it.

There are several solutions elsewhere, like running apt-get clean and autoclean.  I've tried everything.

The problem is that the file permissions on the lock file are screwed up.  It's owner is listed as -949616511 (yes, that's a negative user id).  

I can't get rid of it as root.  I can't change the permissions or owner as root.  In short, I can't think of any conceivable way to change or get rid of that stupid file.  I even tried creating a user with that user id, but got an error, presumably because I can't create a negative user id.

Someone must have a solution.  I've posted this now three times to the forums and not had a response.  As I said earlier, this is a friend's computer, whom I've converted to Ubuntu, but having a broken system in which he can't even install software isn't exactly the best situation.  

Please help me.  I'm totally desperate.

---

### Post by kevinlyfellow on 2007-07-21
Have you tried booting into a live cd and changing the permissions of the lock file?  BTW it should be owned by root (and belongs to the group root), and owner should have rw permissions and group should have read permission.
```
sudo chown root:root /var/cache/apt/archives/lock
sudo chmod 640 /var/cache/apt/archives/lock
```

Also, do an fsck if you haven't already done so.  From a live cd, it should be fairly easy.  Unmount the partition and then, depending on you partitions
```
sudo fsck -t ext3 /dev/hda1
```

If there are a lot of errors that you do need to fix, you can use fsck with some options to say yes always.

---

### Post by bapoumba on 2007-07-21
> **jgordon510 said:**
> 
E: Could not open lock file /var/cache/apt/archives/lock - open (13 Permission denied)
E: Unable to lock the download directory

I can't get rid of it as root. 
Did you try from the terminal or from the GUI ? Please try from the terminal with rm (see **man rm**). You'll have to run it with sudo. Be aware that a file deleted with rm is gone for ever (or at least it is very difficult to get it back, as rm does not put the file in the trash).
```
isabella@yeti:~ $ cd /var/cache/apt/archives
isabella@yeti:/var/cache/apt/archives $  ls lock*
lock
isabella@yeti:/var/cache/apt/archives $ sudo rm lock
[sudo] password for isabella:
isabella@yeti:/var/cache/apt/archives $ ls lock
ls: lock: No such file or directory
isabella@yeti:/var/cache/apt $ cd ~
isabella@yeti:~ $

```

The lock file can be removed, another one will be created when needed.

You also may have a "zombie" process running and locking the file.
Please try:
```
ps -aux | grep <insert_here_a_package_manager>
```
with apt-get, synaptic, aptitude or adept, depending on which package manager your friend has been using when the file got locked.

---

### Post by jgordon510 on 2007-07-21
**kevinlyfellow:**
I've looked at the file on other machines and they all have root ownership, but this one has that bizarre negative uid owner.  chown and chmod can't get permission through sudo or su.  I'll try it from a livecd and see if that changes the situation.

I did an fsck, but did so from a recovery terminal.  There were hundreds of errors and I fixed them, reran it, and it was happy.  That might be an area to explore though.  I don't have access to his computer, but I'll try it later this weekend with a few options. 

[B]
bapoumba:[/B]
Yes, I did it from terminal.

As far as zombie processes, I logged into recovery mode and ran top.  There weren't any processes that could be locking it up.  I'm fairly certain I've ruled that out.

---

