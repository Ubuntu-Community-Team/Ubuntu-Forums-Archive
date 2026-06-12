---
title: "What exactly is a router?"
date: 2012-12-25
forum: General Help
---

### Post by OrangeVixen on 2012-12-25
I'm new to networking and I need this cleared up, I know it sounds obvious, but I'm reading a couple of network howtos on setting up a LAN so all my computers can use one dialup connection.

But they all seem to refer to a "router" differently, some seem to refer to it as a device you connect all the computers to with one connection that goes to the Internet. Other docs refer to the Linux box as the "router".

If I do a shopping search for routers I get pics of devices that appear to be "routers", so is it a computer or is it a separate device?

---

### Post by drpjkurian on 2012-12-25
For local area network (LAN) two devices are maimly required they are Modem and Router.
Modem ( Derived from [COLOR="Red"]Mod[/COLOR]ulator-[COLOR="Red"]dem[/COLOR]odulator)is the device which converts the telephone signals to internet signals so that the computer can communicate with the web. 
Router on other hand is a device which routes the signals from the modem to different computers (just like traffic control). 
Nowadays some modems are having inbuilt router,

---

### Post by sanderj on 2012-12-25
> **OrangeVixen said:**
> I'm new to networking and I need this cleared up, I know it sounds obvious, but I'm reading a couple of network howtos on setting up a LAN so all my computers can use one dialup connection.


dialup connection? Really? No DSL or cable?

---

### Post by haqking on 2012-12-25
A router "routes" traffic from one computer or network to another.

**Modems and routers are not related.**

A router may or may not be required on your home network.

