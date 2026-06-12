---
title: "Automount a vfat partition with single user permissions"
date: 2007-05-07
forum: General Help
---

### Post by pherris on 2007-05-07
Problem: I need to mount a VFAT partition with permissions that only allow one user to access.

I have three partitions on my machine: an EXT3 partition for Ubuntu, NTFS for Vista, and a VFAT partition accessible to both Ubuntu and Vista. While using "umask=006" in fstab works well it has the side effect of "u=rwx,g=x,o=x" to the files. Using fmask and dmask instead of umask fixes the problem.

(the user and group IDs "1000" are mine. To get yours just "grep pherris: /etc/passwd && grep pherris: /etc/group" using your name)

fstab options before: "quiet,utf8,umask=006,uid=1000,gid=1000"
would result in "u=rwx,g=x,o=x".

fstab options now: "quiet,utf8,umask=177,dmask=077,uid=1000,gid=1000"
results in "u=rw,g=,o=" for files and  "u=rwx,g=,o=" for directories.

Is anyone else using something like this solution and, if so, have you had any problems?

Thanks.

---

