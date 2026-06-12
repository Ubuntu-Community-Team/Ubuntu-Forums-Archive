---
title: "sshfs mount problems"
date: 2006-12-14
forum: General Help
---

### Post by kitchens on 2006-12-14
Hello, I'm experiencing this issue on a Dapper machine using 2.6.15-27-386
 kernel. When I attempt to mount sshfs with a command such as this:
```
sudo sshfs root@192.168.1.1:/ /media/sshfs -o allow_other
``` 
I get this error:
```
fusermount: failed to open /dev/fuse: No such device or address
```
In the past I would run this command to correct that problem:
```
sudo mknod -m 666 /dev/fuse c 10 299
```
But now even after running that command I get the 'No such device or address' error. If I attempt to run the 'mknod' command again I get an error that '/dev/fuse' already exists.
Any ideas?

---

### Post by Peter76 on 2006-12-14
I think the problem is youre fuse module is not loaded. Try:

sudo modprobe fuse

And if that works, add it to your /etc/modules

---

### Post by kitchens on 2006-12-14
> **Peter76 said:**
> I think the problem is youre fuse module is not loaded. Try:

sudo modprobe fuse

And if that works, add it to your /etc/modules

That did the trick. Thanks for your input.

---

