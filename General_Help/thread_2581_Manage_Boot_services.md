---
title: "Manage Boot services"
date: 2004-10-29
forum: General Help
---

### Post by ignitionworks on 2004-10-29
Hello,

I'm trying to turn off some unnecessary boot services for a  faster boot. Also, I may want to add some custon configuration at boot. How do i manage boot services?

i couldn't find chkconfig in the default installation? Is there a GUI screen avilable for this? If not, I could install chkconfig.

Also, I compiled a new kernel 2.6.10-rc1 and I did not enable "tmpfs". On reboot, boot complained about not having tmpfs to create some /dev devices? Is tmpfs used to create /dev? I will try enabling tmpfs this evening and see if this is solved :)

Thanks in advance,

Ignitionworks

---

### Post by scias on 2004-10-29
try ntsysv

---

### Post by kamstrup on 2004-11-03
I possitively see something about mounting a tmpfs on /dev in the beginning of the boot process...

I don't know what ntsysv is but it is not in universe... Anyway I'd rather have the runlevel editor from the Gnome System Tools.

---

### Post by randy on 2004-11-04
Install gnome-system-tools and use that to manage your services on startup.  It can be found under the Computer Menu -> System Configuration -> Services.

---

### Post by v79 on 2004-11-04
[QUOTE=randy]Install gnome-system-tools and use that to manage your services on startup.  It can be found under the Computer Menu -> System Configuration -> Services.[/QUOTE]

Not on my (warty) system. No reference to Services at all, and I do have gnome-system-tools installed. And I also would like to speed up the boot times - it's probably my only major complaint about ubuntu.

v79

---

### Post by Rui Pais on 2004-11-04
gnome-system-tools is reduce to network-admin, time-admin, users-admin. Thereis no longer a service-admin. It's has been removed only in ubuntu or is a gnome 2.8 cleanning? 

I started to use sysv-rc-conf. It runs in a terminal but works great and easy. :-\"  Nice as the gnome equivalent. Some one should do a GUI based on that!

---

### Post by kamstrup on 2004-11-05
There's another thread about this which solves the problem partially: 
[http://www.ubuntuforums.org/showthread.php?t=2216](http://www.ubuntuforums.org/showthread.php?t=2216)

The runlevel- (or service-) editor is not included in Debian or Ubuntu for that matter, and will not be. I posted a request at bugzilla; here's the a link to why this is sadly the case: 
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=271859](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=271859)

---

