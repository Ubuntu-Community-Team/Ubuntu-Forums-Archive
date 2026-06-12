---
title: "Adding New upstart Services"
date: 2013-09-19
forum: General Help
---

### Post by bhima-pandava on 2013-09-19
I've got a small collection of executables which need to be started at boot, as an unprivileged user, and then need a little clean up during shutdown.  As far I can determine this is something which should be done using upstart these days.  Unfortunately I've been having problems. No matter how I format the new conf file, initctl check-config returns "Invalid job class".

My current new-service.conf reads like this:

```

start on filesystem or runlevel [2345]
stop on run level [016]
task
exec /etc/local/my_service/bin/broker -n -L100 -l/var/log/my_service/broker.log
```

The things I've been confused about, besides the cryptic output of initctl check-config, are how to execute the job as an unpriveldged user and how to deal with spaces in the arguments.  I had broken them all out using env variables... but abandoned them when I couldn't get initctl check-config to accept the script.

Cheers!

---

