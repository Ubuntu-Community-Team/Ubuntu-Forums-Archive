---
title: "mount dependence in fstab"
date: 2018-05-05
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2018-05-05
Lets have i have 3 partitions and a bind point
[LIST]
[*]/ 
[*]/home 
[*]/mnt 
[/LIST]
bind point:
[LIST]
[*]bind  /home/user/extraSpace /mnt/someFolder 
[/LIST]
How can i prevent the system from trying to bind a point that does not exist before /home is mounted?

---

### Post by dino99 on 2018-05-05
i've no clue about your request, but found this, if it can clarify something:
[https://superuser.com/questions/623375/mounting-directories-with-bind-different-permissions](https://superuser.com/questions/623375/mounting-directories-with-bind-different-permissions)

---

### Post by pqwoerituytrueiwoq on 2018-05-05
I dealt with this once before on my laptop and NEVER found a solution i ended up doing a clean install
i had some flaky fix in place it did not fix it but make it happen less frequently
*looks up old threads, here we go [https://ubuntuforums.org/showthread.php?t=2336078](https://ubuntuforums.org/showthread.php?t=2336078)
here is some other info i found:
[https://copyninja.info/blog/systemd_automount_entry.html](https://copyninja.info/blog/systemd_automount_entry.html)
[https://www.freedesktop.org/software/systemd/man/systemd.mount.html](https://www.freedesktop.org/software/systemd/man/systemd.mount.html)

---

