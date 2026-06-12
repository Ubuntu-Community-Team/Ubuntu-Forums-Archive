---
title: "How do I create a service to run my server code?"
date: 2008-07-07
forum: General Help
---

### Post by necromantula on 2008-07-07
I have two server programs, both basic CLI programs, and I want them to run as services, similar to mysqld or apache. How can I get them to run on startup as a service, and auto-restart if they close?

I am running 8.04, the latest release, with all current updates. No major modifications, other than removal of some things to run faster

---

### Post by bodhi.zazen on 2008-07-07
It is very straight forward.

You can add the commands to /etc/rc.local

Or if you want to start a service, add it to /etc/init.d and link (or update-rc.d , but these are all links to /etc/init.d and upstart is getting away from runlevels).

[https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto)

---

