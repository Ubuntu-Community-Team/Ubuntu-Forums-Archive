---
title: "selinux-policy-default package won't install on feisty"
date: 2007-05-03
forum: General Help
---

### Post by quark_77 on 2007-05-03
Hi All,

I've enabled SELinux on my kernel with the appropriate switches, selinux=1 enforcing=0. I can't get selinux-policy-default to install - the actual package runs through OK, however, here's the end of it:
```
Validating file contexts files ...
make: /usr/sbin/setfiles: Command not found
make: *** [tmp/valid_fc] Error 127
dpkg: error processing selinux-policy-default (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 selinux-policy-default

```

True to what it says, /usr/sbin/setfiles doesn't exist. Does anyone know why this could be happening. For the record, I'm using an encrypted root partition, luks/devmapper and my "device" is using the XFS file system - for all other commands the filesystem behaves as if it wan't encrypted so I'm unsure why this package is falling over, just a thought though as it's the only major change I've from when I was on Edgy...

I picked up a number of links to various debian bug reports on the topic, although I'm not getting the same messages they are.

Thanks in advance for your help,

Quark_77

---

### Post by quark_77 on 2007-05-05
Ok it will install... if you create a symlink from /sbin/checkfiles to /usr/sbin/checkfiles.

---

### Post by maruhana on 2007-11-20
Can you give more info on how to install Selinux step by step

thank you very much

---

