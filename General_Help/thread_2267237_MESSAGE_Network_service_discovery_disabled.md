---
title: "MESSAGE: Network service discovery disabled"
date: 2015-02-28
forum: General Help
---

### Post by suomalainen on 2015-02-28
Ubunteros,

Upon boot-up I keep getting the message "Network service discovery disabled- Your current network has a .local domain, which is not recommended and incompatible with the Avahi network service discovery. The service has bee disabled. "

How serious is this?
What is it?
And can something be diabled so message never again pops up?

Thank you

---

### Post by grahammechanical on 2015-02-28
If we disable advisory messages from the operating system there will come a time when we will do serious damage to the OS and then we will complain that the OS did not warn us about the harm we were going to do.

Ubuntu has Network Manager which can automatically make a connection to a router/modem. Sometimes, the connection to the router is made before the router has itself established a connection to the Internet service provider. When that happens we get the message that the discovery service has been disabled.

The Avahi discovery service is there for when we want to connect to other machines in the network. That is the case with the Internet which is a Wide Area Network (WAN). But we may also have a Local Area Network (LAN) and we will need Avahi to discovery the other machine son our LAN.

I get that message every time I load Ubuntu without giving the router time to fully initialise. It does not prevent me from using the computer or from accessing the World Wide Web.

[http://en.wikipedia.org/wiki/Avahi_%28software%29](http://en.wikipedia.org/wiki/Avahi_%28software%29)

Regards.

---

