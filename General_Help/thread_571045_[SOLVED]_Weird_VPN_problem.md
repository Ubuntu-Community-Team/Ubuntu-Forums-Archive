---
title: "[SOLVED] Weird VPN problem"
date: 2007-10-08
forum: General Help
---

### Post by jfrorie on 2007-10-08
Fiesty Gnome.  HP zd8000 laptop.  Wireless (No cable attached) Using the network manager applet.  I try to create a new OpenVPN connection. OpenVPN is installed as checked by apt-get.

openvpn is already the newest version.
openvpn set to manual installed.

On the page "Create Connection 2 of 2",  the forward button NEVER is enabled.  I have tried every possible combination, Pre-shared Keys (What I am trying to create), x509, password, etc.  I fill in EVERY field, even checked all the boxes on the optional tab.  I cannot make the form enable the forward button.  

Any ideas?  Is there some Validation that I am missing?  Is this something related to the fact that I am wireless with the cable unplugged?


Thanks!

---

### Post by jfrorie on 2007-10-09
Solved.

I'm a bit of an idiot.  

Apparently all the options under OpenVPN require at least one parameter that is pulled from a file.  Instead of selecting a file for the Pre-Shared key entry field, I simply typed in the key.  It appears that for all instanced you must create a text file with the PSK as an entry.

---

