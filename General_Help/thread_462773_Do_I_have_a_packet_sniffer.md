---
title: "Do I have a packet sniffer?"
date: 2007-06-03
forum: General Help
---

### Post by zodmaner on 2007-06-03
Recently I downloaded and run chkrootkit and got this result:

> 
...
Checking `sniffer'... lo: not promisc and no packet sniffer sockets
eth1: PACKET SNIFFER(/sbin/dhclient3[4866])
eth0:avahi: PACKET SNIFFER(/sbin/dhclient3[5474], /usr/sbin/avahi-autoipd[5313])
...


What does this result mean? Do I have a packet sniffer on my machine?

I also got this message:

> 
...
Searching for OBSD rk v1... /usr/lib/security
/usr/lib/security/classpath.security
...


What does it mean?

---

### Post by RHTopics on 2007-06-03
Both "dhclient" and "avahi-autopid" are part of the standard Ubuntu 7.04 installation.

dhclient is the dynamic host configuration protocol client which provides the automatic assignment of an IP address to your computer from an available DHCP server.  Definitely need this unless you have your computer setup to exclusively use a static IP address.

avahi on the other hand is something that I have been wondering about.  Not such much as a security threat, but is it taking up resources without doing anything useful.

---

### Post by zodmaner on 2007-06-03
Thanks! :) So it seems that I have nothing to worry about, right?

BTW, where can I find out more information about services that are running in the background?

---

### Post by RHTopics on 2007-06-03
From the messages you received from chkrootkit, I don't think you do.  If have you have always just used the Ubuntu repositories, then it would be highly unlikely you have a rootkit problem.

Both, dhclient3 (dchp3-client) and avahi-autopid are packages that can be reinstalled, if doing so would ease your concern.

Not certain from your question whether you want to know more about a specific service or process.  Or you want to identify all services running on your computer.

To see a display of all services and processes, from the Menu bar click System -> Administration -> System Monitor.  Click the Processes tab.  From the System Monitor menu bar, click View, click All Processes.

To learn more about a specific service or process, you can open a Terminal window and then type: man "name of service" (ex. man acpid).

---

### Post by zodmaner on 2007-06-03
> 
To see a display of all services and processes, from the Menu bar click System -> Administration -> System Monitor. Click the Processes tab. From the System Monitor menu bar, click View, click All Processes.

To learn more about a specific service or process, you can open a Terminal window and then type: man "name of service" (ex. man acpid).


Thanks, that is what I have been looking for. Sorry for not being clear, I want to know more about a specific service or process (to understand what it does) and also want to identify all services that are currently running on my computer.

Aside from Ubuntu repositories I also install Affinity and Avant Window Navigator from outside repositories (download.tuxfamily.org/avant), Deluge .deb file from Deluge official website, python-gtkglext1 from glChess website (for 3d support in glChess) and finally easyUbuntu .deb file (with all the codec from Medibuntu repositories).

---

