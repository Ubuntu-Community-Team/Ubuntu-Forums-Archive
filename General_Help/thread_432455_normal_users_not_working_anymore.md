---
title: "normal users not working anymore"
date: 2007-05-04
forum: General Help
---

### Post by jebe86 on 2007-05-04
HI all, 

I have an ubuntu-desktop runnig 6.10.
I did upgrade packages on May 2nd, at 17:00 MET, and immediately after that, only root can do things. Any other user, from normal account to gdm, can not do anything.
I upgraded to 7.04 (using upfate manager), but still ìhave the same problem.
It loks like some kind of protection (selinux non running, and lockdown-plessus disabled). 

effect is not only that normal user can not login, but also other apps will not work.

Example:
root@laptop-p:~# su user
Cannot execute /bin/bash: Permission denied
root@laptop-p:~# gdm
gdm_config_parse: Authdir /var/lib/gdm does not exist. Aborting.

Any clue ?

any help greatly appreciated

---

### Post by aidanr on 2007-05-04
permissions problem maybe? what does ```
ls -ld /
``` give back?

---

### Post by jebe86 on 2007-05-04
> **aidanr said:**
> permissions problem maybe? what does ```
ls -ld /
``` give back?

root@laptop-p:/etc/security# ls -ld /
drwx------ 27 root root 4096 2007-05-03 18:42 /

---

### Post by aidanr on 2007-05-04
ok so it is a permissions problem, users and other groups do not have read or execute permissions, for example mine gives back:

drwxr-xr-x 21 root root 4096 2007-04-22 21:59 /

i'm not sure exactly how to go about fixing this, for example setting 755 permissions recursively probably wouldn't be wise

can someone else chime in here?

---

### Post by jebe86 on 2007-05-04
> **aidanr said:**
> ok so it is a permissions problem, users and other groups do not have read or execute permissions, for example mine gives back:

drwxr-xr-x 21 root root 4096 2007-04-22 21:59 /

i'm not sure exactly how to go about fixing this, for example setting 755 permissions recursively probably wouldn't be wise

can someone else chime in here?


nopes, just changing permissions -R would not be wise, but what surprises me is the fact that just upgrading some packegs had this effect.
Packages upgrade where (as from /var/log/dpkg,log)


# cat /root/doc/lista_dpkg | grep installed | grep -v half
2007-05-02 08:14:38 status installed beep-media-player 0.9.7.1+cvs20050803-1.1ubuntu1
2007-05-02 08:18:34 status installed beep-media-player 0.9.7.1+cvs20050803-1.1ubuntu1
2007-05-02 09:08:31 status installed libogg-dev 1.1.3-2ubuntu1
2007-05-02 09:08:50 status installed libvorbis-dev 1.1.2-1ubuntu1
2007-05-02 09:11:17 status installed libflac-dev 1.1.2-5ubuntu1
2007-05-02 09:31:48 status installed soundkonverter 0.2-0ubuntu1
2007-05-02 17:00:28 status installed libx11-data 2:1.0.3-0ubuntu4.1
2007-05-02 17:00:34 status installed libx11-6 2:1.0.3-0ubuntu4.1
2007-05-02 17:00:34 status installed libx11-dev 2:1.0.3-0ubuntu4.1
2007-05-02 17:00:34 status installed tzdata 2007e-0ubuntu0.6.10
2007-05-02 17:00:39 status installed kdelibs-data 4:3.5.5-0ubuntu3.4
2007-05-02 17:00:39 status installed libqt3-mt 3:3.3.6-3ubuntu3.1
2007-05-02 17:00:39 status installed kdelibs4c2a 4:3.5.5-0ubuntu3.4
2007-05-02 17:00:40 status installed libpq4 8.1.9-0ubuntu0.6.10

---

### Post by jebe86 on 2007-05-04
Ok, assuming that only / had changed permissions, and not all/othe dirs underneath, I change only / to drwxr-xr-x, and everything seems fine now !

Thanks for the help.

Now I'll try to see why / changed perms.

thanks again

---

