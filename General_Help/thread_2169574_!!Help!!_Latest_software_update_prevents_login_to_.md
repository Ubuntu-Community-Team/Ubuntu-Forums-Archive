---
title: "!!Help!! Latest software update prevents login to 12.04 LTS - apache2 error loop"
date: 2013-08-22
forum: General Help
---

### Post by bXfnxXr on 2013-08-22
I just installed the latest updates and was asked to restart the computer to complete installation. It loads back to the login screen and I put my password in and it dumps to a black screen with this bit of unhelpfulness:[INDENT]apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
* Stopping save kernal messages
* Starting web server apache2

* Starting anac(h)ronistic cron 

* Stopping anac(h)ronistic cron [/INDENT]

At which point, it dumps back to the login screen where I put my password back in and it loops back to the error. Is there a way to uninstall the latest update or start without apache2 without access to the computer?

---

### Post by bXfnxXr on 2013-08-23
Does anyone have any idea? I ran through the loop several times and an apache call of some kind is pretty constant but the acron one disappeared. I would very much like to go back to work!

---

### Post by steeldriver on 2013-08-23
You can ignore the apache2 error, it's 'normal' for a box that's not in an FQDN environment (like a home LAN for example)

More likely you have issues with your graphics card / driver - you could try booting with 'nomodeset' or into recovery mode - if you can get at least that far then we can try to figure out exactly what

---

### Post by bXfnxXr on 2013-08-23
I can get to recovery mode by holding down shift during bootup. I can also access the root command line through the grub menu. This is my school computer on my universities ethernet and does have an absolute domain name. I was using apache to host a server, so there could be something wrong with it, but it is no longer needed so I would like to start by disabling it to see if that fixes the problem. If you have any ideas how I can tackle this issue I would be very grateful.

---

