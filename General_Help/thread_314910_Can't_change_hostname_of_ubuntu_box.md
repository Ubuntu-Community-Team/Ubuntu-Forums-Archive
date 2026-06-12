---
title: "Can't change hostname of ubuntu box"
date: 2006-12-08
forum: General Help
---

### Post by smith.norton on 2006-12-08
I am running Ubuntu 6.06 LTS. I try to change the name of my PC using 'hostname -v newname' (after logging into gnome and opening a terminal). But this change of name is only temporary. As soon as I restart my PC, what I find is again the old name that I specified during installation.

Can anyone suggest what's wrong?

---

### Post by brt on 2006-12-08
have a look at /etc/hostname

---

### Post by esaym on 2006-12-08
I got a similar question

How do I change the name that is shown on the DHCP Clients list on my router:

[[img]http://la.gg/thmb/snapshot3_1.png[/img]]("http://la.gg/v/snapshot3_1.png")

Im the "*"

:confused:

---

### Post by taurus on 2006-12-08
If you decide to change your /etc/hostname, you _better_ change /etc/hosts to the same name or you won't be able to use sudo and some of the network apps will not work...

Applications -> Accessories -> Terminal
```
gksudo gedit  /etc/hostname  /etc/hosts
```

---

### Post by brt on 2006-12-08
maybe this will help you:

[http://www.geocities.com/rlcomp_1999/hostname.html](http://www.geocities.com/rlcomp_1999/hostname.html)

---

### Post by bodhi.zazen on 2006-12-08
[http://ubuntuforums.org/showthread.php?&t=255322](http://ubuntuforums.org/showthread.php?&t=255322)

---

### Post by Iowan on 2006-12-08
> **esaym said:**
> How do I change the name that is shown on the DHCP Clients list on my router:
Edit **/etc/dhcp3/dhclient.conf** 
Find the line similar to:
```
send host-name "myhostname";
```
Replace **myhostname** with your host name.
Don't forget to uncomment the line (remove the "#").

---

### Post by esaym on 2006-12-09
> **Iowan said:**
> Edit **/etc/dhcp3/dhclient.conf** 
Find the line similar to:
```
send host-name "myhostname";
```
Replace **myhostname** with your host name.
Don't forget to uncomment the line (remove the "#").
Thanks!

---

