---
title: "service startup after server shutdown and server reboot"
date: 2017-03-08
forum: General Help
---

### Post by leetskil on 2017-03-08
hello

good day

just wanted to ask, how do i setup service startup after server shutdown and server reboot? just letting you know that i'm new to ubuntu.. thank you in advance.

---

### Post by TheFu on 2017-03-08
It depends on the release.

In the old days, we'd use init-scripts.  These are well-documented in almost every Linux/Unix admin book. Pick a book and read.  These scripts are compatible with upstart AND systemd, because so many already exist.  Look in /etc/init.d/ for all the scripts.  These are linked to different "runlevels" with S and K symbolic links.  "S" is startup and "K" is shutdown (really it is kill). These run in order S00 ---> S99 at startup.  For shutdown, they run in reverse order K99--> K00.

I don't know much about systemd yet. Been avoiding it since it showed up in 16.04 (unwanted by me). Believe it does dependency validation and parallel startup of as much as they can.  It doesn't always work as expected for me.  Restarting the network subsystem has never worked on my 16.04 machine, for example.

Ok - a few links that google found: 
* [http://www.tldp.org/HOWTO/HighQuality-Apps-HOWTO/boot.html](http://www.tldp.org/HOWTO/HighQuality-Apps-HOWTO/boot.html)
* [http://upstart.ubuntu.com/cookbook/](http://upstart.ubuntu.com/cookbook/)
* [https://wiki.ubuntu.com/SystemdForUpstartUsers](https://wiki.ubuntu.com/SystemdForUpstartUsers)

Just remember the history -  init.d --> upstart --> systemd

---

### Post by leetskil on 2017-03-08
@TheFu thank you for the brief advice, i will check out the links :KS:)

---

### Post by SeijiSensei on 2017-03-08
Most the time time when you install a server package it sets itself up to start at boot automatically.  What packages are you running that do not start automatically?

---

### Post by leetskil on 2017-03-12
@SeijiSensei have installed nginx, hhvm, mariandb, everytime i boot up or start the virtual server (i'm using hyper-v), it needs to be started up manually.

---

### Post by SeijiSensei on 2017-03-12
I'm surprised that nginx and mariadb did not set themselves up at installation.  Apache and MySQL certainly do.

How you would enable this depends on the distribution you're running.  For versions before 16.04 you can use 
```
sudo update-rc.d servicename enable
```
On 16.04 and later with systemd use
```
sudo systemctl enable servicename.service
```
For the first you'd use something like "sudo update-rc.d nginx enable".  On 16.04 it would be "sudo systemctl enable nginx.service".

---

### Post by TheFu on 2017-03-12
Sometimes for non-default services, there is a setting in /etc/default/ that needs to be changed too.  Don't know about nginx or mariaDB - it has been a while since I setup my systems that use those.  Don't get me wrong, I prefer nginx and mariaDB over the other, well-know, alternatives. Just don't remember how to tell them to start automatically.  Plus, the way to do it is likely different between 14.04 and 16.04. People running servers shouldn't use any other releases at this point.

Google found answers for mariaDB and nginx which backup what SS says above. Those are extremely standard methods, BTW, taught in a beginning admin class. Don't know about the other tools.

---

### Post by kevdog on 2017-03-12
I'm running 16.04 and install nginx from the package manager

The startup script for systemd is located /lib/systemd/system/nginx.service  (You don't need to specifically know this however most of the system installed scripts are located within /lib/systemd/system

nginx.service
```

# Stop dance for nginx
# =======================
#
# ExecStop sends SIGSTOP (graceful stop) to the nginx process.
# If, after 5s (--retry QUIT/5) nginx is still running, systemd takes control
# and sends SIGTERM (fast shutdown) to the main process.
# After another 5s (TimeoutStopSec=5), and if nginx is alive, systemd sends
# SIGKILL to all the remaining processes in the process group (KillMode=mixed).
#
# nginx signals reference doc:
# http://nginx.org/en/docs/control.html
#
[Unit]
Description=A high performance web server and a reverse proxy server
After=network.target

[Service]
Type=forking
PIDFile=/run/nginx.pid
ExecStartPre=/usr/sbin/nginx -t -q -g 'daemon on; master_process on;'
ExecStart=/usr/sbin/nginx -g 'daemon on; master_process on;'
ExecReload=/usr/sbin/nginx -g 'daemon on; master_process on;' -s reload
ExecStop=-/sbin/start-stop-daemon --quiet --stop --retry QUIT/5 --pidfile /run/nginx.pid
TimeoutStopSec=5
KillMode=mixed

[Install]
WantedBy=multi-user.target

```

By convention, if you were writing your own systemd service file --- meaning through a script of if wanting to write a startup or shutdown script these are placed in /etc/systemd/system
Here is an example of a startup systemd script I wrote to turn on the magic packet of the networking card to allow for WOL startups

/etc/systemd/system/wol@.service
```

# Systemd file to turn on Magic Packet on network card
# Could be improved to actually discover the active interface
# If you want to enable wol on  on interface eth0: sudo systemctl enable wol@eth0.service
# 

[Unit]
Description=Wake-on-LAN for %i
Requires=network.target
After=network.target

[Service]
Type=oneshot
ExecStart=/sbin/ethtool -s %i wol g

[Install]
WantedBy=multi-user.target

```

Systemd services are started by:
sudo systemctl start <system name>  ie sudo systemctl start nginx.service

To enable them to start at boot:
sudo systemctl enable <system name> ie sudo systemctl enable nginx.service


References:[https://ubuntuforums.org/showthread.php?t=2339386](https://ubuntuforums.org/showthread.php?t=2339386)

Lastly -- unrelated to this post however honestly the BSD way of how services are started -- everything listed within /etc/rc.conf is by far the easiest way to administer services.  I can not speak about the efficiency of this process or with services that are started asynchronously, however its frankly a lot easier to administer as even compared to systemV init scripts

---

### Post by leetskil on 2017-03-13
@SeijiSensei thank you for the reply i will try it right away..

---

### Post by leetskil on 2017-03-13
@kevdog okay i will try your method, thank you for reply..

---

