---
title: "Run at startup"
date: 2014-12-05
forum: General Help
---

### Post by Luft on 2014-12-05
I use an Ubuntu server connected to the internet via a DSL connection.  My ISP uses DHCP so my IP frequently changes.  I use a DNS service called NoIP that allows me to run software on my server that periodically checks for a changed IP address and updates my DNS automatically.

I need that software to start automatically when my server is rebooted.  How can I do this with Ubuntu 14.04?

Thank you.

---

### Post by mevsthevoices2 on 2014-12-05
Check out
```

man init
man update-rc.d
less /etc/init.d/README
```

create a script inside of init.d that conforms to the description given in the README file, make it executable, and add it to start up using 
```
update-rc.d SERVICENAME defaults
```
or some other settings to describe where during startup the script will be called. Many of the scripts rely on 
```
start-stop-daemon --start/--stop
```
which allows alot of fine detail in how, where, and who by the process will be launched

---

### Post by nerdtron on 2014-12-05
Is there a command (like a single line?) that you use to run the program you need?

You can put in the /etc/rc.local

---

### Post by ian-weisser on 2014-12-05
You can do it with an @reboot cron job.
You can do it with an etc/init.d script.
You can do it with an Upstart job (my favorite). Soon to be changed to a systemd job.
You can do it with a dbus service.
You can do it with an ifup hook script.
You can do it all kinds of ways.

The appropriate way will depend on the services that must be available when your software runs, how you intend to monitor that software or it's output, whether or not a human needs to be logged in, and how you intend to maintain it.

---

