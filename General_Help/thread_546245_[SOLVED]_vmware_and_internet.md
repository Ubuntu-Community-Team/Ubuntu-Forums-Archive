---
title: "[SOLVED] vmware and internet"
date: 2007-09-08
forum: General Help
---

### Post by uroskriznar on 2007-09-08
My native system is Ubuntu. Now I also installed windows xp in vmware, but internet is not working. Internet is working fine in ubuntu. Does anyone know, what could be the problem?

---

### Post by bogdan_5844 on 2007-09-08
you could ease your way by using InnoTek VirtualBox,simply install the VirtualBox Addons and you have internet,audio and video drivers right there
if you want to use VMWare,sorry,i can't help :(

---

### Post by niki001 on 2007-09-08
check this out in vmware workstation, go to 'Virtual machine settings', tab 'hardware'.
See if 'connect at power on' is choosen and in network connection choose option 'NAT: Used to share the hosts IP address'.
Save the settings and try again. Hopefully this works for you

greetz niki

---

### Post by PilotJLR on 2007-09-08
If NAT or Bridged mode doesn't work, see if the Windows guest has any interfaces under "Network Connections"... there should be at least 1 there.
Either way, be sure to install VMware Tools and reboot the Windows guest!

I think, but am not sure, that you need Tools installed for XP to use its virtual NIC.

---

### Post by uroskriznar on 2007-09-08
Thanks guys. I changed from bridged to NAT and now it seems to work :-)))

---

