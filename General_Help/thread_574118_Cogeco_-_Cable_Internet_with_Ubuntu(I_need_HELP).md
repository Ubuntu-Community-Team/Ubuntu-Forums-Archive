---
title: "Cogeco - Cable Internet with Ubuntu(I need HELP)"
date: 2007-10-12
forum: General Help
---

### Post by justin_c18 on 2007-10-12
As a favour for my brother, I am fixing his computer. I am going to be be reformatting and installing Ubuntu on it. Installation should go all well because Ubuntu's detection of hardware is awesome. 

But, I may have a problem with his internet. He's currently using Cogeco cable internet. I'm used to pppoe and since I am on a small network, the username and password and such is on my router so I don't have to deal with any of that when I connect computers to my network. But, like I said, he's using cable internet and I've never configured cable internet on a computer before, not even XP. What would I need to do to get cogeco working with ubuntu? Is there a username and password I have to use to connect to the internet, is it stored on the modem, or on their side of the network?

I don't want to make his computer/internet inoperable, I've reformatted many times, I'm just worried about his internet connection.

These questions are pretty vague, but, please.. I need the help. Any help would be appreciative.

Thank you,
Justin

---

### Post by RedSquirrel on 2007-10-12
I'm pretty sure the cable internet will simply use DHCP. You probably won't have to do any configuration beyond the Basic Procedure here:

[https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html](https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html)

---

### Post by DGortze380 on 2007-10-12
most cable ISPs use DHCP.

---

### Post by dbott67 on 2007-10-12
> **justin_c18 said:**
> ...he's using cable internet and I've never configured cable internet on a computer before, not even XP. What would I need to do to get cogeco working with ubuntu? Is there a username and password I have to use to connect to the internet, is it stored on the modem, or on their side of the network?

As mentioned above, you'll only need to set the network to DHCP (which is the default).  Cogeco does not use username/password authentication, unlike PPPoE.  

If you get a router for your brother (or even take a look at your own) you'll see that most routers have 3 or 4 ISP settings:

1. Cable/DHCP
2. DSL/PPPoE
3. STATIC IP
4. Others (PPTP, L2TP, BigPond)

 You would set the router to CABLE/DHCP and then plug in his computer.  His computer would then grab an IP from the router.  If he doesn't have a router, the settings would be exactly the same and the computer will grab the IP directly from Cogeco.

So, you really need to do nothing.  Just install Ubuntu and it should just work.  If you want to be extra careful, just pop in the Live CD and boot into Ubuntu --- if he can get online, it "just works".

-Dave

---

### Post by the_nite_owl on 2007-10-12
One other thought, if you have or are adding a router.
Many cable internet providers provision your connection based upon your network cards MAC address.  If he currently connects directly to the cable modem and you add in a router, the router may have to be set to alias the MAC address of the network card that used to connect directly. 
The same issue can occur if you swapped out the PC or the network card of the original PC.  The cable company would have to be called to get the connection working with the new network adaptor and many times they just do not know what they are doing.  A good tech would understand that you needed to re-provision the connection for the new network adaptor but most would not and would make you go through a whole lot of troubleshooting before they gave up and passed it on to someone who knew something.

---

### Post by dbott67 on 2007-10-12
> **the_nite_owl said:**
> One other thought, if you have or are adding a router.
Many cable internet providers provision your connection based upon your network cards MAC address.  If he currently connects directly to the cable modem and you add in a router, the router may have to be set to alias the MAC address of the network card that used to connect directly. 
The same issue can occur if you swapped out the PC or the network card of the original PC.  The cable company would have to be called to get the connection working with the new network adaptor and many times they just do not know what they are doing.  A good tech would understand that you needed to re-provision the connection for the new network adaptor but most would not and would make you go through a whole lot of troubleshooting before they gave up and passed it on to someone who knew something.

Good point.  Many cable ISPs use the MAC address of the NIC for authentication.  As the_nite_owl notes, most routers can clone the NIC provided by (or registered to) the ISP.

In this particular case, I do not believe that Cogeco does this, as I have setup routers & what-not for other Cogeco users.  The only issue that may arise is 'resetting' the cable modem.  If you do happen to change network cards or add a router to the mix, you may need to press the 'reset' button on the back of the cable modem, as there does appear to be some binding of the NIC's MAC address to the cable modem.

-Dave

---

### Post by justin_c18 on 2007-10-12
Thank you muchly.

The computer is at my house, so I won't know if the Cogeco connection works. But, with the recent postings, I'm almost positive it will.

Thanks again, much appreciated.
Justin

---

