---
title: "apt configure script"
date: 2007-02-07
forum: General Help
---

### Post by carverj on 2007-02-07
Followed Syitty's advice on following forum post:
[http://www.ubuntuforums.org/archive/index.php/t-33633.html](http://www.ubuntuforums.org/archive/index.php/t-33633.html)
and encountered some problems with the script. Bailed out half way through and it hasn't helped me!  Also getting the following error when finishing synaptic tasks:
```
E: selinux-policy-default: subprocess post-installation script returned error exit status 2
```

---

### Post by carverj on 2007-02-07
Just to expand on that error as seen at end of terminal aptitude install (amsn)

```
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up selinux-policy-default (1.26-7) ...
cat: /selinux/policyvers: No such file or directory
Compiling policy ...
policyvers value 0 not in range 15-20
usage:  /usr/bin/checkpolicy [-b] [-d] [-M] [-c policyvers (15-20)] [-o output_file] [input_file]
make: *** [/etc/selinux/./policy/policy.] Error 1
dpkg: error processing selinux-policy-default (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 selinux-policy-default

```

---

