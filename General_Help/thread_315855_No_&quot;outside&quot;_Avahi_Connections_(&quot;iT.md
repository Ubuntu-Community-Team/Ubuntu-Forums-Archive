---
title: "No &quot;outside&quot; Avahi Connections (&quot;iTunes sharing&quot;)"
date: 2006-12-09
forum: General Help
---

### Post by MarkusThielmann on 2006-12-09
I'm experiencing a strange avahi problem.

Today I installed a system with ubuntu-minimal. After that I installed xubuntu-desktop, Rhythmbox, Banshee and Avahi.

The system is running on a network, together with 2 mt-daapd Servers, one Ubuntu Box with working Rythmbox "Music Sharing" plugin (avahi) and a few windows itunes boxes.

Every computer can see every daapd ressource. Except the one I installed today. I can see his shared data from all other PCs, but it can't locate any of the other ressources (via Rhytmbox, Banshee, avahi-browse -a or avahi-discover). By the way: avahi-browse and avahi-discover detecting the services on localhost, but ONLY them. There is no firewall (I can even telnet the mt-daapd port).

I'm really running out of ideas. I even can't find a error message or something that could help.

---

### Post by chalex on 2006-12-09
Does Avahi need any configuration after install?  Do you have mDNS running (package nss-mdns maybe)?

---

### Post by MarkusThielmann on 2006-12-09
> **chalex said:**
> Does Avahi need any configuration after install?  Do you have mDNS running (package nss-mdns maybe)?

I just changed AVAHI_DAEMON_START=0 to =1 in/etc/default/avahi-daemon, as I found this information somewhere on the net. I'm not sure If I need a running daemon for accessing shares.

libnss-mdns and mdns-scan are installed on both (x)ubuntu computers.

---

### Post by chalex on 2006-12-10
You could also look through /usr/share/doc/package_name for any additional setup instructions. Look for something like README.Debian

---

### Post by MarkusThielmann on 2006-12-11
It's a known bug:

[https://bugs.launchpad.net/distros/ubuntu/+source/avahi/+bug/72728](https://bugs.launchpad.net/distros/ubuntu/+source/avahi/+bug/72728)
[http://www.avahi.org/ticket/72](http://www.avahi.org/ticket/72)

Hopefully updated soon...

---

