---
title: "date shows UTC"
date: 2015-02-28
forum: General Help
---

### Post by geohei on 2015-02-28
Hi.

Ubuntu 12.04 server.
Despite the fact that /etc/timezone is properly configured to correct timezone, date command shows UTC.
How can I change this behavior?
All this happens on a VPS.

My local Ubuntu 14.04 VM has /etc/timezone also configured, but date shows the local time.

What differs both systems?

Thanks,

---

### Post by TheFu on 2015-02-28
Run /usr/bin/tzselect with sudo.

Or

TZ can be set for each login ... or in each userid's environment.

For example, add/uncomment the appropriate line to your .bashrc:```

TZ='America/New_York'; export TZ
#TZ='America/Denver'; export TZ
#TZ='America/St_Thomas'; export TZ
#TZ='America/Buenos_Aires'; export TZ
#TZ='Europe/London'; export TZ
#TZ='Asia/Bangkok'; export TZ
#TZ='Asia/Tokyo'; export TZ
#TZ='Asia/Hong_Kong'; export TZ
#TZ='Asia/Seoul'; export TZ
#TZ='Asia/Kathmandu'; export TZ
#TZ='Europe/Amsterdam'; export TZ
#TZ='Europe/Rome'; export TZ
#TZ='Europe/Vienna'; export TZ
#TZ='Europe/Prague'; export TZ
#TZ='Africa/Johannesburg'; export TZ
```

You get the idea.

---

### Post by Nutria on 2015-02-28
> **geohei said:**
> Hi.

Ubuntu 12.04 server.
Despite the fact that /etc/timezone is properly configured to correct timezone, date command shows UTC.
How can I change this behavior?
All this happens on a VPS.

How long has it been like that?  (Did it just start happening?)

Is "date" aliased to "date -u"?

---

### Post by geohei on 2015-03-02
Hi.

Thanks for the answer.

No aliases set.

Also ...
```
root@venus:~# cat ~/.bashrc | grep TZ
root@venus:~#
```

Must be something else.

---

### Post by geohei on 2015-03-03
I found that apparently /etc/localtime is in charge.

TZ can be changed using:
```
root@venus:~# dpkg-reconfigure tzdata
```
This worked!

Now I would like to change the locales to en_US.UTF-8. This must be done in /etc/default/locale,
```
root@venus:~# locale -a
C
C.UTF-8
de_DE.utf8
en_US.utf8
POSIX
root@venus:~# cat /etc/default/locale
LANG=en_US.UTF-8
```
This worked as well.

Changes persist after reboot.

---

