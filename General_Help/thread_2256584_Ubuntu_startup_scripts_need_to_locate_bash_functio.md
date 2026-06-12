---
title: "Ubuntu startup scripts: need to locate bash function &quot;clean_all&quot;"
date: 2014-12-13
forum: General Help
---

### Post by Groot on 2014-12-13
I just installed Ubuntu 14.10 . One of the things that I prefer in my  desktop is to not clear out /tmp . I'm trying to do the same in 14.10:  to prevent the /tmp from being cleared at boot. 

  In one of the startup scripts ( /etc/init.d/mountall-bootclean.sh ), there's a call to "clean_all", which does the cleanup. I'd like to modify it. But, for the life of me I can't find where it is defined:

  ```
 % sudo grep -r -w -l clean_all /etc
 /etc/init.d/mountall-bootclean.sh
 /etc/init.d/checkroot-bootclean.sh
 /etc/init.d/mountnfs-bootclean.sh
  
```
So lets look at one of those, /etc/init.d/mountall-bootclean.sh . It starts with:

  ```
. /lib/lsb/init-functions

. /lib/init/bootclean.sh

```

It's not defined in either of those. Out of frustration (and equipped with an SSD), I tried the following:
  [FONT=courier new]sudo find /bin /boot /etc /lib* /sbin /usr /var -type f -print0 | xargs -0 -s 4096 sudo grep -s -w -l clean_all
[/FONT]  The result? It's only in the following files:
  ```
/etc/init.d/mountall-bootclean.sh
/etc/init.d/checkroot-bootclean.sh
/etc/init.d/mountnfs-bootclean.sh
/usr/lib/gimp/2.0/python/gimp.so
/var/log/auth.log

```  I must be missing something really obvious, for I can't seem to find clean_all defined anywhere! Any ideas?


  PS: I checked, it's not a file either

---

### Post by ian-weisser on 2014-12-13
Most startup jobs are no longer in /etc/init.d
Most Upstart jobs are in /etc/init instead.
Current planning is to replace Upstart with systemd in 15.04.

The specific Upstart job you are looking for is /etc/init/mounted-tmp.conf 
See [http://askubuntu.com/questions/20783/how-is-the-tmp-directory-cleaned-up](http://askubuntu.com/questions/20783/how-is-the-tmp-directory-cleaned-up) for a great discussion of your options.

---

### Post by Groot on 2014-12-14
Lord! Shows how long it's been since I mucked around with a clean install. 

That link looks like exactly what I was looking for; thanks!

---

