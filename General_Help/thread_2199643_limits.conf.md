---
title: "limits.conf"
date: 2014-01-15
forum: General Help
---

### Post by fafabone on 2014-01-15
Hi All,
I need to augment the max number of file opened per process.
If I send the command ulimit -a on root user, I receive 1024 and if I send the command on apache user, I receive 4096.
I've read many documents on the net, so I've followed common tips, but none was the right one.
- I've set on limits.conf:
*               soft    nofile            65000
- On /etc/pam.d/sshd /etc/pam.d/login /etc/pam.d/common-session I've check or added the line "session required pam_limits.so"
I've added fs.file-max = 65000 on /etc/sysctl.conf file
- I've rebooted the system
What I need to do? In the next future, could I change the nofile value without reboot the system?
Thanks for the help.

---

### Post by fafabone on 2014-01-16
Please, give me an help

---

### Post by Doug S on 2014-01-16
The only thing I can suggest is that you give us a little more information about your specific application and what error messages you are getting.
The only difference I observe between our two limits.conf file is that my setting isn't soft:```
#        - memlock - max locked-in-memory address space (KB)
#        - nofile - max number of open files (smythies.com - so Samba will not complain)
[COLOR=#ff0000]* - nofile 16384[/COLOR]
#        - rss - max resident set size (KB)
#        - stack - max stack size (KB)
```

---

### Post by Bucky Ball on 2014-01-17
Thread moved to ***General Help.***

Posting in the correct sub-forum may help your cause. ;)

---

### Post by tgalati4 on 2014-01-17
What problem are you trying to solve?  Perhaps there are other ways to solve it?

When you changed your sysctl.conf settings did the behavior of your system change?  What is the behavior?

---

### Post by fafabone on 2014-01-20
Please, can you change the category of this post in General Help?
 I tried hard limit also in limits.conf. 
I need to augment the number of concurrent connection possible. It is not an hardware limit, because during the stress tests (8K and 16K concurrent get requests), the cpu was busy for 40%, ram was 90% free, but active connections had never been more than 4K. 
The time of the answer to get requests exploded. Can you suggest a way to augment the number of concurrent connection possible?

---

