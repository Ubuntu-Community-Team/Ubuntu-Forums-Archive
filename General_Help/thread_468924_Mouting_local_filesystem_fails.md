---
title: "Mouting local filesystem fails"
date: 2007-06-09
forum: General Help
---

### Post by Fallon on 2007-06-09
I've had Ubuntu work before with the LiveCD but want to use the Wubi method really.

It fails at 

mounting local filesystems
media/host/wubi/disks/usr.virtual.disk
media/host/wubi/disks/extra.virtual.disk - No such file or directory

Any ideas? Tried reinstalling, can't seem to get any further than this point. I'd be grateful for any assistance.

---

### Post by ago on 2007-06-09
You can ignore that, it should not be a fatal error. You can simply remove the 2 lines from /etc/fstab

---

### Post by Fallon on 2007-06-09
I can't find the etc folder

---

### Post by ago on 2007-06-10
sudo gedit /etc/fstab

---

### Post by Fallon on 2007-06-11
How can I execute sudo if I can't boot into it? :(

---

### Post by Fallon on 2007-06-15
> **Fallon said:**
> How can I execute sudo if I can't boot into it? :(

3 beans

---

