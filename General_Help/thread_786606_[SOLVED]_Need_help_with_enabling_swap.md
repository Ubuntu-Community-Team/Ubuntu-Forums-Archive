---
title: "[SOLVED] Need help with enabling swap"
date: 2008-05-08
forum: General Help
---

### Post by thomasyen on 2008-05-08
Hello all.
I have been running Ubuntu for about ten months now, and I only just recently discovered that I have no swap space! I had created a 2 Gb swap partition while installing the system, but when I used the command "swapon -a", I got this: 

thomasyen@thomasyen-desktop:~$ swapon -a
swapon: cannot canonicalize /dev/disk/by-uuid/46bab5bf-18a6-47b5-bd83-b77b5b570b13: No such file or directory
swapon: cannot stat /dev/disk/by-uuid/46bab5bf-18a6-47b5-bd83-b77b5b570b13: No such file or directory

My /etc/fstab file lists this:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
...
UUID=46bab5bf-18a6-47b5-bd83-b77b5b570b13 none            swap    sw              0       0
...

And when I gave the command "top", it returned this:

top - 20:51:46 up 16 min,  2 users,  load average: 0.62, 0.43, 0.36
Tasks: 136 total,   1 running, 134 sleeping,   0 stopped,   1 zombie
Cpu(s): 12.3%us,  1.1%sy,  0.0%ni, 86.6%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1035160k total,   803088k used,   232072k free,    27504k buffers
[COLOR="Blue"]Swap:        0k total,        0k used,        0k free,   387808k cached
[/COLOR]

Can anyone help me?

---

### Post by kpkeerthi on 2008-05-08
It appears that the UUID of your swap partition does not match with the one in FSTAB. [Get the UUID]("http://ubuntuforums.org/showthread.php?t=349376") and update your FSTAB.

---

### Post by thomasyen on 2008-05-09
Thanks! My swap space is now enabled.

---

