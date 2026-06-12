---
title: "FUSE Installation on 12.04"
date: 2014-04-28
forum: General Help
---

### Post by Ryan_Collins on 2014-04-28
Hi all,

I'm working on installing FUSE for use with SSHFS and continue getting stuck with fuse module not present errors. I've tried installing via apt-get and downloading the tarball. No luck with either. I'm wondering if someone can point me in a better direction. lsmod | grep fuse lists nothing. 

--Ryan

---

### Post by Habitual on 2014-04-29
IF ```
modprobe fuse
``` as root doesn't complain you should be ok.

I *think* the process to install the module is 
```
insmod fuse
``` but hold off until someone says otherwise, or differently ( I don't use Ubuntu)

Have you seen [https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS) ?

---

### Post by steeldriver on 2014-04-29
Are you sure fuse support is not configured in to the built kernel? it is on my 12.04 desktop

```

$ grep -i 'fuse' /boot/config-`uname -r`
CONFIG_AUFS_BR_FUSE=y
**CONFIG_FUSE_FS=y**

```

I can mount sshfs without loading any additional modules

---

