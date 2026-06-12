---
title: "its hard to switch wireless networks"
date: 2008-04-11
forum: General Help
---

### Post by zigNzag on 2008-04-11
hi I have to wifi networks around me, Is there a easy way to switch what one i connect to. maybe this is a glitch, but lets say im conected to linksys and want to switch to my home network. Ubuntu will give me 2 options home or linksys. If im connected to linksys and want to connect to home I try to click the home bullet but it rarely fills in and connects to my home wifi net work. So basically its just hard to switch between networks please help

---

### Post by rajj on 2008-04-11
not sure about the best way to achieve this, but here is one way  from cli you can do this:

wireless info is stored in a file called /etc/wpa_supplicant.conf.
You can modify that file to include priority within each setting:
For example:

network={
  ssid="static-wpa-test"
  psk'"test"
**  priority=5**
}

So change the priority value, restart wpa_supplicant daemon and renew your IP.
for example. if your interface is eth1
**stop the process:**
sudo pkill wpa_supplicant
**start it again:**
sudo wpa_supplicant -wB -ieth1 -c/etc/wpa_supplicant.conf
**get an IP address:**
sudo dhclient eth1

So substitute eth1 with whichever interface you are working with.

---

### Post by bluepowder7 on 2008-04-11
are you using the default network manager?  i've hated it and it always had problems switching from wired to wireless or from one wireless to another.  someone told me about WiCD, and i've loved it ever since.  do a google search for it - it should lead you to a download and instructions on sourceforge.

---

### Post by wannadumpwindows on 2008-04-11
Here's the link to WICD on sourceforge:

[http://sourceforge.net/projects/wicd/]("http://sourceforge.net/projects/wicd/")

I've used it for about a year now, on two laptops and I haven't had a single problem. I love it. I like it a lot better than network-manager, I can tell you that for sure!

P.S. There's also a repo around somewhere. I can't remember the address, but if you find and use it, WICD will be updated just like the rest of your software!

---

### Post by zigNzag on 2008-04-11
thanx guys it works fine now wicd pwns

---

