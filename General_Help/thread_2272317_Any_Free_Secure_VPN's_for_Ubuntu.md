---
title: "Any Free Secure VPN's for Ubuntu"
date: 2015-04-05
forum: General Help
---

### Post by seth19 on 2015-04-05
I have been searching for a way to use a secure VPN like Cyberghost, Hotspot Shield or Tunnelbear on Ubuntu for free. I've used these programs on Windows for free for basic security when browsing, ordering, shopping, etc sensitive information and wondered what would be the best way to use a free VPN for Ubuntu. I don't really need any premium account as I just prefer to use VPN's only occasionally, like filing my taxes for instance. Also I always use wired connections in such cases and never go wireless. Additionally it would be an added bonus if I could just be more secure in general and not have to worry about outside connections such as malicious groups, govt. even, business, etc. But my purpose is to keep my personal information safe and for my eyes only. Any help will be greatly appreciate. 

PS. I also have a computer that I could use as a server, maybe? And was wondering if that might be an option somehow? I had read something about using Logmein Hamachi or Amahi but wasn't sure if that would work? I completely new to this and am very confused by terms like OpenVPN and everything. Even if something doesn't work maybe setting up some sort of proxy or anything, because some sort of added security is better than nothing. Thank you!

---

### Post by sandyd on 2015-04-05
> **seth19 said:**
> I have been searching for a way to use a secure VPN like Cyberghost, Hotspot Shield or Tunnelbear on Ubuntu for free. I've used these programs on Windows for free for basic security when browsing, ordering, shopping, etc sensitive information and wondered what would be the best way to use a free VPN for Ubuntu. I don't really need any premium account as I just prefer to use VPN's only occasionally, like filing my taxes for instance. Also I always use wired connections in such cases and never go wireless. Additionally it would be an added bonus if I could just be more secure in general and not have to worry about outside connections such as malicious groups, govt. even, business, etc. But my purpose is to keep my personal information safe and for my eyes only. Any help will be greatly appreciate. 

PS. I also have a computer that I could use as a server, maybe? And was wondering if that might be an option somehow? I had read something about using Logmein Hamachi or Amahi but wasn't sure if that would work? I completely new to this and am very confused by terms like OpenVPN and everything. Even if something doesn't work maybe setting up some sort of proxy or anything, because some sort of added security is better than nothing. Thank you!

Side note: below assumes you are not connecting in a 'public' area, if you are, ignore

A small explanation on what VPNs do is in order:

Normally, your traffic goes something like this (Standard setup)
------------------------
Computer -> Ethernet/Wifi -> Internet gateway -> Internet
------------------------

With a VPN
------------------------
Computer -> VPN -> VPN Gateway -> Internet
------------------------

As you can see from above diagrams, the VPN will only protect you from someone listening at either the internal LAN network or the internet gateway. As a result, unless you suspect that your internal network is insecure, a VPN does not provide more security. In fact, you have to rely on the VPN provider's promises that they do not log your data. As soon as it is out on the internet, anything is fair game.

That being said, Cyberghost, VPNBook and some others all support OpenVPN. Any host that supports openvpn can be used in Ubuntu by installing the openvpn module for networkmanager.

---

### Post by sammiev on 2015-04-05
There was 1 free service that was changing there name every few weeks. I pay for my service and have very happy with them over the years. Just watch for what's free.

---

