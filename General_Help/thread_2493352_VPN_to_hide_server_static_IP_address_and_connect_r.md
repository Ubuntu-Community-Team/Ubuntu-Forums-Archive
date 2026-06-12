---
title: "VPN to hide server static IP address and connect remotely to another computer"
date: 2023-12-12
forum: General Help
---

### Post by freeflyjohn on 2023-12-12
I am seeking advice about VPN which I have very limited understanding of and get very confused.

The diagram below shows my setup and there are two things I am trying to do:

1. I want my server (which is running Ubuntu) to be hidden behind a VPN
2.  I want to connect my server to my parents iMac which will have a USB  HDD connected, so that I can perform off site backups of the HDD's in my  server 

I have a static IP address which comes standard with my ISP (Zen internet)


(Refer to attached image below)


A  work colleague has setup a VPN for remote connection to a server (which  runs Enterprise Architect) and he used TP-Link ER605 VPN router for the  remote access.

For connection to my parents iMac, would this work as shown in the diagram below ?

(Refer to attached image below)

I  know the ideal situation would be to have a NAS at my parents house,  but a 4 bay NAS costs around £500+ and then I would need the HDDs for  the NAS so thats another £400+

Plus I wouldn't need anytime  access like a NAS is designed to provide, I would just ring my parents  when I want to perform an offsite backup, ask them to plug in the the  USB HDD and connect remotely.

My parents might change their ISP from Virgin to Zen internet, in which case they too would have a static IP address.

How can I go about setting up a VPN to meet these requirements ?

---

### Post by TheFu on 2023-12-12
If you want to hide your public IP, then you'll need a VPN server on a VPS somewhere else and VPN connections between their system and your system to that 3rd party VPN.

Wireguard can do this.
If you are the trusting sort, you can use something like TailScale. I'm not so trusting, so I have a $4/month VPS.

