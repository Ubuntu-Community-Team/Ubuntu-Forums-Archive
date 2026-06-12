---
title: "Canon LBP7010C installation problem"
date: 2016-11-15
forum: General Help
---

### Post by sefayalvac on 2016-11-15
Hello all,
I want to install my printer (Canon LBP7010C) to my ubuntu 15.10. I have tried everything, but I couldn't install it. I have applied the installation procedure in the following link:
[http://askubuntu.com/questions/105891/how-to-make-lbp-1120-canon-printer-work](http://askubuntu.com/questions/105891/how-to-make-lbp-1120-canon-printer-work)

When I check the ccpd status with "sudo /etc/init.d/ccpd status", I get:
/usr/sbin/ccpd: 3327 3310

but I cant print anaything yet. I paste my error_log here:
```
 [15/Nov/2016:21:59:32 +0200] [Job 37] ccp send_data error, exit
E [15/Nov/2016:21:59:37 +0200] [Job 38] Unable to send data to printer.
W [15/Nov/2016:22:14:32 +0200] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'LBP7010C-7018C-Gray..' already exists
W [15/Nov/2016:22:14:32 +0200] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'LBP7010C-7018C-RGB..' already exists
W [15/Nov/2016:22:15:08 +0200] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'sefa-Gray..' already exists
W [15/Nov/2016:22:15:08 +0200] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'sefa-RGB..' already exists
E [15/Nov/2016:22:17:14 +0200] [Job 39] ccp send_data error, exit
W [15/Nov/2016:22:17:14 +0200] Notifier for subscription 86 (dbus://) went away, retrying!
W [15/Nov/2016:22:17:14 +0200] Notifier for subscription 107 (dbus://) went away, retrying!
W [15/Nov/2016:22:17:14 +0200] Notifier for subscription 126 (dbus://) went away, retrying!
W [15/Nov/2016:22:17:14 +0200] Notifier for subscription 142 (dbus://) went away, retrying!
W [15/Nov/2016:22:17:14 +0200] Notifier for subscription 148 (dbus://) went away, retrying!
W [15/Nov/2016:22:17:14 +0200] Notifier for subscription 151 (dbus://) went away, retrying!
W [15/Nov/2016:22:17:14 +0200] Notifier for subscription 162 (dbus://) went away, retrying!
W [15/Nov/2016:22:17:14 +0200] Notifier for subscription 163 (dbus://) went away, retrying!
W [15/Nov/2016:22:17:14 +0200] Notifier for subscription 175 (dbus://) went away, retrying!
W [15/Nov/2016:22:17:14 +0200] Notifier for subscription 176 (dbus://) went away, retrying!
E [15/Nov/2016:22:17:20 +0200] [Job 39] ccp send_data error, exit
W [15/Nov/2016:22:20:03 +0200] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'LBP7010C-7018C-Gray..' already exists
W [15/Nov/2016:22:20:03 +0200] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'LBP7010C-7018C-RGB..' already exists
W [15/Nov/2016:22:21:23 +0200] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'sefa-Gray..' already exists
W [15/Nov/2016:22:21:23 +0200] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'sefa-RGB..' already exists
E [15/Nov/2016:22:21:47 +0200] [Job 40] ccp send_data error, exit
```

Thank you,

---

### Post by sefayalvac on 2016-11-16
I get this error from syslog
<code>
Nov 16 17:06:36 hermes kernel: [ 1559.892620] c3pldrv[3192]: segfault at 0 ip           (null) sp 00000000ffab590c error 14 in c3pldrv[8048000+13000]
Nov 16 17:06:38 hermes kernel: [ 1562.046962] c3pldrv[3217]: segfault at 0 ip           (null) sp 00000000ffba93cc error 14 in c3pldrv[8048000+13000]
</code>

---

