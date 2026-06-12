---
title: "Need Help Running GCALDaemon"
date: 2007-10-19
forum: General Help
---

### Post by poebae on 2007-10-19
I followed the installation steps at [http://www.terminally-incoherent.com/blog/2007/10/11/howto-two-way-sync-between-kontact-and-gcal/](http://www.terminally-incoherent.com/blog/2007/10/11/howto-two-way-sync-between-kontact-and-gcal/), but when I ran standalone.sh, I got the following output:

```

INFO  | GCALDaemon V1.0 beta 14 starting...
INFO  | RSS/ATOM feed converter enabled.
INFO  | Local time zone is GMT+10:00.
INFO  | HTTP server starting on port 9090...
WARN  | Set the 'http.allowed.hostnames' parameter to limit remote access.
INFO  | HTTP server started successfully.
INFO  | Start listening file /home/grahambae/GCALDaemon/google.ics...
INFO  | File listener started successfully.
INFO  | Offline file synchronization enabled.
INFO  | LDAP server disabled.
INFO  | Gmail notifier disabled.
INFO  | Sendmail service disabled.
INFO  | Mail terminal disabled.
FATAL | Fatal service error!
java.lang.NullPointerException
   at org.gcaldaemon.core.Configurator.manageBackups(Configurator.java:1072)
   at org.gcaldaemon.core.Configurator.getCalendar(Configurator.java:945)
   at org.gcaldaemon.core.file.OfflineFileListener.run(OfflineFileListener.java:60)

```

Can anyone suggest a reason why I might be getting these errors?

---

### Post by drygal on 2007-12-12
Apparently you helped me with the same problem that I got by posting this link above. I followed this:

"... 

Open the /opt/GCALDaemon/conf/gcal-daemon.cfg and add the following line somewhere close to the top:

work.dir=/home/yourusername/.GCALDaemon/

..."

and it solved it.

---

