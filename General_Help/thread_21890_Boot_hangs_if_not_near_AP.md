---
title: "Boot hangs if not near AP"
date: 2005-03-24
forum: General Help
---

### Post by Polymira on 2005-03-24
Ok, I have 2 wifi cards for my laptop, one onboard minipci card that I have to use ndiswrapper for, and a pcmcia neetgear WG511 (for rfmon support). Now, if either hardware are present at boot (and the mpci onboard always is), if it can't find my network ... it hangs for like 3 minutes, which is total crap. I know I can't be the only one with this issue, so would anyone else out there like to show me a fix or something of the sort? To me, I would think it should do this in the background, so it would continue booting while searching =/

---

### Post by bnutting on 2005-03-24
You could always hit <CTRL>+C to skip the network when it starts to hang.

---

### Post by Steel3 on 2005-03-24
I once installed Ubuntu (warty) on a computer with a wireless card during the first install, and after that every time I removed the wireless card it wouldn't boot and hang permanently when it tried to find the network.

---

### Post by alastair on 2005-03-24
It's hard to know what the right thing to do is sometimes. After all, other services might depend on a network address. Perhaps your home directory is an NFS mount? etc.

This sounds like it /might/ be DHCP taking its time to timeout. If you are using "dhclient", you could try changing (or adding) a timeout parameter to the dhclient .conf file  -perhaps :

/etc/dhcp3/dhclient.conf

see : man dhclient.conf

---

