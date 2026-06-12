---
title: "Installing Network/Video Card Drivers"
date: 2013-09-13
forum: General Help
---

### Post by TauntzE on 2013-09-13
I'm completely new to Ubuntu as of now. I installed 13.04 onto one of my hard drives and I'm having issues trying to install the drivers for my network adapter and my graphics card.
I have NVIDIA GT520 and a Netgear WNDA3100v2. I've got the .run file for the graphics drivers but whenever I run it I get an error message saying I'm on X server. For the adapter I thought I might be able to run the exe through wine but I've read that won't help install the drivers. I don't have any access to internet on that HD so I need to boot onto my other and copy the files I need on it to USB and put it onto there. 
Any help would be appreciated. ;)

EDIT: I've been installing the drivers for the wrong adapter this whole time. I have a FR-300USB and will try installing the drivers from that using ndis. Will update. Still having issues with very slow performance though.

---

### Post by Yellow Pasque on 2013-09-13
Delete the .run file. There's no need to build your own packages (or worse, install without using a package).
[http://www.psychocats.net/ubuntu/drivers](http://www.psychocats.net/ubuntu/drivers)

---

### Post by TauntzE on 2013-09-13
> **Temüjin said:**
> Delete the .run file. There's no need to build your own packages (or worse, install without using a package).
[http://www.psychocats.net/ubuntu/drivers](http://www.psychocats.net/ubuntu/drivers)
I have no access to the internet, so that won't work. I'm looking for a manual method. 
I've installed the NVIDIA drivers so that's no longer an issue. I thought it would help the lag on the system but it didn't. I was using the[COLOR=#000000] Gallium llvmpipe drivers and read that they give slow performance. 
It was running fine on one of the boots but no dice so far. I also tried installing the driver using ndiswapper but to no avail. [/COLOR]

---

