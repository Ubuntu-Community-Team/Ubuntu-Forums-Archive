---
title: "Change Router Mac Address Permanently"
date: 2023-10-07
forum: General Help
---

### Post by jaggifzr on 2023-10-07
Hello experts i want to change Mac address of wifi router(labled on back side of router) i want to change it permanently ) i have rooted phone also and i ahve laptop also i want a little help is anybody help me i really need it . im searching from last many days on internet
Thanks in Advance

---

### Post by MAFoElffen on 2023-10-08
LOL.

You cannot change the "permanent" mac address of a network device. It is burned into the permanent registers of the hardware. For the router, it is in the mainboard. To change the mac address of it, you would have to replace the mainboard. In the laptop, you would have to change the wireless board to change it's mac address and the mainboard to change its Wired NIC's mac address. The phone has a permanent Mac address and a permanent IMIE number... 

The prefix (first half) of the mac address is the OUI of the vendor of the chipset. The suffix is unique to the device itself.

(That is also how legal organizations can track a device down.)

You can spoof it or clone it, but you can not change the original address. That brings up something a but different... 

"Some Routers", in the setup menu, advanced settings, if they have the ability to change the MAC address, that is where that setting can be changed, but it really does not change the original embedded address... It is called "mac address cloning". Where it uses what you change it to in the packets. Not all routers have that feature. 

Phones and laptops do not have that feature. So with them, you can spoof the address.

But--- Spoofing and Cloning are not considered as, by your wording, meant or referred to as being "permanent."

---

### Post by ActionParsnip on 2023-10-08
Is the router Ubuntu based.....? How is this related to Ubuntu?

---

### Post by guiverc on 2023-10-08
Question also asked at [https://www.linux.org/threads/change-mac-address.47024/](https://www.linux.org/threads/change-mac-address.47024/)

---

### Post by MAFoElffen on 2023-10-08
"Maybe" he ties that in, when at the end he mentioned in passing 'a laptop' as one of the devices(???) He did not mention what OS it had. I do wonder about his "intent."

I thought this question should be moved to the Security or Networking section.

Sorry. I did forget my disclaimer: "This is an Ubuntu General Support Section and all questions should relate to support of Ubuntu or it's flavors. There are other sections on the Forum for support of Non-Ubuntu Distro's or for discussions."

---

