---
title: "failed restart/hibernate/shutdown"
date: 2008-04-24
forum: General Help
---

### Post by spamalot on 2008-04-24
hi all,

shutting off my computers stalls midway. here's the last messages shown during the shut off process:

* stopping gnome display manager
* stopping web server apache 2
httpd (no pid file) not runnin
* stopping avahi mDNS/DNS-S Daemon
* stopping DHCP D_bus daemon
* stoppoing console list daemon
* stopping MTA
* stopping firestarter firewall
* stopping MySQL database server
* stopping sys clock
ALSA

any suggestion, please?

---

### Post by Islington on 2008-04-24
this is happening to me as well, I posted a thread about it and noone responded.

---

### Post by spamalot on 2008-04-24
i'm wondering if a recent update might have contributed to this. where's the link to your thread?

---

### Post by Islington on 2008-04-24
[http://ubuntuforums.org/showthread.php?t=765791](http://ubuntuforums.org/showthread.php?t=765791)

---

### Post by Islington on 2008-04-24
Figured it out.

There is some leftover during the update: particularly two packages:

network-manager and network-manager-gnome

uninstall and reinstall these.

BTW netowork manager is needed for internet connection so I highly recommend downloading the two packages seperately to the desktop first.

[http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.6.6-0ubuntu3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.6.6-0ubuntu3_i386.deb)

and [http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_0.6.6-0ubuntu5_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_0.6.6-0ubuntu5_i386.deb)

see if that works.

---

### Post by spamalot on 2008-04-26
by the way, that didnt work for me...still looking. any help would be nice.

---

### Post by spamalot on 2008-06-03
hi all!

sorry to post again on this topic, but my problem is not solved. at the very least, could someone please suggest a way to diagnose the problem so i can narrow my search? 

basically, linux does not shut off property: applications are shut down, but then the screen gets black and nothing happens. i have to unplug the PC and restart...

thanks!

e.

---

### Post by Pjotr123 on 2008-06-03
The operating system itself shuts down as it should, but the hardware is still powered and the hard drive keeps spinning. On my laptop I have the same thing. Not on my desktops.

Strangely enough, Xubuntu 8.04 does shut down properly. Apparently, Xfce performs better than Gnome, in this respect.

Greeting, Pjotr.

---

### Post by spamalot on 2008-06-04
thanks.

would it be advisable that i upgrade to Ubuntu 8.04?

---

### Post by spamalot on 2008-08-18
Hi All,

The above problem is *still* not solved. Please, could someone suggest a way to diagnose the problem?

Thanks!

---

### Post by FLCL on 2008-08-18
Yeah, for a while I had this problem with my first install and then it just stopped. But now it's back again randomly. It just started yesterday. 
After selecting shutdown it goes to black screen listing some items, and below it, it goes on about network manager failed, and stuff. THEN it will shutdown, but whats with that?
Any help?

---

### Post by spamalot on 2008-08-23
Just want to join FLCL in asking for help on this long unresolved topic. Thanks!.

---

