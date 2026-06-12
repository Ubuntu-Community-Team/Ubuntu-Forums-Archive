---
title: "Is useful change the Mac Addrress?"
date: 2017-07-21
forum: General Help
---

### Post by joan_carles2 on 2017-07-21
Hello

Currently I'm changing my Mac Address with Network Manager.

When you visit a website which is the mac address that registers the website that I visit? Registers the mac address of the router or the mac address of my computer?

In case that register the MAC Address of the router... can be changed the Mac address of the router?

Rgds

---

### Post by TheFu on 2017-07-21
MAC is seen only on local LANs or if a client-side program grabs it and provides it to the remote system (rare).  MAC is generally only seen by directly connected devices at the "ethernet" level of communication. Packets that have to be routed do not use MACs. [https://en.wikipedia.org/wiki/MAC_address](https://en.wikipedia.org/wiki/MAC_address) explains more.

There are times when modifying the MAC address is useful, but not nearly as often as people would believe.
Some cable ISPs use the MAC as a sorta login credential to their modems.  Mine did about 15 yrs ago, but stopped sometime as more homes added more devices. 

Not all devices allow "spoofing" of the MAC address.  Many do.  A MAC address is also a physical identification for a network device (including bluetooth), so if you'd rather not have that physical connection to the device, then spoofing all the MACs (bluetooth, wired and wifi) is necessary.  There are other methods to identify a computer, however.  The EFF has a few web pages that will guess how unique your specific computer+browser finger print is.

Don't confuse MAC with IP address.  IPs are universally used since the TCP protocol requires it to be used for any returned packets to arrive.

Some routers let you change their MAC, but that might break the connection to the ISP.  If you change it, be certain to record the prior value so you can put it back.  Changing the MAC will usually force an WAN IP address change for DHCP devices.

---

