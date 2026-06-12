---
title: "mysqld uses 400% CPU"
date: 2015-07-03
forum: General Help
---

### Post by ELMIT on 2015-07-03
My CPU indicator shows 100% most of the time on my 8 core system.

Using top it shows 

top

> top - 06:39:39 up 14:27,  9 users,  load average: 37.23, 42.10, 44.34
Tasks: 359 total,   1 running, 358 sleeping,   0 stopped,   0 zombie
%Cpu(s): 97.8 us,  1.7 sy,  0.0 ni,  0.2 id,  0.0 wa,  0.0 hi,  0.2 si,  0.0 st
KiB Mem:  32899048 total, 32331808 used,   567240 free,  5909384 buffers
KiB Swap: 33503228 total,        0 used, 33503228 free. 12867604 cached Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND                                                                                    
 1697 mysql     20   0 4519132 303080  11260 S 379.3  0.9   2972:32 mysqld      


It used to be in much lower range.
What could it cause, how can I fix it?

---

### Post by oscar-tiderman on 2015-07-04
Is there any process using MySQL when you see the load? You could run "mysqladmin processlist" to find out what it is doing. Could also be the leap second bug if there is nothing obvious causing the mysqld CPU spike, if so you can fix it with: date -s "`date -u`"

---

### Post by ELMIT on 2015-07-04
Thanks!   mysqladmin processlist   showed that the bookmark program I have installed does not only handle MY bookmarks, but also from other's, ... When I stopped the access to that web site, mysqld is normal again.

---

