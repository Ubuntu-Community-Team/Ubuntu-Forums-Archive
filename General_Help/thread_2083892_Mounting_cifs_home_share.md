---
title: "Mounting cifs home share"
date: 2012-11-13
forum: General Help
---

### Post by netsense on 2012-11-13
G'day all,

I'm trying to mount a couple of shares on our CentOS server into the filesystem of a Ubuntu desktop and a Linux Mint laptop (they all mount fine into XP, Vista & Win7), and getting exactly the same issue.

The fstab line for the mounts is the same for each: 
//IP address/sharename     /mnt/mountdir  cifs   username=username,password-password,_netdev,rw    0 0

The general shares mount Ok; however, regardless of what I try to  do, the home share on the server mounts onto the laptop, but can only  be accessed as superuser. I have tried playing with uid & gid, rw, file_mode & dir_mode, guest, nounix, iocharset parameters for the mount; and the results are all the same. One of the issues I see is that when mounted, the directories are owned by user 500 (from the CentOS system, but has the same username and password on all machines); of course, the sameuser on the Ubuntu & Linux Mint boxes has a uid of 1000. Despite this, the server's non-home shares mount OK. The mount points all have the same owner and permissions.

I suppose I could do it through nfs, but I should be able to do it using the servers samba shares.

Can anyone help?

---

### Post by bab1 on 2012-11-13
> **netsense said:**
> G'day all,

I'm trying to mount a couple of shares on our CentOS server into the filesystem of a Ubuntu desktop and a Linux Mint laptop (they all mount fine into XP, Vista & Win7), and getting exactly the same issue.

The fstab line for the mounts is the same for each: 
//IP address/sharename     /mnt/mountdir  cifs   username=username,password-password,_netdev,rw    0 0

The general shares mount Ok; however, regardless of what I try to  do, the home share on the server mounts onto the laptop, but can only  be accessed as superuser. I have tried playing with uid & gid, rw, file_mode & dir_mode, guest, nounix, iocharset parameters for the mount; and the results are all the same. One of the issues I see is that when mounted, the directories are owned by user 500 (from the CentOS system, but has the same username and password on all machines); of course, the sameuser on the Ubuntu & Linux Mint boxes has a uid of 1000. Despite this, the server's non-home shares mount OK. The mount points all have the same owner and permissions.

I suppose I could do it through nfs, but I should be able to do it using the servers samba shares.
Can anyone help?

Usually this is caused by incorrect user permissions or incorect [homes] share settings.  What does the [homes] share configuration look like?  What are the permissions of the server directory that holds the [homes] share?

---

### Post by netsense on 2012-11-14
Bab1,

Thank you for the tip - I checked the permissions on the user directory, and found it to be 0700, unlike the other users; don't know how it got that way, but changed it to 0755 and hey presto, everything works!

Thank you (although I should have thought of it myself!).

---

