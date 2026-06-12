---
title: "My crontab is not working"
date: 2008-04-13
forum: General Help
---

### Post by Helgiks on 2008-04-13
I'm having a little trouble getting my crontab to work, every thing seems to be all right.

# reboot

# date;ls -lut /etc/init.d/cron
   Mon Apr 14 01:45:08 GMT 2008
   -rwxr-xr-x 1 root root 1761 2008-04-14 01:36 /etc/init.d/cron

# ps -el | grep cron
   1 S     0  5724     1  0  75   0 -   583 -      ?        00:00:00 cron

# ls -lut /etc/crontab
   -rw-r--r-- 1 root root 724 2008-04-14 01:36 /etc/crontab

# date;ls -lut /etc/cron.daily
   Mon Apr 14 01:47:12 GMT 2008
   total 68
   -rwxr-xr-x 1 root root 1309 2008-04-14 01:45 sysklogd
   -rwxr-xr-x 1 root root  123 2008-04-14 01:45 tripwire
   -rwxr-xr-x 1 root root 3283 2008-04-14 01:45 standard
   -rwxr-xr-x 1 root root  420 2008-04-14 01:45 slocate
   -rwxr-xr-x 1 root root  383 2008-04-14 01:42 samba
   -rwxr-xr-x 1 root root   89 2008-04-14 01:42 logrotate
   -rwxr-xr-x 1 root root  946 2008-04-14 01:42 man-db
   -rwxr-xr-x 1 root root  314 2008-04-14 01:42 aptitude
   -rwxr-xr-x 1 root root  502 2008-04-14 01:42 bsdmainutils
   -rwxr-xr-x 1 root root 4197 2008-04-14 01:42 exim4-base
   -rwxr-xr-x 1 root root 5811 2008-04-14 01:42 apt
   -rwxr-xr-x 1 root root  311 2008-04-14 01:42 0anacron
   -rwxr-xr-x 1 root root  219 2008-04-14 01:42 apport
   -rwxr-xr-x 1 root root  473 2008-03-30 06:24 find.notslocate
   -rwxr-xr-x 1 root root  473 2008-03-30 06:24 find.notslocate.dpkg-new

# date;ls -lut /etc/cron.daily
   Mon Apr 14 01:48:32 GMT 2008
   total 68
   -rwxr-xr-x 1 root root 1309 2008-04-14 01:45 sysklogd
   -rwxr-xr-x 1 root root  123 2008-04-14 01:45 tripwire
   -rwxr-xr-x 1 root root 3283 2008-04-14 01:45 standard
   -rwxr-xr-x 1 root root  420 2008-04-14 01:45 slocate
   -rwxr-xr-x 1 root root  383 2008-04-14 01:42 samba
   -rwxr-xr-x 1 root root   89 2008-04-14 01:42 logrotate
   -rwxr-xr-x 1 root root  946 2008-04-14 01:42 man-db
   -rwxr-xr-x 1 root root  314 2008-04-14 01:42 aptitude
   -rwxr-xr-x 1 root root  502 2008-04-14 01:42 bsdmainutils
   -rwxr-xr-x 1 root root 4197 2008-04-14 01:42 exim4-base
   -rwxr-xr-x 1 root root 5811 2008-04-14 01:42 apt
   -rwxr-xr-x 1 root root  311 2008-04-14 01:42 0anacron
   -rwxr-xr-x 1 root root  219 2008-04-14 01:42 apport
   -rwxr-xr-x 1 root root  473 2008-03-30 06:24 find.notslocate
   -rwxr-xr-x 1 root root  473 2008-03-30 06:24 find.notslocate.dpkg-new

# mkdir /root/bin/ && cd /root/bin
# echo "date >> /tmp/test" > foo && cat /root/bin/foo
   date >> /tmp/test

# date;sh /root/bin/foo && cat /tmp/test
   Mon Apr 14 01:52:01 GMT 2008
   Mon Apr 14 01:52:01 GMT 2008


Than I put the foo script in my crontab


# crontab -l
   SHELL=/bin/sh
   PATH=/usr/bin:/usr/sbin:/sbin:/bin:/usr/lib/news/bin
   MAILTO=root
   #

   * * * * *    /root/bin/foo 

# date;cat /tmp/test;ls -lut /root/bin/foo
   Mon Apr 14 01:58:15 GMT 2008
   Mon Apr 14 01:52:01 GMT 2008
   -rw-r--r-- 1 root root 17 2008-04-14 01:52 /root/bin/foo


-- Wait a few minutes, and than check again


# date;cat /tmp/test;ls -lut /root/bin/foo
   Mon Apr 14 02:01:53 GMT 2008
   Mon Apr 14 01:52:01 GMT 2008
   -rw-r--r-- 1 root root 17 2008-04-14 01:52 /root/bin/foo

# reboot

# date;cat /tmp/test;ls -lut /root/bin/foo
   Mon Apr 14 02:10:29 GMT 2008
   Mon Apr 14 01:52:01 GMT 2008
   -rw-r--r-- 1 root root 17 2008-04-14 01:52 /root/bin/foo


Is there any reason why my foo script should not be running every minute?

---

### Post by scxtt on 2008-04-13
syntax is wrong ...

*/1 * * * * /root/bin/foo

---

### Post by Helgiks on 2008-04-13
Makes no difference, I have tried it that way too.

---

### Post by scxtt on 2008-04-13
i did a test that way, worked fine -- could be a problem w/ "foo" ... try something simple like:

*/1 * * * * echo "this is a test." 2>&1 >> /home/<user>/test.txt

---

### Post by Helgiks on 2008-04-14
Yes, that worked, and now the foo script is working too, I don't really know what did the trick, it must have been the */1 instead of *, even though I did try that before, well, thanks allot.

---

### Post by scxtt on 2008-04-14
* * * * * <script> doesn't work, that's basically saying "always do this", not "do this every minute" ... you **need** */1 in the 1st position to do it every minute, just how */2 would do it every 2 ... i'm also thinking:

0-59 * * * * <script>

would work ...

---

