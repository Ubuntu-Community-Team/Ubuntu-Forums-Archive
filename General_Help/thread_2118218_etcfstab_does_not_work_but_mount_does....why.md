---
title: "/etc/fstab does not work but mount does....why?"
date: 2013-02-20
forum: General Help
---

### Post by saejin on 2013-02-20
I can not understand why my fstab entry failed to mount, but if I then try to do in manually, the directory mounts.  Any ideas?

192.168.2.1 is  able to be pinged

/etc/fstab entry in the same file that does not work when I do a **sudo mount -a**

[B]192.168.2.1:/media/stores/store1/store1 /media/store1 nfs rw,auto,mountvers=3,rsize=8192,wsize=8192,timeo=14,nolock 0 0
[/B]
when I do a mount -a     I get the error
**mount.nfs: an incorrect mount option was specified**

command line that does work
**sudo mount -t nfs -o nfsvers=3 192.168.2.1:/media/stores/store1/store1  /media/store1**


[COLOR=Red]update:  It was a typo, a period where a comma should have been that evaded me even as I transposed it into the forum.  Not all was lost on stupidity.  I found the VIM editor knows the syntax of /etc/fstab,  knows it is editing /etc/fstab and highlights each part of the line in a different color.   The error was standing out in a bright color of white while the other parts of the line were green, blue etc.

):PThe vim  editor is a great piece of work.  Thanks for the folks that gave it to us![/COLOR]

---

### Post by lordievader on 2013-02-20
You are trying to mount a network file system. Are you sure that at the time of booting the network interface is up?

-lordievader.

---

### Post by saejin on 2013-02-20
a

---

### Post by jawilljr on 2013-02-20
Change the line:

```
192.168.2.1:media/stores/store1/store1 /media/store1 nfs rw,auto,mountvers=3,rsize=8192,wsize=8192,timeo=14 ,nolock 0 0
```

to this:

```
192.168.2.1:/media/stores/store1/store1 /media/store1 nfs rw,auto,mountvers=3,rsize=8192,wsize=8192,timeo=14 ,nolock 0 0
```

It is missing a slash '/' in front of 'media'.

Hope that works.

Jerry

---

### Post by saejin on 2013-02-20
a

---

