---
title: "apache log - preventing zipping"
date: 2007-11-19
forum: General Help
---

### Post by phillips321 on 2007-11-19
Hi guys,

I use a tool called visitors to my web stats, the problem is that the output of the log files keeps getting saved as "**************.log.*n*.gz" i.e.

```
-rw-r----- 1 root adm  831K 2007-11-19 19:52 access_phillips321.co.uk.log
-rw-r----- 1 root adm  388K 2007-11-11 02:38 access_phillips321.co.uk.log.1
-rw-r----- 1 root adm  148K 2007-09-09 04:27 access_phillips321.co.uk.log.10.gz
-rw-r----- 1 root adm   76K 2007-09-02 04:46 access_phillips321.co.uk.log.11.gz
-rwxrwxrwx 1 root root 563K 2007-08-26 03:17 access_phillips321.co.uk.log.12.gz
-rw-r----- 1 root adm   12K 2007-11-03 22:49 access_phillips321.co.uk.log.2.gz
-rw-r----- 1 root adm   47K 2007-10-28 02:23 access_phillips321.co.uk.log.3.gz
-rw-r----- 1 root adm   58K 2007-10-20 23:57 access_phillips321.co.uk.log.4.gz
-rw-r----- 1 root adm   64K 2007-10-14 03:44 access_phillips321.co.uk.log.5.gz
-rw-r----- 1 root adm   32K 2007-10-06 23:05 access_phillips321.co.uk.log.6.gz
-rw-r----- 1 root adm   23K 2007-09-29 22:14 access_phillips321.co.uk.log.7.gz
-rw-r----- 1 root adm   68K 2007-09-22 23:43 access_phillips321.co.uk.log.8.gz
-rw-r----- 1 root adm   42K 2007-09-15 18:09 access_phillips321.co.uk.log.9.gz

```

how do i prevent apache from splitting up my log files like this and instead keep the log files as one huge single file?

also is there a way i can recover the data from the files that are already archived and incorporate them into the main log file?

cheers

---

### Post by phillips321 on 2007-11-19
Any one got any idea?
[[IMG]http://www.forumpix.co.uk/uploads/1195520852.jpg[/IMG]](http://www.forumpix.co.uk)

---

