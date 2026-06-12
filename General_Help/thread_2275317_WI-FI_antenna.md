---
title: "WI-FI antenna"
date: 2015-04-25
forum: General Help
---

### Post by Old Jimma on 2015-04-25
Hi Commununity! ):P

I've got 14.04 installed on a Lenovo 420, and the WI-FI in the laptop works fine... as long as I don't stray far. ](*,)

I want to use another external WI-FI antenna that plugs into one of the USB ports, and use a real antenna so that I get better reception from a sources that is much further away. :idea:

The reason why I want to do this is because, I'm going to retire and want to access the free  wi-fi available at welcome stations at U.S. National parks... I'm an oldest of old geezer and want to just park at the station's parking lot, instead of trekking into the station itself, and access their free wi-fi from the luxury of my beat-up Ford Ranger truck.

:-k

Can somebody help me get started on how to use the plug-in wi-fi antenna to get access? 

Thanks!  
O:)

Old Jimma from the Old Country

---

### Post by Keith_Helms on 2015-04-25
I have an Etekcity 300Mbps USB Wireless Network Adapter.  It's dirt cheap ($19 at Amazon) and it's plug and play supported by Ubuntu 14.04.  I think I also used it under 12.04 with no problems.  I just plug it in and the Network applet recognizes a second wireless network.  It seemed to see more networks and show better signal strength than the internal wifi in my old laptop.  I got a new laptop about 3 months ago and I haven't tried it with that one yet, but I have no doubt it would work fine.

To get started, I'd look at similar products on places like Amazon or Newegg and read the specs and the user reviews.  See what chipset the specifications say the device uses and then google whether Linux supports that chipset or not and what the earliest kernel version is that supports the chipset.  The Ubuntu 14.04 flavors use the 3.13 kernel and the latest Ubuntu refresh - 14.04.2 - uses the 3.16 kernel.

Edit:  If you really want to push the distance you can connect from, you'll need a directional antenna that you need to point towards the location of the router.  The product I was referring to is omnidirectional meaning it should receive a signal okay from any direction.

---

