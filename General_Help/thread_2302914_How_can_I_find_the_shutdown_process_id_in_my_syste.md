---
title: "How can I find the shutdown process id in my system?"
date: 2015-11-14
forum: General Help
---

### Post by libertorres on 2015-11-14
Hello

I would like to know where is shutdown process in my system when I run it in the shell of Lubuntu. 

When I run it in Ubuntu
$ sudo shutdown -h +30

I can see it as
$ ps -ef 
root      5470  3101  0 20:00 pts/0    00:00:00 sudo shutdown -h +30
root      5471  5470  0 20:00 pts/0    00:00:00 shutdown -h +30

When I run it in Lubuntu and I launch ps -ef I am not able to recognize the associated process.
I can see that it is scheduled in file:  /run/systemd/shutdown/scheduled

More info:
System:Lubuntu 15.10
Init: systemd

---

### Post by ian-weisser on 2015-11-16
Shutdown under systemd should not be a separate process. It's an instruction to systemd.

You can see by looking at shutdown using the 'ls' command...
```
$ ls -l /sbin/shutdown 
lrwxrwxrwx 1 root root 14 Oct 15 07:02 /sbin/shutdown -> /bin/systemctl
```
...that 'shutdown' seems merely a symlink to systemd's systemctl.

Are the Ubuntu and Lubuntu systems both 15.10? Or is the Ubuntu system perhaps pre-systemd?

---

