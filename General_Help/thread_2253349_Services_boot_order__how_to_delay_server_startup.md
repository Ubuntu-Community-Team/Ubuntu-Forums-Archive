---
title: "Services boot order : how to delay server startup ?"
date: 2014-11-19
forum: General Help
---

### Post by anglade on 2014-11-19
On (x)ubuntu 14.04.1 : 
I've installed and configures two servers : tftpd-hpa and isc-dhcp-server (useful for my LTSP set up).
Both of them works fine when started manually.
```
service isc-dhcp-server start
``` for instance starts the server that attribute IP adresse to boxes connecting to my network.

I've added to runlevel defaults both services :
```

update-rc.d isc-dhcp-server defaults
update-rc.d tftpd-hpa defaults
```This works fine also. I can see in /var/log/syslog that the system is trying to startup my servers. Nice !

Unfortunately both of them keeps trying to startup BEFORE the networks interfaces are up and running. So they (almost) always fail to start. Also, they get respawned so fast that respawning ends much before the network interfaces are available. 

_I would like to figure out how to modify the standard init scripts so that both of those servers wait much longer before being started. _I'm not sure, but I think at least interface eth1 must be up and running for them to be able to start correctly. 

Any help would be deeply appreciated.

PMA

---

### Post by Lars Noodén on 2014-11-19
I'm not sure the standard init scripts are available any more for most services.  (x)ubuntu 14.04 uses [upstart](http://upstart.ubuntu.com/cookbook/) to manage services.  I see the file */etc/init/tftpd-hpa.conf* has the details for tftpd.  There should be a similar file for dhcpd.  You would need something like this in there:

```

start on (started network-interface
          or started network-manager
          or started networking)

```

or whatever networking 'emits' during startup.

---

### Post by anglade on 2014-11-20
Hi,

Thank you for those advices. 

I was not knowing that ubuntu has two init directory : /etc/init and /etc/init.d And I 'm not sure I've implemented correctly your idea. 
Here is what I did : 
In /etc/init/isc-dhcp-server.conf : 
```

description "ISC DHCP IPv4 server"
author "Stéphane Graber <stgraber@ubuntu.com>"

start on (runlevel [2345]
          and started network-interfaces or started network-manager or started networking)
#start on (started network-interfaces or started network-manager or started networking)
stop on runlevel [!2345]
...

```
And in /etc/init.d/isc-dhcp-server :
```

...
PATH=/sbin:/bin:/usr/sbin:/usr/bin
sleep 10
test -f /usr/sbin/dhcpd || exit 0

DHCPD_DEFAULT="${DHCPD_DEFAULT:-/etc/default/isc-dhcp-server}"
start on (started network-interface or started network-manager or started networking) INTERFACE=eth1

# It is not safe to start if we don't have a default configuration.
...

```

To no avail : my system keeps starting exactly the same way it ever did. 

Am I mistaking somewhere ? 

Regards

PMA

---

### Post by Lars Noodén on 2014-11-20
I'm just trying tftpd but the same should be true for dhcpd.  tftpd works for me with this activation line in /etc/init/tftpd-hpa.conf :

```
 
start on (started networking or started network-interfaces or started network-manager)

```

It also works with this:

```

start on (runlevel [2345] and (started networking or started network-interfaces or started network-manager) )

```

---

