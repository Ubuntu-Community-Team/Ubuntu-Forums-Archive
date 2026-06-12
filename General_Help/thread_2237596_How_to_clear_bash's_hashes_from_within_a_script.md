---
title: "How to clear bash's hashes from within a script"
date: 2014-08-02
forum: General Help
---

### Post by terminator14 on 2014-08-02
I made a shell wrapper script for /sbin/fdisk. I have a second script - install.sh - install it into /usr/local/bin/.
The problem is, bash hashes /sbin/fdisk, so when the install.sh script exits, running "fdisk" still points to /sbin/fdisk instead of /usr/local/bin/fdisk.
Outside of install.sh, this can be easily fixed with "hash -r" or "hash -d fdisk", but this can't be done from within the install.sh script, because the script runs in
a different environment than the shell that ran it.
Is there any way to clear the bash hash table in the shell that runs install.sh by adding some line to install.sh, so that as soon as install.sh is done running,
you can run "fdisk" and it will point to the new location (/usr/local/bin/fdisk)?

---

