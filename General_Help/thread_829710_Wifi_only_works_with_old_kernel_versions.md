---
title: "Wifi only works with old kernel versions"
date: 2008-06-15
forum: General Help
---

### Post by Dragon45 on 2008-06-15
I have several kernel options on the Grub screen: -19, -17, and -14. Wireless internet access only works on the oldest kernel version -14 (and winxp, but i'd rather not mention that ;) ). With -19, it will show it as connected (wireless conn bars appear in the system tray), but it will not actually have the capability to use the connection and can't connect to the internet, download new package/version lists, etc, and shows no signs of life at all.

I'm completely baffled. help?

---

### Post by Dragon45 on 2008-06-15
It seems that drivers for the wireless interface are not recognized under the newer kernel versions; they're listed as Unknown Devices in the network configuration manager.

---

### Post by GenesisV2.0 on 2008-06-16
Have you tried the battleaxe that is ndiswrapper, if by mircale you do get through the endless list of instructions and have a copy of the wireless driver of manufacturers disk then it should work.

---