With the VPS having a static IP and running the main wireguard node, neither you, nor your parents need to have static IPs. In fact, you can setup your phone and table and laptop to join the wireguard "mesh" network for access to any of the systems from anywhere (assuming the outbound wireguard traffic isn't blocked by the location).  Some enterprises will block all outbound traffic that isn't HTTP/HTTPS and going through their proxy. Wireguard won't work.  There are some things you can do, perhaps to use the HTTPS ports and if they have a dumb firewall and dumb proxy, the VPN will work, but ... that shouldn't be expected.

When it comes to running a VPN server, I have a few rules.  Never, ever, run the VPN on your primary edge router that protects your entire network. When that device fails, there are some terrible failure modes which may leave you with no VPN, but access still provided.  I don't want anything on my edge router besides a firewall and routing.  No DHCP, no DNS, no fancy addons, no VPN.  They should do routing and firewalling, nothing else.  Sure, there are 500 packages that can be installed on our edge routers now, but just because something is possible, that doesn't make it a good idea.

---

### Post by freeflyjohn on 2023-12-15
> **TheFu said:**
> If you want to hide your public IP, then you'll need a VPN server on a VPS somewhere else and VPN connections between their system and your system to that 3rd party VPN.

Wireguard can do this.
If you are the trusting sort, you can use something like TailScale. I'm not so trusting, so I have a $4/month VPS.

With the VPS having a static IP and running the main wireguard node, neither you, nor your parents need to have static IPs. In fact, you can setup your phone and table and laptop to join the wireguard "mesh" network for access to any of the systems from anywhere (assuming the outbound wireguard traffic isn't blocked by the location).  Some enterprises will block all outbound traffic that isn't HTTP/HTTPS and going through their proxy. Wireguard won't work.  There are some things you can do, perhaps to use the HTTPS ports and if they have a dumb firewall and dumb proxy, the VPN will work, but ... that shouldn't be expected.

When it comes to running a VPN server, I have a few rules.  Never, ever, run the VPN on your primary edge router that protects your entire network. When that device fails, there are some terrible failure modes which may leave you with no VPN, but access still provided.  I don't want anything on my edge router besides a firewall and routing.  No DHCP, no DNS, no fancy addons, no VPN.  They should do routing and firewalling, nothing else.  Sure, there are 500 packages that can be installed on our edge routers now, but just because something is possible, that doesn't make it a good idea.

Thanks TheFu, I still find VPN very confusing so have been doing some research but this confuses me even more !

So for my 1st requirement where I want to hide my IP:

[LIST]
[*]I need to use a VPN service provider, whether that be a free service (such as OpenVPN) or paid for service (such as NordVPN) ?  But the free VPNs are not as secure as the paid VPNs as the free VPNs sell you're data ?
[*]The VPN either either runs as a client on the device (laptop, desktop, phone, tablet etc) or on a router that supports VPN ?
[*]My Fritzbox router supports IPSec and Wireguard, but you're saying not to run VPN on this router and instead use another VPN router such as the TP-Link ER605 I mentioned ?
[/LIST]

For my 2nd requirement where I want to securely connect to my parents iMac for offsite backups:
[LIST]
[*]Is a VPN service required for this too ?
[/LIST]

After some research I have found a few VPN providers, Private Internet Access or Torgaurd, I was thinking of going with Private Internet Access.

If I went with Private Internet Access, would the following setup meet my two requirements ?


[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293205&stc=1[/IMG]

---

### Post by TheFu on 2023-12-15
> **freeflyjohn said:**
> Thanks TheFu, I still find VPN very confusing so have been doing some research but this confuses me even more !


That's not unusual.  Just keep track of the clients and the server.

> **freeflyjohn said:**
> 
So for my 1st requirement where I want to hide my IP:

[LIST]
[*]I need to use a VPN service provider, whether that be a free service (such as OpenVPN) or paid for service (such as NordVPN) ?  But the free VPNs are not as secure as the paid VPNs as the free VPNs sell you're data ?
[*]The VPN either either runs as a client on the device (laptop, desktop, phone, tablet etc) or on a router that supports VPN ?
[*]My Fritzbox router supports IPSec and Wireguard, but you're saying not to run VPN on this router and instead use another VPN router such as the TP-Link ER605 I mentioned ?
[/LIST]

OpenVPN is the name of a software package, not a service.  Nearly all VPN providers use either OpenVPN or Wireguard as the software package. These "providers" run the server.  You can run your own server.  There are free VPN services, which shouldn't be trusted.  Heck, some of the paid VPN services cannot be trusted either.  "Trusted" depends on what you need/want.  

> **freeflyjohn said:**
> 
For my 2nd requirement where I want to securely connect to my parents iMac for offsite backups:
[LIST]
[*]Is a VPN service required for this too ?
[/LIST]


There are lots of different ways to connect to your parent's machine, but if you have a VPN server you are already using (that you control), why not use that secured tunnel?  If you are using a paid VPN, this won't be possible and you'll need to setup either "push" or "pull" connections - one side of that connection will need to be "public" and it is easier if 1 side has a static, public, IP.

> **freeflyjohn said:**
> 
After some research I have found a few VPN providers, Private Internet Access or Torgaurd, I was thinking of going with Private Internet Access.

If I went with Private Internet Access, would the following setup meet my two requirements ?

Only you can decide if you trust those providers.  I used PIA for a few years, then they were bought by a company who I considered to be less-than-trustworthy.  YMMV. Only you can decide if they  meet your trust requirements and whether **any** paid or free VPN service is worth trusting or not.

You seem to think a router is required to run a VPN service. That is NOT the case and I'd never recommend putting any VPN server onto a router.  Only you can decide if that is something you think is necessary.  Lots of people choose to reduce their security by running extra stuff on their routers.

I'm not a fan of TPLink.  I've had some bad outcomes with their routers.  If they sell a dumb switch, that could be fine, but even a managed switch, I'd rather not have from them anywhere in my network.  It is a matter of trust.

---

### Post by freeflyjohn on 2023-12-16
Thanks again TheFu, I'm slowly starting to make a bit more sense out of VPN.  I now understand that OpenVPN is a protocol used by a VPN server which could run on my own server or a commercial server where you pay the provider a subscription.


> **TheFu said:**
> That's not unusual.
There are lots of different ways to connect to your parent's machine,  but if you have a VPN server you are already using (that you control),  why not use that secured tunnel?  If you are using a paid VPN, this  won't be possible and you'll need to setup either "push" or "pull"  connections - one side of that connection will need to be "public" and  it is easier if 1 side has a static, public, IP.


So could I install OpenVPN on my Ubuntu Dell machine and use that to connect to my parents machine and would this be a safe and secure connection ?  Or should OpenVPN be ran on a different piece of hardware rather than Ubuntu running on my Dell machine ?  

You stated that this wouldnt work if my server was using a paid VPN, so the easiest solution would be to temporarily disconnect from the paid VPN whilst connecting to my parents machine using my own OpenVPN server ?  Or is it easy enough to setup these push or pull connections whilst still connected to a paid VPN and how does this work (presumably I still would need OpenVPN running on my server) ?  

I've used VPN before to connect to the office server when working from home and I guess this is what I am trying to achieve between my house and my parents house.  The IT guy at my last company said he used OpnSense, should I look at running OpnSense or OpenVPN on my server ?

> 
You seem to think a router is required to run a VPN service. That is NOT  the case and I'd never recommend putting any VPN server onto a router.   Only you can decide if that is something you think is necessary.  Lots  of people choose to reduce their security by running extra stuff on  their routers. 

I guess what I'm asking is should I use a software VPN or hardware VPN ? I assumed that a VPN router would be a hardware VPN, which would be better as its dedcicated and faster at performing the encryption/decryption?  Should I use a software VPN or hardware VPN ?  I've heard that you can run VPN on a Raspberry Pi for example.

> 
I'm not a fan of TPLink.  I've had some bad outcomes with their routers.   If they sell a dumb switch, that could be fine, but even a managed  switch, I'd rather not have from them anywhere in my network.  It is a  matter of trust.

Is there a VPN service provider and a hardware VPN (unless a software VPN is suitable) that you can recommend ?

---

### Post by TheFu on 2023-12-16
> **freeflyjohn said:**
> Thanks again TheFu, I'm slowly starting to make a bit more sense out of VPN.  I now understand that OpenVPN is a protocol used by a VPN server which could run on my own server or a commercial server where you pay the provider a subscription.

That's true. There are other, perhaps better (for certain values of "better", VPNs.  Consider IPSec and Wireguard.
I stopped using OpenVPN a few years ago and switched to Wireguard.  It is 100x easier to setup and faster for transfers.  IPSec is what most enterprises use - I suppose SSL-based VPNs have been cracked by state operators, we know 100% that some states have cracked TLS v1.2 and all earlier protocols, for example. While there hasn't been any announcement about TLS v1.3 being cracked, it has been out long enough that I find it easy to believe it is also cracked at this point.

> **freeflyjohn said:**
> 
So could I install OpenVPN on my Ubuntu server and use that to connect to my parents machine (to perform offsite backups) and would this be a safe and secure connection ?  Although you stated that this wouldnt work if my server was using a paid VPN, so the easiest solution would be to temporarily disconnect from the paid VPN whilst connecting to my parents machine using my own OpenVPN server ?  Or is it easy enough to setup these push or pull connections whilst still connected to a paid VPN and how does this work (presumably I still would need OpenVPN running on my server) ?  

If you run a VPN server, that system needs to have an open port available to the world.  Do you really want to do that to your parents?  Also, while not mandated, having a static IP where the VPN server runs really is required.  I suppose using a dynamic DNS service to keep up with the current, public, IP, for VPN clients would work.  I have a VPS running at a cloudy provider for $4/month that does this for me. It has a static IP.

Whether anything is "easy" or not, depends on your skill and understanding.  I can bring up a new wireguard VPN server on a random VPS in about 3 minutes, but it took much longer to figure out the minimal details to make that possible.

For connections between you and your parents, you could just use ssh-based tools. Nearly all backup software on Linux works over ssh. Then you've split the problem into 2 separate parts - VPN-side and backup-side.

> **freeflyjohn said:**
> 
I've used VPN before to connect to the office server when working from home and I guess this is what I am trying to achieve between my house and my parents house.  The IT guy at my last company said he used OpnSense, should I look at running OpnSense or OpenVPN on my server ?

Using a VPN isn't the same as running a VPN or setting up a mesh network with a VPN.
I use OPNSense on my router. No way would I run a VPN on it and I won't use openVPN at all due to the complexity.  OPNSense is just a router distro that runs on x86-64 systems using BSD as the base OS.  There are linux-based router OSes like OpenWRT and DD-WRT and probably 20 others, some commercial.  Don't confuse router software with a VPN.

> **freeflyjohn said:**
> 
I guess what I'm asking is should I use a software VPN or hardware VPN ? I assumed that a VPN router would be a hardware VPN, which would be better as its dedcicated and faster at performing the encryption/decryption?  Should I use a software VPN or hardware VPN ?  I've heard that you can run VPN on a Raspberry Pi for example.


What?  Hardware VPNs are for enterprises. Do you need to support 5000 concurrent VPN connections?  Those devices have specialized chips to handle the encryption load.  Today, a router is just a computer with some extra ethernet ports.  All VPNs that we'd have for home use are software.  
Running a VPN on a raspberry pi.  Sure, you can do it, but why?  I'd rather see you setup a virtual machine inside a physical computer, load a minimal OS into that VM, and load wireguard into it.  wireguard is very light and it can use CPU-based encryption extensions which nearly any non-toy CPU provides.

> **freeflyjohn said:**
> 
Is there a VPN service provider and a hardware VPN (unless a software VPN is suitable) that you can recommend ?
No. I'm not in the market and decided long ago that none met my needs for trustworthiness and price.  I can spin up a VPN for the few days a month that I need one in just a few minutes, pay $0.20 for that CPU time, then destroy the system.  It is an on-demand VPN.  Last month, I probably needed a VPN less than 10 hours total, so it was under $0.50 in costs.  Any approximate cost is $1/week, if I run it 24/7.

---

### Post by freeflyjohn on 2023-12-16
Thanks TheFu

> 
Also,  while not mandated, having a static IP where the VPN server runs really  is required.  I suppose using a dynamic DNS service to keep up with the  current, public, IP, for VPN clients would work.  


OK, my server has a static IP address so thats a good start.

> 
For connections between you and your parents, you could just use  ssh-based tools. Nearly all backup software on Linux works over ssh.  Then you've split the problem into 2 separate parts - VPN-side and  backup-side.


I already use ssh with rdiff-backup for doing backups on my local network, so I planned to do the same with the offsite backup at my parents house where their machine would pull the data from my server (you actually helped me get rdiff-backup working a few years ago on this forum).

Stupid question.... if I am running the VPN server then does that mean that my parents machine would connect to my VPN server using a VPN client running on their machine ?  I assume it wouldnt work the other way around i.e. I wouldn't be able to connect from my server to their machine using VPN, because its my machine thats running the VPN server ?

> 
Using a VPN isn't the same as running a VPN or setting up a mesh network with a VPN.

Yes I realise that, I was just explaining that I've used VPN to connect to office servers and I am trying to implement the same setup between my house and my parents house.  The companies I've worked for have taken cyber security very seriously, one company worked on military projects so security had to be even tighter and meet cyber essentials.  Yet they still used VPN to connect to the office servers, so if I can setup the same thing I can be reassured about secuity (or am I being naive ?).

> I use OPNSense on my router

Whats the reason for doing this out of interest and do you recommend I should consider this ?  I dont know anything about OPNSense, I just know my company used it and I'm always keen and intersted to do what I can to protect my server.

> 
What?  Hardware VPNs are for enterprises. Do you need to support 5000 concurrent VPN connections?

OK understood, in that case a software VPN would be fine as I dont need concurrent connections.

> 
I'd rather see you setup a virtual machine inside a physical computer,  load a minimal OS into that VM, and load wireguard into it.  wireguard  is very light and it can use CPU-based encryption extensions which  nearly any non-toy CPU provides.

Interesting, this sounds like a possible solution then.  So wiregaurd is a better alternative to OpenVPN ? 

This is where I'll have another learning curve.... virtual machines !  There I was, just thinking I could install a VPN (or wiregaurd) server onto my existing Ubuntu installation running on my server.  But from your suggestion of using a virtual machine and seeing that OPNSense needs to run on a separate piece of hardware or virtual machine, I'm beginning to think that you shouldn't (or maybe even can't?) install these things onto an existing Ubuntu installation ?  They have to be on a new machine, whether that be a new piece of hardware or a virtual machine ?

Whats the reason for using a virtual machine in this case, is it for security or simply that these things have to run on a seperate machine ?

I'm curious about how to do this, my only experience of virtual machines  is using Parallels Desktop on my Mac Book Pro which can run Windows and Ubuntu. I've never setup a virtual machine of my own before.  A quick google search for 'Ubuntu virtual machine' says...

"As a Linux based OS, Ubuntu supports a wide range of virtualization solutions. Aside from popular third-party apps, such as VirtualBox and VMWare, the Linux kernel has its own virtualization module called KVM (Kernel-based Virtual Machine)"

What virtual machine should I use and what OS should be installed on that virtual machine so that I can use wiregaurd ?

---