If you have a ISP connection and one computer you may be able to hardwire to the modem and then connect directly to the Internet and you wont need a router, however all your Internet traffic will go through a Router on the Internet (a router is the Information Superhighways Traffic Cop directing packets to a destination based on where they came from (source address) to where they want to go (destination address)

A router is like a post office sorting office, it decides where something is going based on address/zip code etc.

If you wanted wireless/WiFi in your house then a Wireless Router will enable multiple connections to all connect to it and the traffic will be routed to other machines on the LAN or out to the Internet based on the packets source and destination address.

Routers can be specialised hardware devices or software running on a Linux or a Windows machine.

[http://www.cisco.com/cisco/web/solutions/small_business/resource_center/articles/connect_employees_and_offices/what_is_a_network_switch/index.html](http://www.cisco.com/cisco/web/solutions/small_business/resource_center/articles/connect_employees_and_offices/what_is_a_network_switch/index.html)

Also read about the OSI layers [https://www.youtube.com/watch?v=p5i5ZE3Oquo](https://www.youtube.com/watch?v=p5i5ZE3Oquo)

This explains packets, routing, etc very well [https://www.youtube.com/watch?v=Ve7_4ot-Dzs](https://www.youtube.com/watch?v=Ve7_4ot-Dzs)

---

### Post by haqking on 2012-12-25
> **drpjkurian said:**
> For local area network (LAN) two devices are maimly required they are Modem and Router.
**Modem ( Derived from [COLOR=Red]Mod[/COLOR]ulator-[COLOR=Red]dem[/COLOR]odulator)is the device which converts the telephone signals to internet signals so that the computer can communicate with the web. **
Router on other hand is a device which routes the signals from the modem to different computers (just like traffic control). 
Nowadays some modems are having inbuilt router,

there is no such thing as a Internet signal and a modem does not convert a signal for use on the Internet.

A modem modulates a signal to be sent to another modem which can demodulate it back into a language the attached computer can understand.

Modems were around and used before the www came about, they can dial straight into another computer without the use of the Internet.

What they do with the modulation/demodulation is to allow one computer to communicate with another often today involving Internet access.

This could be through POTS (plain old telephone system) or *DSL or Fibre or Cable.

At one time they simply converted a digital signal into a analogue one to allow the telephone lines to carry the information which would then be converted back to digital at the receiving modem.

---

### Post by sgage on 2012-12-25
> **OrangeVixen said:**
> I'm new to networking and I need this cleared up, I know it sounds obvious, but I'm reading a couple of network howtos on setting up a LAN so all my computers can use one dialup connection.

But they all seem to refer to a "router" differently, some seem to refer to it as a device you connect all the computers to with one connection that goes to the Internet. Other docs refer to the Linux box as the "router".

If I do a shopping search for routers I get pics of devices that appear to be "routers", so is it a computer or is it a separate device?

The "separate device" really **is** a computer - a very special-purpose one. It runs software that makes it a... router. You can run software on your computer to make it a router, but of course you'd have to also have the hardware to present either ethernet connectivity or wireless to whatever other computers you wanted to share the connection with. When I was still on dial-up, I used to share my connection using my computer as a router, essentially.

Nowadays, a router often presents several ethernet ports plus a wireless capability. It also typically acts as a DHCP server, so that when you boot your computer, it can get an IP address from the router. Then the router keeps track of all the input/output from the various computers attached to it - it "routes" the traffic.

---

### Post by lisati on 2012-12-25
*cough* Simple explanation: A modem is a device which lets you transmit and receive computer signals via the phone line.

---

### Post by haqking on 2012-12-25
> **lisati said:**
> *cough* Simple explanation: A modem is a device which lets you transmit and receive computer signals via the phone line.

*cough* OP asked what a router was ;-)

---

### Post by lisati on 2012-12-25
> **haqking said:**
> *cough* OP asked what a router was ;-)

I noticed that, but wasn't satified with the modem part of the discussion. :D

+1 to the comparision with "Traffic Control" for the router.

---

### Post by haqking on 2012-12-25
> **lisati said:**
> I noticed that, but wasn't satified with the modem part of the discussion. :D

I dont even know why modems are in the discussion...LOL

---

### Post by lisati on 2012-12-25
> **haqking said:**
> I dont even know why modems are in the discussion...LOL

Exactly. Perhaps it arose because the devices provided by some ISPs have both router and modem functionality built in.

---

### Post by offgridguy on 2012-12-25
Can't speak for OP, but does this mean a wifi card is in essence a router?

---

### Post by haqking on 2012-12-25
> **lisati said:**
> Exactly. Perhaps it arose because the devices provided by some ISPs have both router and modem functionality built in.

no it was from post #2

> For local area network (LAN) two devices are maimly required they are **Modem** and Router.Which is of course wrong, as a modem is not needed on a LAN.

It kind of complicated the whole definiton of a router.

---

### Post by haqking on 2012-12-25
> **offgridguy said:**
> Can't speak for OP, but does this mean a wifi card is in essence a router?

no it isnt, it is a wireless card enabling a computer to connect to a wireless access point which may also be a router.

A router is explained above, and in no way resembles a wireless card.

---

### Post by offgridguy on 2012-12-25
> **haqking said:**
> no it isnt, it is a wireless card enabling a computer to connect to a wireless access point which may also be a router.

A router is explained above, and in no way resembles a wireless card.
Thank you:D

---

### Post by offgridguy on 2012-12-25
> **haqking said:**
> 

It kind of complicated the whole definiton of a router.
Agreed

---

### Post by sgage on 2012-12-25
> **offgridguy said:**
> Can't speak for OP, but does this mean a wifi card is in essence a router?

No, a wifi card is hardware, that lets you take advantage of a nearby router that offers wifi connectivity. 

Though there is probably a way, with the right software, to make the computer containing the wifi card a router.

---

### Post by lisati on 2012-12-25
The OP appears not to have been back to this thread for a few hours. A summary might be in order.

[LIST]
[*]A **router** is a device that supervises and controls traffic on your network. Its role is similar to to a telephone exchange, which manages connections between telephones. The router manages communications between computers.
[*]A **modem** is a device that allows you to transmit *digital* data across a medium, such as a phone line, that is better suited to *analogue* data. You don't normally need one to connect to your **Local Area Network** (LAN)
[*]A **Network Interface Card** (sometimes referred to as an NIC) is a device that lets you physically connect to a network, usually through a router
[*]A **WiFi card** is a form of NIC that uses radio signals instead of a wire to access a router
[/LIST]
In the interests of brevity, this summary is somewhat simplified.

---

### Post by Thee on 2012-12-25
> **OrangeVixen said:**
> 
But they all seem to refer to a "router" differently, some seem to refer to it as a device you connect all the computers to with one connection that goes to the Internet. Other docs refer to the Linux box as the "router".

The reason why there are 2 explanations what a router is, is because both the device that you can buy that acts as a router for all your computers to connect together over the network, and a PC that is configured and made specifically for the same purpose are both called routers.

So a router is a device (dedicated device or a dedicated PC) which is used to connect multiple PC's or devices that can interact with each other over the local network and also share the internet connection.

But of course, a dedicated device type of router is the most commonly used, most inexpensive and practical.

---

### Post by eddier on 2012-12-25
I allways explain a router as a sound mixer in reverse,instead of mixing signals from several devices into one output,you have one input and several outputs. Except they are bidirectional !
If you only have one PC then you wont need a Router. Unless your into carpentry-but thats a different route.

eddie

---

### Post by haqking on 2012-12-25
> **eddier said:**
> I allways explain a router as a sound mixer in reverse,instead of mixing signals from several devices into one output,you have one input and several outputs. Except they are bidirectional !
If you only have one PC then you wont need a Router. Unless your into carpentry-but thats a different route.

eddie

Loads of people use a router with one PC.  I would suspect a large majority of the readers of this forum are using or have only one PC connected to a router.

For the benefits of the firewall, NAT, logs etc.

You also dont "need" a router with more than one PC.

I cant believe this thread has got so complicated, good job nobody asked about Layer 3 switches, Bridges, hubs (active and passive), Netbios and IPX/SPX routing....LOL ;-)

I think it would be beneficial to alot of people to read up on the OSI layers and watch the net warrior video in my [post number #4]("http://ubuntuforums.org/showpost.php?p=12420961&postcount=4")

---

### Post by offgridguy on 2012-12-25
> **lisati said:**
> The OP appears not to have been back to this thread for a few hours. A summary might be in order.

[LIST]
[*]A **router** is a device that supervises and controls traffic on your network. Its role is similar to to a telephone exchange, which manages connections between telephones.
[*]A **modem** is a device that allows you to transmit *digital* data across a medium, such as a phone line, that is better suited to *analogue* data. You don't normally need one to connect to your **Local Area Network** (LAN)
[*]A **Network Interface Card** (sometimes referred to as an NIC) is a device that lets you physically connect to a network, usually through a router
[*]A **WiFi card** is a form of NIC that uses radio signals instead of a wire to access a router
[/LIST]
In the interests of brevity, this summary is somewhat simplified.
Nice factual explanation. Thanks.

---

### Post by Zill on 2012-12-25
> **haqking said:**
> ...I cant believe this thread has got so complicated, good job nobody asked about Layer 3 switches, Bridges, hubs (active and passive), Netbios and IPX/SPX routing...
A good point!

My understanding is that a "typical" home router actually rolls up five main functions into one box.
[LIST=1]
[*]DSL modem to connect to the phone line
[*]NAT firewall to translate IP addresses
[*]DHCP server to allocate LAN dynamic IP addresses
[*]Hub to distribute signals via one or more ethernet ports
[*]wifi access point
[/LIST]

---

### Post by OrangeVixen on 2012-12-25
> **drpjkurian said:**
> 
Nowadays some modems are having inbuilt router,

What is confusing me is that a couple of howtos on IP masquerading (NAT) have different references to "router". Some are saying it's a Linux with a modem, others are describing it to something similar to what you described.

I have one Linux with a ppp0 interface using dialup. I'm not sure where the "router" goes.

I also found references to "switch" and "hub", I need to connect computers within the LAN to the Linux box with the dialup so they can access the net too. The Linux box has an ethernet card (a eth0 interface)

Do I connect the Linux box's eithernet card to a router or is the Linux box "is" the router in this case? where does the switch and hub come in?

---

### Post by OrangeVixen on 2012-12-25
> **Thee said:**
> 
So a router is a device (dedicated device or a dedicated PC) which is used to connect multiple PC's or devices that can interact with each other over the local network and also share the internet connection.

Thanks, I think I am beginng to understand what a router is now.

Since I am using dialup (and no, seriously, I'm at my relative's place in the middle of no where, we're lucky to have telephone, power, water, and food), the Linux box is using dialup to connect to the net, hence I am able to post this.

There are two other computers (a Mac and a Windows box) I want connect to the net, the Linux box has a ethernet card and so do the other two computers (they all have one) so I guess in this case the Linux box IS the router?

If so, then all I need is a switch or hub to connect the other computers to the "router" which is the Linux box?

---

### Post by Cheesemill on 2012-12-25
> **OrangeVixen said:**
> If so, then all I need is a switch or hub to connect the other computers to the "router" which is the Linux box?
Sounds good to me.
You also have to set up your linux box as a router that provides NAT and DHCP (not essential but makes configuring the other machines a lot easier).

I've used this tutorial successfully plenty of times (in your case replace eth0 with the name of your dial up interface):
[http://codeghar.wordpress.com/2012/05/02/ubuntu-12-04-ipv4-nat-gateway-and-dhcp-server/](http://codeghar.wordpress.com/2012/05/02/ubuntu-12-04-ipv4-nat-gateway-and-dhcp-server/)

---

### Post by OrangeVixen on 2012-12-25
> **Cheesemill said:**
> Sounds good to me.
You also have to set up your linux box as a router that provides NAT and DHCP (not essential but makes configuring the other machines a lot easier).


Thanks so I just need to get a *switch*, I got the NAT part, but do I *really* need to set up DHCP?

I have /etc/resolv.conf set properly on my Linux box (the "router") to use the ISP's domain name servers, do my subnet computers (the Mac and the Windows box) need DHCP?

Btw, the tutorial I'm going by is [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing) (which got my confused about "routers" in the first place).

---

### Post by Cheesemill on 2012-12-25
DHCP is optional. If you don't use it it just means that you have to set up networking (IP address, netmask, gateway and DNS settings) on the other client machines manually instead of it being automatic.

---

### Post by redmk2 on 2012-12-25
> **OrangeVixen said:**
> Thanks so I just need to get a *switch*, I got the NAT part, but do I *really* need to set up DHCP?

I have /etc/resolv.conf set properly on my Linux box (the "router") to use the ISP's domain name servers, do my subnet computers (the Mac and the Windows box) need DHCP?

Btw, the tutorial I'm going by is [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing) (which got my confused about "routers" in the first place).
It might be helpful to think of the Linux machine as a stack of services.  The routing part handles the *inter-networking of different IP networks *(e.g. ***packet forwarding***).  The switch (or hub) handles the *inter-connection of machines on THE SAME network*.  The other items are enhancements to IP networking in a single network (LAN).

If you think of you dial-up connection as the interface to the wider world (WAN) and the Ethernet connection as the interface to the local network, then the router is the machine that forwards (back and forth) the traffic from the LAN to the WAN and visa versa.

The NAT is just translating the IP addressing for the machines on the LAN to the single Ethernet interface IP address on the Linux machine.  When the data traffic is flowing you need a source and a destination.  NAT handles that in a router with LAN addressing.

DHCP just automates IP addressing as has been stated preciously.

---

### Post by davidtrounce on 2012-12-25
Possibly because many of the wireless Modems come with a router built in.

---

### Post by offgridguy on 2012-12-26
991 views so far, this is obviously an interesting topic for a lot of people, including me. :D

---

### Post by diskmaster23 on 2012-12-26
This is something you might have not thought of, but the computer with the modem you are trying to share will have to be powered on for it to 'route' your other computers to the internet. You power down that computer with the modem, your connection to the internet goes down. Unless you have a dedicated just for dialing up and routing to the internet. 
Just as a friendly reminder.

Wow...this is a throwback to the dial-up days. ::Shudders:: I don't wanna go back.

---

### Post by OrangeVixen on 2012-12-26
> **diskmaster23 said:**
> This is something you might have not thought of, but the computer with the modem you are trying to share will have to be powered on for it to 'route' your other computers to the internet.

Wow...this is a throwback to the dial-up days. ::Shudders:: I don't wanna go back.

Yes I'm keeping the Linux "router" on all the time.

What confused me about the "router" was that none of the HOWTOs that I read ever stated (clearly) that a router can be *either* a dedicated device (picture required) or a Linux box configured to do NAT (and DHCP). 

So when I did searches for router, it showed me pictures of devices that look nothing like a Linux box or any computer.

I'm at my relatives place where there is barely telephone connections, so dialup is all we have. I can barely get any connection above 26k on this 56k modem.

I just realized how much bandwidth some "bloated" sites require, they're probably making ISPs and engineers who want to design higher capacity connections a lot of money. Some web pages transfers up to 10M-BYTES of data PER WEBPAGE. (what a waste) :(

---

### Post by haqking on 2012-12-26
> **OrangeVixen said:**
> Yes I'm keeping the Linux "router" on all the time.

What confused me about the "router" was that none of the HOWTOs that I read ever stated (clearly) that a router can be *either* a dedicated device (picture required) or a Linux box configured to do NAT (and DHCP). 

So when I did searches for router, it showed me pictures of devices that look nothing like a Linux box or any computer.

I'm at my relatives place where there is barely telephone connections, so dialup is all we have. I can barely get any connection above 26k on this 56k modem.

I just realized how much bandwidth some "bloated" sites require, they're probably making ISPs and engineers who want to design higher capacity connections a lot of money. Some web pages transfers up to 10M-BYTES of data PER WEBPAGE. (what a waste) :(

a "router" can be a dedicated device (the Internet runs on the back of dedicated routers, they can also be a typical looking computer running either Linux or Windows whose software is configured to be a router.

DHCP, DNS or any other service or anything else is not a function of a router, they are just additional services which routers can provide such as the home based "routers" which often also have a modem, a DNS service, a DHCP service, NAT etc etc.

In one sentence **A router routes TCP/IP packets from source to destination, any other service is an addition to it.**

Peace

---

### Post by OrangeVixen on 2012-12-27
I think the key clarification point that needs to be cleared up is that a router can be either a computer (running Linux, Windows, etc) or an integrated device (a "router").

Because if you do a search for "routers" online you don't get pics of computers running Linux or whatever but rather small integrated devices called "routers".

Where as the LAN routing HOWTOs refer to computers running Linux as "routers".

So now I learned a router can refer to either one of those.

---

### Post by ZippyUbu on 2012-12-27
Interesting Topic +1 ;-)

> I think the key clarification point that needs to be cleared up is that a  router can be either a computer (running Linux, Windows, etc) or an  integrated device (a "router").You are correct OV. A router can be a PC with Linux installed, a Windows Server with the correct services installed or a dedicated piece of hardware, Cisco XR 12410.

--
Zu

---

### Post by sgage on 2012-12-28
This might interest some folks:

[How to build a router based on Linux]("http://lxer.com/module/newswire/ext_link.php?rid=178437")

---

### Post by offgridguy on 2012-12-31
> **sgage said:**
> This might interest some folks:

[How to build a router based on Linux]("http://lxer.com/module/newswire/ext_link.php?rid=178437")
Interesting

---

### Post by JKyleOKC on 2012-12-31
Once you have this set up and running, you may find that connection speed drops to a crawl when all three machines are trying to address the web at the same time. Your 28K bits/sec will drop to 28K/3 or approximately 9.3K bits/sec per computer; dialup has 10 bits per byte, so you can expect about 930 bytes/sec of data transfer. That 10-MB web page will take about 1000 seconds, or almost 20 minutes, to load!

---

### Post by offgridguy on 2013-01-01
> **JKyleOKC said:**
> Once you have this set up and running, you may find that connection speed drops to a crawl when all three machines are trying to address the web at the same time. Your 28K bits/sec will drop to 28K/3 or approximately 9.3K bits/sec per computer; dialup has 10 bits per byte, so you can expect about 930 bytes/sec of data transfer. That 10-MB web page will take about 1000 seconds, or almost 20 minutes, to load!
Thanks for the input, actually i was looking at my neighbors router,and i 
wonder ,why bother using a computer when you can have a dedicated router device for a lot less money ?

---

### Post by OrangeVixen on 2013-01-01
> **offgridguy said:**
> why bother using a computer when you can have a dedicated router device for a lot less money ?

Are there dedicated routers for dialup? ppp? I always wondered that, I thought you can only set up a router like that with a computer?

---

### Post by JKyleOKC on 2013-01-01
> **OrangeVixen said:**
> Are there dedicated routers for dialup? ppp? I always wondered that, I thought you can only set up a router like that with a computer?At one time, dedicated routers such as the LinkSys WRT254 were available; these had no modem included as part of the unit. They worked equally well (or poorly in some cases) with dial-up, DSL, or cable, because in each case a separate modem was required between the router and the phone/cable connection.

These days most if not all consumer-grade units combine the router and the modem into one box, so that a "cable router" won't work with DSL, a "DSL router" won't work with cable, and neither will work with dial-up although many do have a "WAN port" to which you can connect a dial-up modem. My ISP calls these combination units "gateways" and they often include wireless capability (as did the WRT254 for that matter).

However standalone dial-up modems themselves are difficult to find these days, and the ones that were built into recent computers (but not in the past couple of years) don't have any way to get the router in between the modem and the computer. In such a case, creating a "software router" within the computer as described in the original how-to article is the only way to travel...

---

### Post by offgridguy on 2013-01-01
I found this article, which i found helpful.

[http://ask-leo.com/whats_the_difference_between_a_hub_a_switch_and_a_router.html](http://ask-leo.com/whats_the_difference_between_a_hub_a_switch_and_a_router.html)

---

