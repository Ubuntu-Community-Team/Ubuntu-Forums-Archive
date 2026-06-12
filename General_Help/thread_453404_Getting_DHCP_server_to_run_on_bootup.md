---
title: "Getting DHCP server to run on bootup"
date: 2007-05-24
forum: General Help
---

### Post by Stolly on 2007-05-24
Hi,

A predecessor setup a Ubuntu VM to run a DHCP service to serve a wireless network.

Works fine, but the DHCP doesn't start up when the VM is booted. 

I looked in 

/etc/rc5.d

and see this

S40dhcp3-server -> ../init.d/dhcp3-server

As far as i can see, this should start the DHCP server.  But it doesn't happen.

What can i check next ?

Cheers !

---

### Post by mbradlcu on 2007-05-27
I though Ubuntu default was runlevel 2? but yea that should start it if you're running runlevel 5..

---

