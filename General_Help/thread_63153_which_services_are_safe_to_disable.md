---
title: "which services are safe to disable?"
date: 2005-09-07
forum: General Help
---

### Post by glandula on 2005-09-07
when i used xp i used this service guide to decide what could be disabled [http://www.blackviper.com/WinXP/servicecfg.htm](http://www.blackviper.com/WinXP/servicecfg.htm)

is there a similar guide for ubuntu somewhere ? what is safe to disable?

---

### Post by djib on 2005-09-07
[QUOTE=glandula]when i used xp i used this service guide to decide what could be disabled [http://www.blackviper.com/WinXP/servicecfg.htm](http://www.blackviper.com/WinXP/servicecfg.htm)

is there a similar guide for ubuntu somewhere ? what is safe to disable?[/QUOTE]
 Hello,
I don't know any such thing for ubuntu but I think there are no 'extra' services in ubuntu that you should disable.
If you want to try and disable some services you can go in /etc/init.d and prevent the service you want from beeing executed (chmod o-x networking for example).

---

### Post by John.Michael.Kane on 2005-09-07
[http://www.marzocca.net/linux/bum.html](http://www.marzocca.net/linux/bum.html) this will show you what services are installed. after you have a determand which ones you dont need, use synaptic to uninstall them. you can also use synaptic to remove any programs that you dont need as well..

hope this helps

---

### Post by skoal on 2005-09-07
Good info Plisken.  Here's what my runlevel looks like, which works quite well for the average desktop:

skoal@morpheus://~ $ ls /etc/rc5.d/
K11anacron   S11klogd   S20acpid   S20makedev  S99rmnologin
S05vbesave   S12alsa    S20dbus-1  S20rsync    S99stop-bootlogd
S10sysklogd  S19cupsys  S20inetd   S21kdm

NOTE: substitute S21kdm with S2?gdm (for Gnome) and most who use Nvidia will probably have S??nvidia-glx in there (but I use the Nvidia binary installer, not the deb).

That's pretty slim pickens there (and almost the bare minimum).  I really don't use the acpi features (S20acpid), so I could stop that daemon as well.  I could also remove S20rsync since I don't use this linux box for transfering across network shares.  

That basically gives me sound, video, and printer support.  If you're going to experiment with these services, modify run levels 3-5 (not 2), and make the appropriate change in /etc/inittab to use that custom run level.  Leave run level 2 intact at it's default settings...

\\//_

---

