---
title: "Mounting Windows Shares"
date: 2006-11-06
forum: General Help
---

### Post by jimmymac on 2006-11-06
Hi guys,

I'm having a wee problem with mounting my windows share.  The drive I'm sharing is actually formatted as ext3.
I've mounted it in fstab as smbfs.
But it only gives me read-only access.

Any ideas?

TIA

Jimmy

---

### Post by Najand on 2006-11-06
Add "rw" option to your /etc/fstab file.

---

### Post by jimmymac on 2006-11-06
so the line should look something like this:

//venus/music   /music          smbfs   auto,rw,user    0       0

??

TIA

Jimmy

---

### Post by Najand on 2006-11-06
It should work, if there is no password or user ID needed for it.

---

### Post by jimmymac on 2006-11-08
Ok, the line doesn't work!
If I map it through a windows machine with no password/user etc.  It maps fine, it's just mounting it through ubuntu that gives read-only access!

Any other ideas?

TIA

Jimmy

---

### Post by jimmymac on 2006-11-08
When I try to access the SMB share, I get the error message:

smbmnt must be installed suid root for direct user mounts (1000,1000)

smbmnt failed: 1

My understanding is that this means that only root can mount the drive?
Surely I must be wrong with this!!

MTIA

Jimmy

---

### Post by Najand on 2006-11-08
Ah Huh! Ok, now I'm understanding your problem. You should be able to solve the problem you are experiencing by changing smbmnt's permissions.
Hmm, a
```

sudo chmod +s /usr/bin/smbmnt

```
may help you. Please tell me your result. I hope it works; though,if it doesn't we will look for some other solution.

---

### Post by jimmymac on 2006-11-09
Ok tried that and now I get:

mount: only root can mount //venus/music on /music

what did I just do?  Obviously changed permissions on smbmnt but what does +s do?

TIA

Jimmy

---

### Post by taurus on 2006-11-09
Mount it with sudo...

---

### Post by jimmymac on 2006-11-09
I can mount it with sudo but it's still read-only....

---

### Post by Najand on 2006-11-09
If you are mounting it in in the following format:
```

sudo mount -t smbfs //samba-server/files /mnt/files/ -o rw,username=username,password=xxxx

```
and it is just Read-Only and changing /usr/bin/smbmnt is not helping you, then either the username and password only has read-only access, or you've got the wrong username and/or password and the server is mapping you to the guest account (which then has read only access.)

---

