---
title: "How to manage /etc/rc.d files in Ubuntu?"
date: 2007-02-19
forum: General Help
---

### Post by CaptSaltyJack on 2007-02-19
In Kubuntu, there's the very cool "System Services" that provides a nice GUI to not only stop/start services, but also disable/enable them during system boot.

Stopping/starting services in a shell is easy, I know how to do that part.. (/etc/init.d/servicename start/stop/restart).  But looking around in the /etc/rc?.d directories.. yikes, what a mess.  Why does everything start with S10, S13, K19, etc??  Why is apache2 in several directories?  When GUI apps disable a service.. what exactly are they doing to disable them?

Basically, I like Ubuntu but rcconf is blah..and the "bum" app is horrible.  How do you manage the rc.d files in Ubuntu?  In Kubuntu it's a snap.. but Ubuntu.. ?

---

### Post by dcstar on 2007-02-21
> **CaptSaltyJack said:**
> In Kubuntu, there's the very cool "System Services" that provides a nice GUI to not only stop/start services, but also disable/enable them during system boot.

Stopping/starting services in a shell is easy, I know how to do that part.. (/etc/init.d/servicename start/stop/restart).  But looking around in the /etc/rc?.d directories.. yikes, what a mess.  Why does everything start with S10, S13, K19, etc??  Why is apache2 in several directories?  When GUI apps disable a service.. what exactly are they doing to disable them?

Basically, I like Ubuntu but rcconf is blah..and the "bum" app is horrible.  How do you manage the rc.d files in Ubuntu?  In Kubuntu it's a snap.. but Ubuntu.. ?

I seem to recall a package called something like **sysvconf** (or something similar), it runs in a terminal but it is quite nifty.

As far as asking why things are as they are, you better search out the expansive explanations on the run level structure yourself.........

---

### Post by kerry_s on 2007-02-21
Well if your going through the trouble of stopping them, you might as well just uninstall the services you don't need. I will often just create a folder i name off and drop what i don't want in it, after uninstalling what i don't want. Some are not safe to uninstall.

---

### Post by CaptSaltyJack on 2007-02-21
I got it under control, sysv-rc-conf does the trick well enough.

---

