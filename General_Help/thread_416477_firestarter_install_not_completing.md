---
title: "firestarter install not completing"
date: 2007-04-21
forum: General Help
---

### Post by pwab on 2007-04-21
Hi,

I have xubuntu 6.10 running on a small machine, acting as a gateway. It connects to my broadband provider using pppoe. I have all of this set up already.

I installed firestarter and noticed that when I clicked on the GUI "Stop" or "Restart" buttons, it would give a uninformative error. I tried to repeat the exercise on the command-line, by:

pieter@xubuntu-server:/etc/apache2$ sudo /etc/init.d/firestarter restart
 * Stopping the Firestarter firewall...
   ...done.
 * Starting the Firestarter firewall...
   ...fail!

I am pretty sure that it is working the way i set it up (even after a 'stop' command was issued). The correct ports are open, and all the others are closed. My DHCP and NAT setup is also working (even after 'stop')

However, and this is my real problem, when i try to use apt-get upgrade, i get the following:

pieter@xubuntu-server:/etc/apache2$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
[COLOR="Red"]1 not fully installed or removed.[/COLOR]
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
[COLOR="Red"]Setting up firestarter (1.0.3-1.2ubuntu3.1) ...
 * Starting the Firestarter firewall...
   ...fail!
invoke-rc.d: initscript firestarter, action "start" failed.
dpkg: error processing firestarter (--configure):
 subprocess post-installation script returned error exit status 200
Errors were encountered while processing:
 firestarter
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/COLOR]

It seems like, even though it is performing the intended function, it did not complete the setup properly, and not dpkg thinks it is in an invalid state.

Anybody has any suggestions?

Regards,
Pieter

---

### Post by heimo on 2007-04-21
Your message so far is:

subject: firestarter install not completing
> **pwab said:**
> Hi,

I have xubuntu

I'd suggest to give more details.

---

