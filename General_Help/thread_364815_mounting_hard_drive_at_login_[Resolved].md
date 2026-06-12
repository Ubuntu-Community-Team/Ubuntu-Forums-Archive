---
title: "mounting hard drive at login [Resolved]"
date: 2007-02-18
forum: General Help
---

### Post by whobutdrew on 2007-02-18
I have a 2 hard drives in my computer, an 80GB (bootable) and a 250GB (data only).  It is broken up into two partitions, giving me /dev/hdb5 and /dev/hdb6.

I have two folders on my desktop which act as the mount points.  My /etc/fstab for these partitions read as follows:

/dev/hdb5   /home/drew/Desktop/Folder1   auto  user,rw,noauto
/dev/hdb6   /home/drew/Desktop/Folder2   auto  user,rw,noauto

I then added two mount commands (mount /dev/hdb5)(mount /dev/hdb6) into my startup items via System > Preferences > Sessions.

Hdb5 works with no problem.  Hdb6 will not mount at login.  If I go into the Terminal and issue the mount /dev/hdb6 command manually, it mounts with no problems.

I tried writing a script with the two mount commands in it and adding that script to the login items, and again, only the first partition mounted.  I even tried issuing a sleep command between the two mounts.  I even tried just mounting /dev/hdb6 by itself via startup items, and nothing.

I had this working fine in 6.06 (which reminds me, running Ubuntu Edgy).

What's going on??

---

### Post by Falcorian on 2007-02-18
Is there a reason you don't have automounting on? That's always worked for me... And if you have the read/write permissions set accordingly, I don't see how that'd be a problem.

Otherwise, I don't have anything helpful to add, sorry. :(

---

### Post by whobutdrew on 2007-02-18
> **Falcorian said:**
> Is there a reason you don't have automounting on? That's always worked for me... And if you have the read/write permissions set accordingly, I don't see how that'd be a problem.

Otherwise, I don't have anything helpful to add, sorry. :(

If I change 'noauto' to 'auto' in /etc/fstab, the partitions mount as read-only, as the user who issued the mount command was root.

I set both of these up the exact same way, one works, one doesn't.  Its bizarre.

---

### Post by taurus on 2007-02-18
What filesystem are those partitions?

---

### Post by whobutdrew on 2007-02-18
> **taurus said:**
> What filesystem are those partitions?

FAT32, each of them.

---

### Post by Falcorian on 2007-02-18
Well, I'm going to keep trying to force this problem down the automount path... ;) Since that's the only way I know how to get it to work.

With vfat, since it doesn't have permissions stored on disk (as far as I know) you need to add uid=0000,gid=0000, which tells Linux "Assume the drive is owned by user 0000 and group 0000".

Of course, you'll need to find your user ID number, it should be like 1000 or so.

You can ```
cat /etc/group | grep YOURUSERNAME
``` to find it. It's also under System > Admin > Users and groups, click your user name then click Properties and go to the Advanced Tab.

Then you'd set up fstab like:

```

/dev/hdb5 /home/drew/Desktop/Folder1 vfat rw,uid=YOURID,gid=YOURID
```


Of course, others may be able to fix it without the automounting... ;)

---

### Post by whobutdrew on 2007-02-18
> **Falcorian said:**
> Well, I'm going to keep trying to force this problem down the automount path... ;) Since that's the only way I know how to get it to work.

With vfat, since it doesn't have permissions stored on disk (as far as I know) you need to add uid=0000,gid=0000, which tells Linux "Assume the drive is owned by user 0000 and group 0000".

Of course, you'll need to find your user ID number, it should be like 1000 or so.

You can ```
cat /etc/group | grep YOURUSERNAME
``` to find it. It's also under System > Admin > Users and groups, click your user name then click Properties and go to the Advanced Tab.

Then you'd set up fstab like:

```

/dev/hdb5 /home/drew/Desktop/Folder1 vfat rw,uid=YOURID,gid=YOURID
```


Of course, others may be able to fix it without the automounting... ;)

Perfection!  This got it working and got me RW access that I have been going for.  Thanks for your help!!

---

### Post by Falcorian on 2007-02-19
> **whobutdrew said:**
> Perfection!  This got it working and got me RW access that I have been going for.  Thanks for your help!!

Glad I could help! Best of luck!

---

