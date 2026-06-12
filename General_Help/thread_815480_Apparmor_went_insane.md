---
title: "Apparmor went insane"
date: 2008-06-01
forum: General Help
---

### Post by damatta on 2008-06-01
Hello,

I was trying to customize a profile for transmission using aa-logprof. The problem started on that very moment: it asked me to create a user, even though I hit "N" it would not quit looping. Alright I had given up.
After the last boot I tried to mount my second partition but ubuntu complained about not having the privilege - I then knew something was messed up. To spare you from my misfortune (below), I would like to know how to disable Apparmor framework in Hardy Heron or simply revert it back to default values.
Thanks in advance.

I issued in the terminal: sudo apparmor_status

```
apparmor module is loaded.
18 profiles are loaded.
8 profiles are in enforce mode.
   /bin/ping
   /usr/sbin/cupsd
   /usr/sbin/avahi-daemon
   /usr/lib/firefox-3.0b5/firefox
   /sbin/klogd
   /usr/lib/cups/backend/cups-pdf
   /usr/bin/pidgin
   /sbin/syslogd
10 profiles are in complain mode.
   /usr/sbin/traceroute
   /usr/sbin/mdnsd
   /usr/bin/launchpad-integration
   /usr/sbin/ntpd
   /usr/sbin/identd
   /usr/sbin/nmbd
   /usr/sbin/smbd
   /sbin/syslog-ng
   /bin/dash
   /usr/sbin/nscd
58 processes have profiles defined.
0 processes are in enforce mode :
58 processes are in complain mode.
   null-complain-profile (5412) 
   null-complain-profile (5282) 
   null-complain-profile (5673) 
   null-complain-profile (6092) 
   null-complain-profile (6040) 
   null-complain-profile (5989) 
   null-complain-profile (5966) 
   null-complain-profile (7410) 
   null-complain-profile (5646) 
   null-complain-profile (5713) 
   null-complain-profile (5997) 
   null-complain-profile (5987) 
   null-complain-profile (5958) 
   null-complain-profile (5409)  
0 processes are unconfined but have a profile defined.
```

I know not the meaning of that null-complain-profile but seems to indicate misfunctioning. Possibly a bug?

sudo /etc/init.d/apparmor kill

> Killing AppArmor module - failed, AppArmor is builtin: Failed.
sudo /etc/init.d/apparmor stop
> Unloading AppArmor profiles /sbin/apparmor_parser: Unable to remove "/usr/sbin/traceroute".  Unknown error
/sbin/apparmor_parser: Unable to remove "/usr/sbin/smbd".  Unknown error
/sbin/apparmor_parser: Unable to remove "/usr/sbin/ntpd".  Unknown error
/sbin/apparmor_parser: Unable to remove "/usr/sbin/nscd".  Unknown error
/sbin/apparmor_parser: Unable to remove "/usr/sbin/nmbd".  Unknown error
/sbin/apparmor_parser: Unable to remove "/usr/sbin/mdnsd".  Unknown error
/sbin/apparmor_parser: Unable to remove "/usr/sbin/identd".  Unknown error
/sbin/apparmor_parser: Unable to remove "/usr/sbin/cupsd".  Unknown error
/sbin/apparmor_parser: Unable to remove "/usr/lib/cups/backend/cups-pdf".  Unknown error
/sbin/apparmor_parser: Unable to remove "/usr/sbin/avahi-daemon".  Unknown error
: done.

---

### Post by damatta on 2008-06-01
Alright, it seems that loop in aa-logprof caused all this trouble. Fortunately wiping all the rules and rebooting fixed the problem - apparmor back to normal.

---

