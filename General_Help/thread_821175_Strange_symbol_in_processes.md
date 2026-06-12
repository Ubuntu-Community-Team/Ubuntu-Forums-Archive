---
title: "Strange symbol in processes"
date: 2008-06-06
forum: General Help
---

### Post by WasteOfSpace on 2008-06-06
I was checking my running processes with ps aux and I came across the following:

root      5337  5.6  3.8  44964 39464 tty7     SLs+ 13:25   0:04 /usr/bin/X -br -nolisten tcp :0 vt7 -auth /var/run/xauth/A[COLOR="Red"]:0[/COLOR]-ydNdqP

root      5354  0.0  0.1   3912  1596 ?        S    13:25   0:00 -:0
                                    
root      5374  0.0  0.0   5316  1024 ?        Ss   13:25   0:00 /usr/sbin/sshd

avahi     5398  0.0  0.1   2760  1468 ?        Ss   13:25   0:00 avahi-daemon: running [ubuntu1.local]

Process number 5354 has a process running that is called :0
Should I be worried about this?  :confused:

---

