---
title: "Setup for hourly CRONTAB not working"
date: 2012-11-11
forum: General Help
---

### Post by joiseystud on 2012-11-11
I'm trying to create a crontab that executes a time sync command ever hour.

I think the correct syntax for this would be :

```
* */1 * * * ntpdate pool.ntp.org >> /home/user/ntpdate.log
```

Its not working for me. if i run the command in a shell with Sudo it works.  PS I am putting this in the sudo crontab -e , ie root crontab.

---

### Post by efflandt on 2012-11-11
Simple, in crontab default PATH is set to "/usr/bin:/bin".  ntpdate is not in those paths.  So it is best to set the full path to executable or scripts, or first define PATH=

Also in such a line you might consider redirecting stderr to stdout, so any error would also be redirected to your log

```
* */1 * * * /usr/sbin/ntpdate pool.ntp.org >> /home/user/ntpdate.log 2>&1
```

In a terminal read: **man 5 crontab**

---

### Post by joiseystud on 2012-11-11
> **efflandt said:**
> Simple, in crontab default PATH is set to "/usr/bin:/bin". ntpdate is not in those paths. So it is best to set the full path to executable or scripts, or first define PATH=
 
Also in such a line you might consider redirecting stderr to stdout, so any error would also be redirected to your log
 
```
* */1 * * * /usr/sbin/ntpdate pool.ntp.org >> /home/user/ntpdate.log 2>&1
```
 
In a terminal read: **man 5 crontab**
 
 
Excellent.  Thank you!

---

