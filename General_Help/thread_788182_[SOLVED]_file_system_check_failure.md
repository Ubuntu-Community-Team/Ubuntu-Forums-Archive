---
title: "[SOLVED] file system check failure"
date: 2008-05-09
forum: General Help
---

### Post by grandquist on 2008-05-09
I am having trouble with the file system check on start up. I am guessing the problem started because I used vista to delete my mandriva partition. Here is a copy of the log file.

Log of fsck -C3 -R -A -a 
Fri May  9 08:23:34 2008

fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Unable to resolve 'UUID=d2824586-c5a3-4bb1-bdb3-55c6e135967f'

fsck died with exit status 8

Fri May  9 08:23:34 2008
----------------

After that it gives me a shell which exits with ctrl-d. Nothing seems to be broken once I log in.

---

### Post by phidia on 2008-05-09
If you use a text editor with sudo for example sudo gedit /etc/fstab
to delete or comment the entry in fstab that corresponds to the partition that was deleted (you can place the # symbol before the partition entry with the UUID listed in that error message) and that should stop the file system check.

---

