---
title: "Programs have a mind of their own... scary things happening to my firewall!"
date: 2008-06-22
forum: General Help
---

### Post by PARO on 2008-06-22
I'm all of a sudden having a problem where all my programs that access the internet are writing their own holes in my router's firewall. The only thing I can imagine that could be responsible is following bad advice (a command:  sudo chmod a+r /dev/input/event*) to allow a program to access my gamepad, which didn't work, it still doesn't see it, but now I have this problem.  I guess it could also be due to the upgrades installed today, but I haven't seen anyone else having this problem. Anyone know how I can return normal permissions to my programs?  Ubuntu is taking over my network!

---

### Post by PARO on 2008-06-23
Ah... I guess it was the upgrades after all.  New upgrades today fixed everything. Problem solved.

---

### Post by balagosa on 2008-06-23
friendly reminder: do not forget to mark the thread solved

:KS

---

### Post by PARO on 2008-06-30
This problem has reemerged with yet another system update.. and yet I still can't find anyone else having this problem. Things have been fine for about a week, but after the upgrades I installed last night have noticed gnutella and transmission writing their own firewall rules into my router's firewall!  I have a D Link DI-624, and Ubuntu has never been able to write it's own rules to my router's firewall from Dapper on, but for some reason that's changed. Since I still haven't heard (or found) anyone else having this issue I'm wondering if it could be a combination of something I did with something Ubuntu is doing... I have no clue.  Any help would be appreciated.

---

### Post by mcduck on 2008-06-30
Do you have UPnP enabled in your router's settings? It's purpose is to allow devices and programs that support UPnP to open the ports they need to function.

I have a DI-524 and on that router's configuration menu the setting is in Tools/Misc.

---

### Post by PARO on 2008-07-03
Yeah it's enabled, but what should I assume then? That these programs have been upgraded to directly write rules to my router's firewall, or that this has something to do with the Ubuntu upgrades?  So far I've only noticed transmission and frostwire are able to do this. I've noticed that Ekiga however still needs me to write rules for it to work though, it can't, or won't write it's own.  I've been using transmission for probably over a year or so and it's never done this until recently, frostwire I use rarely, so can't really say when that started.  And I've had this router for about 4 or 5 years and have never seen a program do this until I posted here (and I'd definitely know since I had to go in and write rules to allow these programs to work properly). 

As long as this isn't a security issue, I'm fine with it, in fact it saves me the time of having to write my own rules and change ports and all to get things functioning properly. But this seems like it would be granting programs a little too much autonomy in allowing them to bypass my router's firewall and open whatever ports they please. Or does UpnP allow them to do that anyway, only without the visual rules popping up?  If that's the case though, then it must've been broken in every bittorent client I've ever used (some 8 different ones or so, all of which I had to write rules for), or WinXP and Ubuntu, since most of the computers accessing this network run Windows, and I'm obviously running Ubuntu.  So I'm still a little confused about why this is happening. Thanks for your response by the way.

---

### Post by mcduck on 2008-07-07
Well, I'd say that for some reason or other uPnP wasn't working correctly for you, andthen probably some update fixed the problem.. ;)

Transmission at least supports uPnP, and probably Frostwire as well as most P2P apps do these days. (Opening ports for incoming traffic is pretty important for P2P so that makes sence..). I'm not sure if Ekiga supports it or not, if it doesn't htat would be a simple explanation to why you still need to open ports for it by hand.

There has been some discussion about uPnP's safety, and I believe there were some security issues with it. MAny people choose to disable it because of this. I'm actually using it myself, as managing the ports for different apps and all my consoles is a nasty job and I prefer it done automatically. This far I haven't had any problems but that's just how it's been for me and doesnt guarantee that you'd be safe with uPnP.

From Wikipedia:
> 
Problems with UPnP

Lack of Authentication

The UPnP protocol does not implement any authentication, so UPnP device implementations must implement their own authentication mechanisms, or implement the Device Security Service.[2] Unfortunately, many UPnP device implementations lack authentication mechanisms, and by default assume local systems and their users are completely trustworthy.[3][4] Most notably, Routers and firewalls running the UPnP IGD protocol are vulnerable to attack since the framers of the protocol omitted to add any standard authentication method.

For example, Adobe Flash programs are capable of generating HTTPU (HTTP over UDP) requests. This allows the router settings to be modified by a malicious web site when someone with a UPnP-enabled router simply visits that web site.[5] The following changes can be made silently by code embedded in an Adobe Flash object hosted on a malicious website[6]:

    * Port forward internal services (ports) to the router external facing side (i.e. expose computers behind a firewall to the internet)
    * Port forward the router's web administration interface to the external facing side
    * Port forwarding to any external server located on the Internet, effectively allowing an attacker to attack an Internet host via the router, while hiding their IP address
    * Change DNS server settings so that when victims believe they are visiting a particular site (such as an on-line bank), they are redirected to a malicious website instead.
    * Change the DNS server settings so that when a victim receives any software updates (from a source that isn't properly verified via some other mechanism, such as a checking a digital certificate has been signed by a trusted source), they download malicious code instead.
    * Change administrative credentials to the router/firewall
    * Change PPP settings
    * Change IP settings for all interfaces
    * Change WiFi settings
    * Terminate connections

This only applies to the "firewall-hole-punching"-feature of UPnP; it does not apply when the IGD does not support UPnP, or UPnP has been disabled on the IGD.[citation needed] Also, not all routers can have such things as DNS server settings altered by UPnP because much of the specification (including LAN Host Configuration) is optional for UPnP enabled routers[7]

---

### Post by PARO on 2008-07-14
Ok, thanks for the help.

---

