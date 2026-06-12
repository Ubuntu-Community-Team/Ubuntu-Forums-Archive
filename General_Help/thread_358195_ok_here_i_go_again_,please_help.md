---
title: "ok here i go again ,please help"
date: 2007-02-10
forum: General Help
---

### Post by jimbean on 2007-02-10
i`ve installed ubuntu 10 times on 3 different machines
every time i have to disable ipv6 in firefox
to get internet
i believe its my dsl modem
then it takes me about 3 weeks of configuring ubuntu for {synaptic package manager and update manager and add and remove}
i have a paradyne dsl modem
is there a easier way to do this:confused:

---

### Post by gradedcheese on 2007-02-10
easier way to do what?  Please ask a more specific question and we can probably help sort it out.

> 
i`ve installed ubuntu 10 times on 3 different machines


why not install it once?  That would be easier :)

---

### Post by jimbean on 2007-02-10
anyway to config synaptic package manger ,addremove ,
to update
they wont connect

---

### Post by llamakc on 2007-02-10
Are you behind a proxy?

Are you able to get to the WWW and is your only problem Synaptic?

Explain how your machine is connected to the outside: directly to the modem, to a router, to another computer...

---

### Post by gradedcheese on 2007-02-10
Ok.  Do you have internet access in general?  You can use Firefox and the like?

---

### Post by jimbean on 2007-02-10
i have internet i am now using, just this minute on ubuntu 6.10 with firefox
i cannot update any packages in synaptic package manager
or add or remove evolution email or auto update

---

### Post by gradedcheese on 2007-02-10
Alright.  Here's how to disable IPv6 system-wide:

[http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html](http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html)

However if you don't know how to use vi, substitute it for 'gedit' in the commands he has you run.  I suspect that your DSL router indeed doesn't support IPv6

---

### Post by jimbean on 2007-02-10
still working on it
trying and rebooting

---

### Post by llamakc on 2007-02-10
There's no reason to reboot. Just run `sudo /etc/init.d/networking restart`

---

### Post by jimbean on 2007-02-11
ok i used sudo /etc/init.d/networking restart
and this is what i got

 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 3112
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:18:f3:45:19:e5
Sending on   LPF/eth0/00:18:f3:45:19:e5
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 10.0.0.2 port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:18:f3:45:19:e5
Sending on   LPF/eth0/00:18:f3:45:19:e5
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 10.0.0.2
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 10.0.0.2
bound to 10.0.0.4 -- renewal in 1605 seconds.
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.


the gedit that i did on disableing ipv6 did not work
i removed the  line   alias net-pf-10 ipv6
installed line  alias net-pf-10 off
then saved
then rebooted
{did not work}

then i removed   alias net-pf-10 off
then installed   alias net-pf-10 off ipv6
saved the file then rebooted
{did not work}
  
then i installed lines
alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off
#alias net-pf-10 ipv6
saved file and rebooted
{did not work}

any more help is greatly needed thanks in advanced

---

### Post by jimbean on 2007-03-06
ok i figured it out i think
i need to add a search domains address
it works for me

---

### Post by huggies15 on 2007-05-26
hi, i just read through your problems and i am having the same thing...
the only problem is i dont know what u meant by adding a search domain or whatever u did in the end to fix it... it is v. annoying at the moment, i wanna add some games ot this rig :)

cheers,
huggies15

---

