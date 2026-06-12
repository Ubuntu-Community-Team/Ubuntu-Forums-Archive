---
title: "*BUG* overnight unattend update of libc6-i386_2.11.1-0ubuntu7.14_amd64.deb"
date: 2014-08-05
forum: General Help
---

### Post by fdelin on 2014-08-05
Good morning,

My lucid systems auto applied the libc6-i386_2.11.1-0ubuntu7.14_amd64.deb update this morning and now I have apps like lpr, lpq, ssh throwing errors like:

*** glibc detected *** /usr/bin/ssh: munmap_chunk(): invalid pointer: 0x00007fabcd690528 *** and

*** glibc detected *** lpq: double free or corruption (out): 0x00007f187eb5c3f0 ***

I was able to kludge together a wrapper for them with export MALLOC_CHECK_=0 to get the ability for my users to print this morning but this needs to be addressed in a hurry.

Or is there a way that I can at the very least assert MALLOC_CHECK_=0 in a way that all of the programs will inherit this, including scripts that may run in good ole sh.  Beyond /etc/profile.d/xx.sh.

Thanks,

Frank

---

### Post by tgalati4 on 2014-08-05
In /var/log are log files dpkg.log and /apt which contain the update history.  Perhaps the update failed or a reboot is required to get the post-installion scripts to finish correctly.  If your log files are clear and a reboot and a manual check for updates does not fix the problem, then perhaps file a bug against libc6.  It's possible that it is a bad package.  If you have multiple machines, do they pull from a local update mirror?

---

### Post by fdelin on 2014-08-05
Found the issue in launchpad, they are testing a fix, seems to only hit people who are using nscd + ldap for passwd/shadow/group as we are:

[https://bugs.launchpad.net/ubuntu/lucid/+source/eglibc/+bug/1352504](https://bugs.launchpad.net/ubuntu/lucid/+source/eglibc/+bug/1352504)

Thanks,

Frank

---

