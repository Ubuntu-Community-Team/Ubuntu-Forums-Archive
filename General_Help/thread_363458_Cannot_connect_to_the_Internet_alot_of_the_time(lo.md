---
title: "Cannot connect to the Internet alot of the time(loses connection randomly)"
date: 2007-02-16
forum: General Help
---

### Post by billdotson on 2007-02-16
I have this computer and two others in the house. The others run off of wireless and this one plugs directly into the router. The other computer's internet works when mine does not.

I am thinking since it messes up in both Windows and Ubuntu that there is something wrong with my Marvell Yukon Gigabit Ethernet controller (onboard on my Asus P5B Deluxe/Wi-fi AP motherboard) It has been working fine until recently and now I am having internet issues.

In Ubuntu I got the internet working (I think) by going to network manager and hitting configure on the eth0 ethernet device but a window popped up saying I do not have privileges to access the configuration. Then I went to the terminal and just blindly tried sudo network-manager, and then tried sudo net -w. After that I tried the internet and it was working.

I am in Windows now and I got it working in here (I think) by going to the device menu for the ethernet controller, going to the advanced tab, and in the internet connection sharing area I checked on 'Allow other network users to connect to the internet through this computer's connection. It worked after that, but then I turned it off and it is still working.
Funny thing is though Windows sees no problems with it and says it is connected.

I know it is not a driver issue because it was working fine earlier and it doesn't connect in Linux either.

Should I just get a new ethernet cable?

Please help....I hope I get a solution before it goes down again!!  PLEASE..

---

### Post by Kabamaru on 2007-02-17
*I don't have enough experience with the software end of things to help you, but I can offer some hardware related advice.*

Free stuff to try out:

1) Determine if your ethernet cable is faulty:
- Connect the current ethernet cable you have to one/both of your wireless computers (and turn off the computer's wireless network access) to test your cable.  This is assuming that your other computers don't have faulty network cards of their own.

2) Determine if your router port is faulty:
- Connect the current ethernet cable to other ports on your router (with your various computers, remembering to turn off wireless network access from said computers).  This is assuming that your other computers don't have faulty network cards of their own.

3) Determine if your network card is faulty:
- If both your cable and your router are fine, then you may have a problem with your network card.  To test this, you may want to find an extra network card from your other computers that you can use.

Another thing to keep in mind:
Be sure to check that your other computers (the ones that connect wirelessly) are actually connecting to **your** router (and not someone else's).  If they are not, then make them connect to your router wirelessly.  If you force them to connect to your router and they can't access the internet, then your router may be faulty.

---

### Post by gwpritch on 2007-02-17
Make sure that on your wired box that you don't have both a wired and wireless nic trying to connect at the same time. ie deactivate the wireless nic. Otherwise the system gets confused and you will be constantly losing your connection.

---

