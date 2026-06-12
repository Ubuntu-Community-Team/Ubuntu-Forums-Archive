---
title: "Network confusion"
date: 2018-11-19
forum: General Help
---

### Post by alving on 2018-11-19
Hi all
Im not sure what category this is supposed to go in.
I figured "General Help" would be a good starting place.

I have 3 computers on a network in the house.
(All wired and running Edubuntu 14.04.5 x64)
The one we use the most keeps losing its internet connection, i believe the home network is still accessible.
When it happens, the only way i can get the internet back is to reboot the computer.
I tried playing with some of the setting for the network.
I have asked google, without any success either...

Could this be caused by a power surge from the space heater thats plugged into the same electrical circuit?

Im not sure what info would be most relevant.
If someone could let me know;
Either the info needed, or
If they have had the same problem and how to fix it.

Thanks
Allyn

---

### Post by Autodave on 2018-11-19
The space heater could cause that problem.  I, for testing purposes, would run and extension cord for the computer (NOT the space heater) to a different circuit in the house.  If that cures the issue, then you may want to consider a power backup unit for the PC (they are really cheap nowadays) or getting that circuit checked out.  How many other things are that outlet?  That circuit breaker?

---

### Post by alving on 2018-11-19
Thanks for the quick reply.

Plugged into the outlet are just the heater and computer.
WHOLE crap load of stuff on the circuit.
Which includes the computer in question (in our dining room), as well as most of the kitchen.
Fridge, micro-wave, freezer, counter appliances, etc.

I dont really like running extension cords all over the place, but the landlord wouldnt be to happy if i start wiring up new circuits.

Thanks again
Allyn

---

### Post by HermanAB on 2018-11-20
These things are not hard to debug:
1. Ensure that you have only one DHCP server - usually your home router.
2. Check with *ifconfig* and *route* what the settings are when it works and after it stopped working.
3. When all else fails, look at the packets with *tcpdump* when the network settings are refreshed - you will quickly see and understand the handshake that happens there (whois DHCP, I am DHCP, gimme an address, here is your address...).

Once you understand what is supposed to happen with the DHCP handshake, you will see what is going wrong and then you'll be able to fix it.

---

