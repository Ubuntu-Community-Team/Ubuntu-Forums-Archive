---
title: "what is accessing my disk?"
date: 2013-03-02
forum: General Help
---

### Post by djevlen on 2013-03-02
hi

Something is bringing my storage disk drives out of standby and want to find out what it is. I cant use tools like Iotop because its in real time and if the process im looking for is accessing the disk only once every 2 or 3  hours (it is exactly what is happening) i will for  sure miss it.

The best would be to log ALL access/read/write activity to some text file or so and i must be able to set the program to monitor specific disk. not all disks.

Any suggestions  ?

---

### Post by Bufeu on 2013-03-02
*iotop*?
[http://www.manpagez.com/man/1/iotop/](http://www.manpagez.com/man/1/iotop/)

---

### Post by djevlen on 2013-03-02
> **Bufeu said:**
> *iotop*?
[http://www.manpagez.com/man/1/iotop/](http://www.manpagez.com/man/1/iotop/)


it says no such option ::


iotop -m /media/lol
iotop: error: no such option: -m


:(

---

### Post by HermanAB on 2013-03-02
Syslog, cron...

Have a look in /etc/cron.hourly and in the root crontab.

---

