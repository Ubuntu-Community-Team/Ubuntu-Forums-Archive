---
title: "Firestarter problem."
date: 2005-10-26
forum: General Help
---

### Post by .Danny on 2005-10-26
I've installed firestarter but when I try to start it it's giving me this:

> Failed to start the firewall

The device eth0 is not ready.

Please check your network device settings and make sure your Internet connection is active.

If I try the status thingy..

> danny@Ryiah:~$ sudo /etc/firestarter/firestarter.sh status
External network device eth0 is not ready. Aborting..


I'm running a pppoe connection that starts on boot. eth0 is obviously ready and running since I'm here posting this and on irc etc.

What could be the problem? :confused:

---

### Post by .Danny on 2005-10-27
Hmm bump?:(

---

### Post by hmgp on 2005-10-27
Are you sure your connection is eth0?

First time you run firestarter you need to give the network interface.

I'm also in a pppoe ADSL connection, but my network interface is ppp0.

---

### Post by .Danny on 2005-10-28
Ah thanks that did the trick. I just assumed its eth0 since that was what i was selecting in pppoeconf. Thanks.;)

---

