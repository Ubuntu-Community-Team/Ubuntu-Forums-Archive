---
title: "Frustrating CVS Commit error"
date: 2008-01-03
forum: General Help
---

### Post by adamup on 2008-01-03
I have a CVS repository on a network drive at my office. I mount the drive locally and have read/write access. I am using CrossVC as the GUI front-end for CVS.

I can access the repository just fine; update and checkout work. However, when I try to commit a change to the repository I get the following error:

> cvs [commit aborted]: cannot change mode for /media/snapserver/CVSROOT/zfatlas/,index.html,: Operation not permitted

I can't for the life of me figure it out. Any ideas?

---

### Post by geirha on 2008-01-03
What permissions and ownership does that particular file have?

---

### Post by adamup on 2008-01-03
Owner is the local user and the permissions are rwxr-xr-x

---

### Post by geirha on 2008-01-03
Hm, what filesystem is the cvs repository on? If you create a dummy file on that same filesystem, then run chmod 777 or something on it, do you get a similar error?

---

### Post by adamup on 2008-01-04
geirha, thanks so much! You pointed me in the right direction. I found that I could only change the permissions on the remote file as root But I was running my cvs front-end without root privileges. Running cvs using sudo now solves the problem! Thanks!

---

### Post by aydin on 2008-02-27
I had the same problem and I fixed it by changing the mount options. Earlier, the remote filesystem (where cvs root resides) was mounted as root using sudo. Now, I added the options uid and gid to the mount command, and cvs commit worked fine as a regular user.

The mount command:
```
sudo mount.cifs //192.168.1.12/cvs /path/to/cvsroot -ocredentials=/path/to/.smbcredentials,uid=aydin,gid=aydin
```

---

