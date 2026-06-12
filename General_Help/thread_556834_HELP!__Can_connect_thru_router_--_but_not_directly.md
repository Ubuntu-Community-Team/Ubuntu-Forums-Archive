---
title: "HELP!  Can connect thru router -- but not directly connected to modem"
date: 2007-09-21
forum: General Help
---

### Post by GadgetsGuy on 2007-09-21
I have a problem that has made me pull out all of my hair!

My mother has a computer running Feisty that has been directly connected to the modem and working fine for more than 6 months ...

Last week it mysteriously dropped its net connection and nothing I told her to try doing worked, so I came to try to fix it ... (a 7 hour drive, but I am digressing ...)

The modem was operating fine, and the cable company confirmed a connection.

I brought my D-Link router so that I could share her connection with my laptop.  As soon a I plugged in my router to the modem, and hardwired her to the router, her internet connection worked fine.

I did a tune-up on her computer doing the updates etc. (I have auto updates turned off, since I am 700 miles away from her if an update goes bad)

Now I unplug her from my router, and reconnect her computer directly to the cable modem, and the original problem resurfaces ... no net connection at all no matter how many times I recycle the modem, as well as her PC.

I have no clue how to manually check the DHCP settings, or what ever else might be the problem.

ANY and ALL help would be appreciated, as I need to go back to Montreal to tend to my business, of which I am already one day late.

Many thanks in advance!

---

### Post by GadgetsGuy on 2007-09-21
bumping for an answer ...:confused:

---

### Post by PmDematagoda on 2007-09-21
I don't know the answer for your problem, but it may help to post specifics about the modem such as make, brand, how it is connected to the computer, etc.

---

### Post by BeastlyKings on 2007-09-21
I'm not sure about your problem, but as for the 700 mile away thing, why not just Remote log-in to her computer to update/fix problems .ect?
I can see how if it needs rebooting or cables changed or reinstalled or something it could be a hassle but still it would work for small problems.

---

### Post by MrFSL on 2007-09-21
Some cable ISP's bing their modem to the device.

I ran into this when I was doing work in Kentucky a few years ago. The client was getting an address but no network connection. Ultimately when I navigated to the IP address of the supposed DNS server, I was faced with a web page that let me change the default device for the modem.

Weird I know!

I haven't seen it before and I haven't seen it since but if it helps... there you go!

Call the ISP.

---

### Post by GadgetsGuy on 2007-09-21
> **BeastlyKings said:**
> I'm not sure about your problem, but as for the 700 mile away thing, why not just Remote log-in to her computer to update/fix problems .ect?
I can see how if it needs rebooting or cables changed or reinstalled or something it could be a hassle but still it would work for small problems.

Thanks for the suggestion, but to the best of my knowledge, VNC and all other remote access platforms, require a net connection to function. If you know of a way to connect without a net connection, please do share it.

For the last 6+ months I have fixed almost all problems she has had using VNC, but without a net connection (which is the current problem), I am unable to login remotely ...

---

### Post by GadgetsGuy on 2007-09-22
> **MrFSL said:**
> Some cable ISP's bing their modem to the device.

I ran into this when I was doing work in Kentucky a few years ago. The client was getting an address but no network connection. Ultimately when I navigated to the IP address of the supposed DNS server, I was faced with a web page that let me change the default device for the modem.

Weird I know!

I haven't seen it before and I haven't seen it since but if it helps... there you go!

Call the ISP.

I called the ISP and they DO NOT SUPPORT LINUX at all ...

every question I asked -- regardless of nature -- was responded to with "I'm sorry but we do not support Linux ..."  The A55HOLE on the other end of the phone wanted nothing to do with me once I told him I was on Linux ...  :(

---

### Post by GadgetsGuy on 2007-09-22
bump again for the morning Linux gurus ...

---

### Post by GadgetsGuy on 2007-09-22
Well unfortunately Ubuntu has kicked my A55 on this issue ... 

I am losing too much money trying to figure this out, so I am just going to leave my router here, and have bought a new router for myself. :(

I would still be interested in finding out WTF was the problem why I can connect with a router with no problem at all, but directly connected to the modem I can not connect to the net.  :confused:

If anybody has any insight at all into this problem, please do share it with me ..

Thanks!

---

### Post by Dropknee on 2007-10-13
I have this problem too, I can´t access my modem in Ubuntu, but can access with Windows, I´m trying to figured why this happen.

---

### Post by Dropknee on 2007-11-01
Same here and helping to bump this for a solution. 

I have a Linksys WRT54G v.5, in Windows I can access my modem without any problem through the router, but when I'm in Ubuntu, I cant, but if I plug the modem directly to my PC, I can access without any problem, but when I connect back with the router I lost the access once again to my modem.

I don't know if Windows have any special service or something for this, but I cant find a solution.

Any help is appreciated

---

### Post by MrFSL on 2007-11-01
@Dropknee

Let me get this straight:

1) you have a cable modem
2) attached to the cable modem you have a linksys router
3) If the PC connected to the router is running Windows you have internet
4) If the PC connected to the router is running Linux you have no internet

but - If the same computer running linux is connected directly to the modem, you do have internet?

Please clarify... is this the case?

---

### Post by macogw on 2007-11-02
Is it a different Windows computer?  The modem might be doing MAC address filtering.  I know a lot of them do that.  They have to be power-cycled (unplugged for 10 seconds) then you have to reboot your comp for it to do the "handshake" again.  It's a pain in the butt to get the internet with my laptop at my mom's because of that.

---

### Post by Dropknee on 2007-11-02
> **MrFSL said:**
> @Dropknee

Let me get this straight:

1) you have a cable modem
2) attached to the cable modem you have a linksys router
3) If the PC connected to the router is running Windows you have internet
4) If the PC connected to the router is running Linux you have no internet

but - If the same computer running linux is connected directly to the modem, you do have internet?

Please clarify... is this the case?

ok let me clarify this

I have a modem connected through the router, I have Internet in Windows and Linux, the difference is in Windows I can access the modem and in Linux don't and I don't understand that behavior. In windows I can access my router with the generic ip 192.168.1.1 and my modem with his own generic one too and is 169.254.1.1, but in Linux I can access the router with the 192.168.1.1 but cant access my modem with 169.254.1.1 

But if I connect the modem directly to my computer without the router, in Linux I can access the modem with his generic 169.254.1.1 without problem. The problem here is the router in Linux and don't know why

Sorry for my bad english, I hope you guys understand what I'm trying to explain here

Almost forgot, all this is in the same computer.

---

