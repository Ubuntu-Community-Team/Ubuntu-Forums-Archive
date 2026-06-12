---
title: "Argh! Ubuntu keeps logging me out..."
date: 2008-06-09
forum: General Help
---

### Post by tom66 on 2008-06-09
Ubuntu keeps logging me out on stand by. Whenever I close the lid of my laptop, as soon as I resume, I am logged out. Sometimes, I am kept logged in, sometimes not. 

This is really annoying, so if I could get a solution it would be nice.

---

### Post by jimmy the saint on 2008-06-09
System>Preferences>Power Management  and adjust the "when laptop is closed" options

---

### Post by tom66 on 2008-06-09
Both are set to 'Suspend'. 

Here's a copy of my /var/log/auth.log system log, it occasionally seems to be logging me out. 

```

Jun  9 07:39:51 mars gdm[21698]: pam_unix(gdm:session): session closed for user thomas
Jun  9 07:40:10 mars gdm[28453]: pam_unix(gdm:session): session opened for user thomas by (uid=0)
Jun  9 08:00:29 mars gdm[28453]: pam_unix(gdm:session): session closed for user thomas
Jun  9 08:00:44 mars gdm[29705]: pam_unix(gdm:session): session opened for user thomas by (uid=0)
Jun  9 08:01:03 mars gdm[29705]: pam_unix(gdm:session): session closed for user thomas
Jun  9 08:06:54 mars gdm[5311]: pam_unix(gdm:session): session opened for user thomas by (uid=0)
Jun  9 08:12:13 mars sudo:     root : TTY=unknown ; PWD=/ ; USER=thomas ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/use_http_proxy
Jun  9 08:12:13 mars sudo: pam_unix(sudo:session): session opened for user thomas by (uid=0)
Jun  9 08:12:13 mars sudo: pam_unix(sudo:session): session closed for user thomas
Jun  9 08:12:14 mars sudo:     root : TTY=unknown ; PWD=/ ; USER=thomas ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/host
Jun  9 08:12:14 mars sudo: pam_unix(sudo:session): session opened for user thomas by (uid=0)
Jun  9 08:12:14 mars sudo: pam_unix(sudo:session): session closed for user thomas
Jun  9 08:12:14 mars sudo:     root : TTY=unknown ; PWD=/ ; USER=thomas ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/port
Jun  9 08:12:14 mars sudo: pam_unix(sudo:session): session opened for user thomas by (uid=0)
Jun  9 08:12:14 mars sudo: pam_unix(sudo:session): session closed for user thomas
Jun  9 08:17:02 mars CRON[6536]: pam_unix(cron:session): session opened for user root by (uid=0)
Jun  9 08:17:02 mars CRON[6536]: pam_unix(cron:session): session closed for user root
Jun  9 08:41:39 mars gdm[5311]: pam_unix(gdm:session): session closed for user thomas
Jun  9 08:41:57 mars gdm[8596]: pam_unix(gdm:session): session opened for user thomas by (uid=0)
Jun  9 09:17:02 mars CRON[10396]: pam_unix(cron:session): session opened for user root by (uid=0)
Jun  9 09:17:02 mars CRON[10396]: pam_unix(cron:session): session closed for user root
Jun  9 10:17:01 mars CRON[12419]: pam_unix(cron:session): session opened for user root by (uid=0)
Jun  9 10:17:01 mars CRON[12419]: pam_unix(cron:session): session closed for user root
Jun  9 10:39:24 mars gdm[5301]: pam_unix(gdm:session): session opened for user thomas by (uid=0)
Jun  9 11:17:01 mars CRON[7990]: pam_unix(cron:session): session opened for user root by (uid=0)
Jun  9 11:17:01 mars CRON[7990]: pam_unix(cron:session): session closed for user root
Jun  9 12:17:02 mars CRON[9936]: pam_unix(cron:session): session opened for user root by (uid=0)
Jun  9 12:17:02 mars CRON[9936]: pam_unix(cron:session): session closed for user root
Jun  9 13:17:02 mars CRON[11981]: pam_unix(cron:session): session opened for user root by (uid=0)
Jun  9 13:17:02 mars CRON[11981]: pam_unix(cron:session): session closed for user root
Jun  9 13:21:14 mars sudo:   thomas : TTY=unknown ; PWD=/home/thomas ; USER=root ; COMMAND=/usr/sbin/gdmsetup
Jun  9 13:21:14 mars sudo: pam_unix(sudo:session): session opened for user root by (uid=0)
Jun  9 13:21:14 mars sudo: pam_unix(sudo:session): session closed for user root
Jun  9 13:22:27 mars polkit-grant-helper[12232]: granted authorization for org.freedesktop.systemtoolsbackends.set to pid 12192 [uid=1000] [auth=thomas]
Jun  9 14:16:14 mars gdm[5301]: pam_unix(gdm:session): session closed for user thomas
Jun  9 14:16:40 mars gdm[12618]: pam_unix(gdm:session): session opened for user thomas by (uid=0)
Jun  9 14:17:04 mars CRON[13142]: pam_unix(cron:session): session opened for user root by (uid=0)
Jun  9 14:17:04 mars CRON[13142]: pam_unix(cron:session): session closed for user root
Jun  9 14:17:42 mars gdm[12618]: pam_unix(gdm:session): session closed for user thomas
Jun  9 14:17:55 mars gdm[13398]: pam_unix(gdm:session): session opened for user thomas by (uid=0)
Jun  9 14:19:29 mars sudo:   thomas : TTY=unknown ; PWD=/home/thomas ; USER=root ; COMMAND=/usr/sbin/gdmsetup
Jun  9 14:19:29 mars sudo: pam_unix(sudo:session): session opened for user root by (uid=0)
Jun  9 14:19:29 mars sudo: pam_unix(sudo:session): session closed for user root
Jun  9 14:57:32 mars gnome-screensaver-dialog: gkr-pam: unlocked 'login' keyring
Jun  9 15:27:52 mars gdm[13398]: pam_unix(gdm:session): session closed for user thomas
Jun  9 15:28:05 mars gdm[15452]: pam_unix(gdm:session): session opened for user thomas by (uid=0)

```

From my futile analysis, it seems that when it resumes it ends my session - but only occasionally...

Thanks!

---

### Post by tom66 on 2008-06-09
Bump!

---

### Post by mempman on 2008-06-09
what does your /etc/default/acpi-support file say?  Specifically, the following section:

# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES="mysql "

---

