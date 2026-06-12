---
title: "dpkg seriously broken"
date: 2018-04-25
forum: General Help
---

### Post by zerobytez on 2018-04-25
I booted up an old PC running Ubuntu 17.10 Artful, and upon trying to update I get this:

```
Setting up systemd (234-2ubuntu12.3) ...
cp: 'etc/resolv.conf' and '/run/systemd/resolve/stub-resolv.conf' are the same file
dpkg: error processing package systemd (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 systemd
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I'm unable to install packages due to this. From what I see, the error is that copy statement, and I'm not sure whether to delete one, and if so which, or of im not meant to delete either and the error is somewhere else.

---

### Post by again? on 2018-04-25
Try
```
sudo apt full-upgrade
```

> **full-upgrade** (apt-get(8))

full-upgrade performs the function of upgrade but will remove currently installed packages if this is needed to upgrade the system as a whole.
Edit: but then again you probably can't even get to this stage???
FYI, here on 17.10 /etc/resolv.conf is a link to /run/systemd/resolve/stub-resolv.conf

---

### Post by zerobytez on 2018-04-26
Deleted /etc/resolve.conf, seems to have fixed it, which is weird if its a link.

---

### Post by again? on 2018-04-26
Had several issues with systemd and DNS resolving in 17.10.

---

