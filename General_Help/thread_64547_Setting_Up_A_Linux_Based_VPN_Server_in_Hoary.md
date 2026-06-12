---
title: "Setting Up A Linux Based VPN Server in Hoary"
date: 2005-09-11
forum: General Help
---

### Post by FishFoot on 2005-09-11
Hi All,

I've installed Hoary and I've found a new mistress.  After running through a bunch of other distros over the past few years Ubuntu is by far the best I've ever found.  Beautiful work.

I'm interested in setting up a VPN connection to allow me to connect to my home network while traveling.  I would want to have access to ALL my network resources, not just the machine running the VPN server.   I've got a dedicated (dlink) router/firewall that my Ubuntu box is behind.  I'm clear on the need and ways to route packets to that machine using this router.

That said, how do i setup a VPN?  I've done a bunch of searching but I have yet to find anything that is remotely concise.  I've seen mention of Freeswan and Openswan, iptools, and racoon.  But I can't find anywhere that simply says... DO THIS.

In addition, Hoary runs the 2.6 kernel which has the IPsec capabilities built straight in.  I don't know how that affects the process.

So, I turn to the Gurus that have built this WONDERFUL distro and I ask:

1) What are my options for running a VPN?  If there is more than one, what are the pros and cons?

2) How do I go about setting up the SERVER end of things.  The client (Windows or Linux) I would imagine is the easier part of the 2.

Thanks in advance
-FishFoot

---

### Post by KenLazlo on 2005-09-13
Try openvpn

[www.openvpn.org](www.openvpn.org)

It's easier to configure and works fine. 

It runs on Linux and Windows

you need a dyndns name ([www.dyndns.org](www.dyndns.org))

---

### Post by psypher on 2005-09-18
for a bridge mode vpn go here: [http://openvpn.net/wiki/Bridged_Mode_OpenVPN_Server_on_Debian_HOWTO](http://openvpn.net/wiki/Bridged_Mode_OpenVPN_Server_on_Debian_HOWTO)

i followed this to a T and I got it working no problem.(except apt-get bridge-utils instead of bridgeutils) I needed bridge mode to play lan games that rely on broadcast traffic. I got it working tonight and have yet to test out BFME. But I am pretty positive it works as I could see my workgroup from a client vpn connection without any hassle. This will not work with traditional VPN's. 

As a windows client I used OpenVPN Gui for Windows [http://openvpn.se/](http://openvpn.se/) and that just worked. Instead of copying my client keys and config files into /etc/openvpn it went into c:\programfiles\openvpn\config. right clicked openvpn gui, connect and it connected, waited 3 minutes and could see my server side workgroup and could browse all the shares at quite a pleasant speed. connection was between 2 - 512 adsl's and got 40k d/l from server

the config isn't that much different with normal route mode. just create tun's instead of tap devices

---

### Post by Bill_Albertson on 2005-09-28
Fishfoot,

I am in a similar dilemma with regards to the Breezy release.  I have also looked up the Ubuntu Wiki on IPSEC, and it is just for client access.  There is no public direction on this that I have been able to find from the Ubuntu foundation on this issue.  I also can't use openvpn like so many people recommend- its not IPSEC, it is SSL and requires all the hosts on openvpn to be using openvpn.  Different monsters.

I have some background setting up IPSEC gateways, and I will give working out a cross-platform implementation that can easily be followed, and post it back here.  My minimum for this is interoperability with WindowsXP, and both the Ubuntu and WinXP boxes establishing full peering.  From my own research, WinXP already supports client/server IPSEC peering out of the box.

On my own part, I have found security problems with the couple of Dlink wireless products that I use, so I want to make sure that as much access as possible is secured with a password or some other mechanism on my host network.  I was hoping, like you, that someone had already worked all of this out, but it seems nobody has.  So, I guess I will be posting back MY solution to the problem.

I had considered lots of routing madness and virtual gateways running in a star topology out of my OBSD router/firewall, but then I realized that it is just easier and probably more secure to run sessions between clients themselves, and run pass and QOS rules for ESP, UDP 500, TCP 22 & 115, and the usual 80, 443, and other administrativa on a per user basis with authpf.  I am going to try for the largest reasonable keysizes possible to run on these concurrent peering sessions without having timeouts and other such quirky behavior.  On a side note, I really wish the Ubuntu project would work on a port of pf...sigh.

I should have something (at least whether any of this will work) in a couple of weekends.  This is important to me, but I have to work on things that get me paid first :)

---

