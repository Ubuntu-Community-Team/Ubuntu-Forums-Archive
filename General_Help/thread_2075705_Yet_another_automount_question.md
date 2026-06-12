---
title: "Yet another automount question"
date: 2012-10-24
forum: General Help
---

### Post by bomski on 2012-10-24
I have a large (6TB+) software array; and i've managed to get it to automount using the following in /etc/fstab:

```
/dev/md127 /media/RAIDArray/ ext4 defaults 0 0
```

all gravy so far; login as administrator and boom; RAID array mounted... 

Now i'm looking to restrict access to this as read-only from a standard  user; I created a noddy user (default permissions via user accounts  control panel). When logging into the system as the standard user; the RAID array is unmounted... 

I tried to resolve this by adding some switches to the fstab entry:

```
/dev/md127 /media/RAIDArray/ ext4 auto,ro,user,owner 0 0
```

When doing this; neither the admin account or the standard user account can mount the array. I'm assuming that this has to be controlled via permissions and not via the fstab?

In addition to all this; if I add the UUID of the array to the fstab:

```
UUID=XXXX-XXXX-XXXX-XXXX /media/RAIDArray/ ext4 defaults 0 0
```

When using the command sudo mount -a I get the following:

```
special device UUID=fxxxx-xxxx-xxxx-xxxx does not exist
```

anyone dealt with these issues?

---

### Post by drmrgd on 2012-10-24
Can you do this by adding some permission masks to the fstab entry?  I'm terrible at this myself, but this might help:

[http://www.omaroid.com/fstab-permission-masks-explained/](http://www.omaroid.com/fstab-permission-masks-explained/)

---

### Post by bomski on 2012-10-24
I haven't tried user masks (yet); i've read so much conflicting stuff i'm hoping someone that has dealt with this can point me in the right direction!

---

### Post by bomski on 2012-10-25
**UPDATE 1: **

Found after some digging that there are two commands for generating the UUID for a RAID array; both give different results and only one works with fstab:

mdadm --detail -scan gives a UUID which does not work with fstab

**blkid /dev/md127 gives a completely different UUID and works with fstab**

still trying to fathom out the user permissions; anyone got any pointers / advice?

---

