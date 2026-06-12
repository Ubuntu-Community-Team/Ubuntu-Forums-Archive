---
title: "Autostart service when connected to specific wifi network"
date: 2014-04-19
forum: General Help
---

### Post by boczan-tamas on 2014-04-19
Hi,
I'm looking for a way to automatically start a service when a wifi connection is established, but only if the wifi SSID is my home network's SSID. (More specifically I'm trying to automatically start a DLNA service at home, but not anywhere else.)
I know I can add a startup condition to a script placed in /etc/init using Ubuntu's upstart feature, so it will start on started networking, but this way it will start everywhere. How can I solve this?

Thanks.

---

### Post by ian-weisser on 2014-04-21
Upstart won't test for the correct network for you.
Upstart should trigger your script or application, and *that* should test for the network.

A script can easily test for the SSID or router's MAC using the 'ip' or 'iwconfig' commands, or by querying dbus ([example]("http://cheesehead-techblog.blogspot.com/2012/09/dbus-tutorial-fun-with-network-manager.html")).

It's possible to use a second upstart job to do the test, but it may be harder for you to maintain and troubleshoot.

Don't forget to stop your DLNA service upon disconnect.

---

### Post by boczan-tamas on 2014-04-26
Thank you, this solved my problem.

---

