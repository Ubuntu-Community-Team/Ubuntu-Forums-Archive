---
title: "No wireless on a T30 after 8.04 upgrade"
date: 2008-04-24
forum: General Help
---

### Post by cliffdanger on 2008-04-24
Hello there!
I've just upgraded to 8.04 and it seems ubuntu isn't recognizing the fact that I have a wireless card installed. It  worked well under 7.10. Anyone else encounter this problem?
I'm using an IBM t30 Thinkpad
I've looked around and was unable to find any information relating to this issue.
Anything that could help me fix this would be very apreciated.
Thanks
-Ben

---

### Post by Jan Olav Hauge on 2008-05-01
I have the same problem with a brand new installaation

---

### Post by RollingFred on 2008-05-01
Hi There,

Same problem after a brand new install from CD. No dual-boot, full 20GB HD for Ubuntu 8.04.
I cannot see Wireless Network when clicking on the network icon in the toolbar.
Bad chipset?
I see a bug ([104551]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/104551")). Maybe related?

Install on T61 works perfectly.

---

### Post by cliffdanger on 2008-05-06
Hello there everyone! I found a solution to this problem!
the solution is posted here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/220606](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/220606)
And Here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/189398](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/189398)

A quick how to, on how to correct this problem:
Start up a terminal window, In Gnome, go to applications > accessories > terminal
Within the terminal type sudo gedit /lib/modules/2.6.24-16-generic/modules.alias
Within gedit, click find, and search for 

alias aes padlock_aes
comment this section out by placing a # infront of this line.

Now, search for alias aes geode_aes,
again, comment out this section by placing a number # infront of this line.

Finally, save an reboot.
I hope this proved helpful!
Note: This solution isn't mine, it was taken from the two addresses above.

-Ben

---

### Post by lamarcheb on 2008-05-24
Thanks for posting. Rebooting now ...

Working!

* no delays in booting
* sound
* wireless works!

Sadly, this regression is unacceptable. Canonical, where are you on this?

---

### Post by lstrange on 2008-05-25
This fix didn't work for me because I have the High rate wireless LAN Mini PCI card rather than the Cisco.

It is supposed to be supported with hostap but it just doesn't see it.

iwconfig       no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

Anyone else find a solution to this?

---

### Post by lstrange on 2008-05-25
I had installed Ubuntu using Wubi inside windows... so I uninstalled that and installed it from a live cd on its own partition and now Ubuntu sees the wireless card and my network but it is not so far compatible with WPA so I can't jump on... I don't really want to switch to WEP just for one laptop...

---

