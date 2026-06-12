---
title: "Repairing selinux-policy-default"
date: 2007-01-21
forum: General Help
---

### Post by Souljah on 2007-01-21
Hi.

Now I'm having problems installing software and this is what happens:

```
sudo aptitude install nvidia-glx
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initialising package states... Done
Building tag database... Done
The following packages have been kept back:
  fuse-utils libfuse2
0 packages upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
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

Now this is happened with other installations as well? What is this sellinux and how do I repair it? Thanks.

Ryan

---

### Post by Souljah on 2007-01-21
Ok I was instructed to remove selinux.

---

### Post by victorbrca on 2007-03-18
Where you able to remove selinux with no problem??? I've been going on an on for a couple days trying to figure this out without screwing up my system....


Vic.

---

### Post by raycast on 2007-04-01
Run

dpkg --purge selinux-policy-default

to get rid of the broken selinux-policy-default package.

Maybe request the removal of the package from Ubuntu, and try to get some people together to start working on a decent SELinux support in Ubuntu. AFAICT it's pretty much nonexistent.

---

