---
title: "2 cores 4 threads processors?"
date: 2022-06-28
forum: General Help
---

### Post by josephchrzempiec on 2022-06-28
Hello, I have a 2 core 4 threads processor. An athlon 3000g processor. It any much but i Would love to turn it into a Router and NAS storage all in in one. Being that it’s 2 cores and 4 threads how would this work? If I put in pfsense then I can not use it as an NAS system. And if I load Ubuntu on it for an NAS system I can not run a router on it. Or can I do both under Ubuntu, Is there a way? I’m sorry software is not my strong suit. I’m on the hardware side of thing.


P.s.s the motherboard I have has only one pcie slot 16x and 4 sata ports.I don’t remember the model of it. Im not home at the moment and I would like to use what I have to do both because money is way to tight now. Can someone please help me to figure this out? Thank you  

Joseph

---

### Post by TheFu on 2022-06-29
> **josephchrzempiec said:**
> Hello, I have a 2 core 4 threads processor. An athlon 3000g processor. It any much but i Would love to turn it into a Router and NAS storage all in in one. Being that it’s 2 cores and 4 threads how would this work? If I put in pfsense then I can not use it as an NAS system. And if I load Ubuntu on it for an NAS system I can not run a router on it. Or can I do both under Ubuntu, Is there a way? I’m sorry software is not my strong suit. I’m on the hardware side of thing.


P.s.s the motherboard I have has only one pcie slot 16x and 4 sata ports.I don’t remember the model of it. Im not home at the moment and I would like to use what I have to do both because money is way to tight now. Can someone please help me to figure this out? Thank you  

Joseph

There are many things that are *possible* and there are many things that are terrible, terrible, terrible ideas.  Don't mix a WAN router and NAS on the same hardware. Don't.  Just don't.  

**Don't use a VM for your WAN router either.  Don't.  It is a terrible idea.**

Now, if this will be a LAN router and you have a separate WAN router that is fully secured, then I say go for it. Mix whatever you like.  Set up different VMs and run 1 for the LAN router and the other for a NAS devices.  On the router-side, you'll want to have at least 2 LAN ports dedicated via PCI passthru just to the router VM.  Don't mix a bridge for the NAS with those router ports.  

Of course, this assumed you have dedicated hardware for the WAN router.  If you don't have dedicated hardware just for the WAN router, stop. Think about the risks (there are many risks) and reconsider.  Not having money for every desire is called "life".

If it were me, I'd make the current box into a NAS and spend $60 on a cheap Ubiquity router that is still supported. I don't know if that still exists.  If you want more control over your router, spend $120 and get x86-64 router hardware from PCEngines and load up OPNSense. By using x86-64 hardware, you'll have continuous updates from whatever F/LOSS router distro you like.  OpenWRT, pfSense, OPNSense and 10 others.

Don't forget that you'll need backup storage too. If you don't have room for backup storage, then you shouldn't make primary storage available either.  They have to happen in pairs.  Primary and backup storage. Make that a rule. Be consistent.

---

### Post by Doug S on 2022-06-29
My main router, dhcp server, web server, is a single linux server. While it is a Debian server at the moment, it used to be an Ubuntu server.

My firewall/router is implemented with an iptables rule set that has evolved over 13 years and is rather complicated. Since I don't care about collateral damage (i.e. inability for someone legitimate to access my web server) I error on the side of DENY, and block several countries (China, Russia, ...) outright. I study the constant, and varied forms of, attacks and probes from the WAN. Diligence is required if want to run your own WAN facing router/firewall.

---

### Post by josephchrzempiec on 2022-06-29
Hello TheFu, thank you very much for the help and information.  I' still kind a new from coding or well not a good coder at all. I can follow directions no problem there. I do have a Wan router but there is no protection on it other then enabling or disabling ports or DMZ. It is a very cheap tp-link router. I been thinking of replacing it with something like opensense or Pfsense. Sense I'm going the ubuntu way I have been thinking of try something from ubuntu. I know a lot of coding is in my future and I'm okay with that. The reason Why I need some type of protection is because I wanted to have a NAS system I can remotely access and locally access that is not on the same IP address of my network. I normally don't open ports I Use VPN for that. I have multiple static IP Addresses I can assign for this setup. 

Basically I'm just trying to build a all-in-one system. I honestly don't have the money to buy another $20 dollar router let alone a $60 dollar router. My setup is like this. I have a cable gateway modem with 5 ports on it. there is no routing or at least I don't know if there is any routing of it MY ISP gave me. There is no web interface and everything is open. So I can plug a router into one of the ports and Assign a Static IP address to that port and put in a second router to another port and also assign a static IP address to that one as well and so forth. 

P.s.s Hello Doug S, Thank you also for the reply back and Help. I was also thinking about something like a firewall system with a NAS and web hosting at the time. A lot to think about and undecided on what to really do to be honest.

Joseph

---

### Post by josephchrzempiec on 2022-06-29
I'm looking around in my closet to see if I have another motherboard and processor. So far no luck. Only parts and empty cases I found processors older Intel one  4 cores 8 threads well without a motherboard and So far no luck on finding any finding.

So this might mean I might be only can using this board and processor I already have.

Joseph

---

### Post by TheFu on 2022-06-29
> **josephchrzempiec said:**
> Hello TheFu, thank you very much for the help and information.  I' still kind a new from coding or well not a good coder at all. I can follow directions no problem there. I do have a Wan router but there is no protection on it other then enabling or disabling ports or DMZ. It is a very cheap tp-link router. I been thinking of replacing it with something like opensense or Pfsense. Sense I'm going the ubuntu way I have been thinking of try something from ubuntu. I know a lot of coding is in my future and I'm okay with that. The reason Why I need some type of protection is because I wanted to have a NAS system I can remotely access and locally access that is not on the same IP address of my network. I normally don't open ports I Use VPN for that. I have multiple static IP Addresses I can assign for this setup. 

Basically I'm just trying to build a all-in-one system. I honestly don't have the money to buy another $20 dollar router let alone a $60 dollar router. My setup is like this. I have a cable gateway modem with 5 ports on it. there is no routing or at least I don't know if there is any routing of it MY ISP gave me. There is no web interface and everything is open. So I can plug a router into one of the ports and Assign a Static IP address to that port and put in a second router to another port and also assign a static IP address to that one as well and so forth. 

P.s.s Hello Doug S, Thank you also for the reply back and Help. I was also thinking about something like a firewall system with a NAS and web hosting at the time. A lot to think about and undecided on what to really do to be honest.

Joseph

A) There's no "coding" involved with anything here. typing commands into a terminal is **not** coding.  At best, it could be scripting, but most people here don't do that either.  

B) I seriously doubt your ISP modem doesn't include routing if there are 4 ports on it.  Look up the manual on the internet. I bet you find that it is a router/modem. You should use the ISP router if that is what it is.  I'd day 95% it is a router and your ISP is probably patching it and maintaining the configuration in a reasonably secure way, unless someone in the house as disabled it.  ISPs don't ship routers in non-secure setups. They just don't.

C) I wouldn't trust TP-Link for routing.  They have a very poor record of patching.  I speak from experience with TP-Link routers. I have one and use it as a dumb switch inside one of my networks.  Everything is disabled on it - no routing, no wifi, no filtering of any sort, since it can't be trusted anyway.  I bought a flagship TP-Link router and they stopped providing firmware updates within 2 yrs, so it is untrusted.  Any router that doesn't get patched at least quarterly shouldn't be trusted.

D) Security matters.  Part of security is using layers. Don't even think about all-in-one solutions.  Those are constantly being proven to be poor at security.

E) If you have multiple static IPs, then you need to learn much more about networking and network security.  There is very little need to have multiple IPs at home these days.  A single IP can be used for 65K uses and an unlimited number of webapps thanks to SSI.  Any cheap, put patched, router can handle port translations. How to do that is spelled out in the router manual ... or in the classes taken by professionals.

You can remotely access your storage using ssh, sftp, scp, rsync, sshfs, by only opening 1 port for ssh.  This is very common and there are well understood methods to secure ssh.  I use ssh much more than I use my VPN(s).  Learn as much about ssh, ssh-keys and authentication as you can.  You'll see why ssh is how nearly every computer on the internet is managed around the world.

You mentioned a VPN.  Are you running a VPN inside your LAN?  I do and have it setup to allow different clients access over the internet and between untrusted LAN subnets.  The VPN doesn't/shouldn't be run on the WAN router.  Forward a port for VPN use to the VPN server on your server LAN.  That's different from the LAN for wifi stuff and different from the LAN for IoT stuff and different from the LAN for trusted desktops. Don't mix any of those together on the same VLAN or even on the same physical wired network. It is very poor security.  Always remember, vlans are logical tagging only. They aren't security.

I suspect you won't listen and that's fine.  I've done what I could to warn against the direction headed.

---

### Post by TheFu on 2022-06-29
Don't let your network become part of this: [https://arstechnica.com/information-technology/2022/06/pro-russia-threat-group-killnet-is-pummeling-lithuania-with-ddos-attacks/](https://arstechnica.com/information-technology/2022/06/pro-russia-threat-group-killnet-is-pummeling-lithuania-with-ddos-attacks/)

---

### Post by josephchrzempiec on 2022-06-29
Hello TheFu, There is maybe some kind of routing but I do not know. My ISP told me I need my own router or routers. Port forwarding as well as dmz hosting. I have a fiber modem come in with there modem box but that is all I have no access to it myself. 

But you are right it's all in terminal. To me it's coding just my opinion and If I have to make up a python script even from terminal it still is coding. One line or 100 lines of something is coding.

I have one computer I remote into on my main network. It is ubuntu and I do have a VPN server on it that I connect to and as well as remote into it that is all. I wanted to keep this on it's own network and not be a part of my main network. That is why I wanted to build a second router. I do see your points and I'm taking them to heart. I did listen to everything you said. I myself unsure what I'm able or not able to do. 

joseph

---

### Post by josephchrzempiec on 2022-06-30
I did figure out I can not run both not on this limit motherboard. However running a NAS system and Putting security on it would be the best way of doing that. Just using a second normal router is maybe the only way to go for now. Sense I'm limited to what I have for hardware it makes it tough to do. I don't use wireless on anything I have unless it is my phone connected to my main network. For this system there will be no wireless wifi. 

I did want to add one thing in. Yes I do have multiple static IP addresses. It came with the deal I made with my ISP as a package deal. So might as well use them right? Normal it comes with one static Ip address. but for $20 dollars more a monitor you get 5 static ip addresses. I'm deadly aware that security matters it is the first thing on my mine when I wanted to build a firewall router. I didn't put that in my original post because it was something to add onto the router itself. The Tp link routers I have will be replaced soon with something with security in it. That will not be for some time 6 to 8 months maybe from now. 

Joseph

---

### Post by HermanAB on 2022-06-30
If this is a learning system and not a critical business system, then you can do it all on one machine.

Note that you can typically get old computer equipment at the local city dump for next to nothing. There is usually an enterprising city worker who rescues stuff.

---

### Post by mIk3_08 on 2022-06-30
> **josephchrzempiec said:**
> I did figure out I can not run both not on this limit motherboard. However running a NAS system and Putting security on it would be the best way of doing that. Just using a second normal router is maybe the only way to go for now. Sense I'm limited to what I have for hardware it makes it tough to do. I don't use wireless on anything I have unless it is my phone connected to my main network. For this system there will be no wireless wifi.
I did want to add one thing in. Yes I do have multiple static IP addresses. It came with the deal I made with my ISP as a package deal. So might as well use them right? Normal it comes with one static Ip address. but for $20 dollars more a monitor you get 5 static ip addresses. I'm deadly aware that security matters it is the first thing on my mine when I wanted to build a firewall router. I didn't put that in my original post because it was something to add onto the router itself. The Tp link routers I have will be replaced soon with something with security in it. That will not be for some time 6 to 8 months maybe from now. 

Joseph

> **josephchrzempiec said:**
> It came with the deal I made with my ISP as a package deal. So might as well use them right? Normal it comes with one static Ip address. but for $20 dollars more a monitor you get 5 static ip addresses.
Wow! This is cool. This IP are very useful specially IOT (Internet Of Things) Web App development and etc. very cool stuff using your machines, device over Internet. Soon, If one up above will provide I will claim it! Someday I have a huge project of this. Right now I'm in the process of starting the project. Internet is a Huge thing.
> **josephchrzempiec said:**
>  I'm deadly aware that security matters it is the first thing on my mine when I wanted to build a firewall router.
Linux have reach very far enough to this field. Of course, in terms of security Linux is Leading the way. You are in the right place. Linux will always at your back just do good on the Internet. You will always be protected. I'm not too good of this but you can study and search around for this. And there are also here in this community that are well knowledgeable to this field. Don't worry the community will always help you. you just have to be more patience. Linux never fail you.

---

### Post by TheFu on 2022-06-30
I have 5 static IPs too.  You actually don't need or want them.
My ISP manages the BGP routing, so I don't accidentally take over all of China's IPs, by accident and bring the internet down. That's pretty common, but it **is** a router and it does provide a LAN subnet that I use for IoT crap.
I passthru a few static IPs to specific systems 1-for-1 NAT.

I'm afraid that my most important point has been missed.


**JUST BECAUSE SOMETHING IS POSSIBLE, THAT DOESN'T MAKE IT A GOOD IDEA.**  


If you insist, I bet others will help.  I've been cracked enough over the decades to know better. Some things just shouldn't be contemplated, even if they can be achieved.  Mixing a NAS with anything as the primary security is one of those things.  Security stuff fails all the time.  We need belts, suspenders, trousers, and pants (aka underwear) to be safe.

A VPN run by someone else isn't something that I'd trust, especially if run on cloudy systems where all traffic can be modified as it enters and leaves the hardware.

Software - ALL SOFTWARE - has bugs. Thousands. Tens of thousands. Hundreds of thousands of bugs.  Each of these degrade security and integrity.  Non-software people aren't aware of how many bugs there are in all software.  

I worked in development, testing, and QA for a long time.  Any non-trivial software has bugs and most of those bugs have security implications.  The more features any system has, the more catastrophic bugs there are to be attacked.  Chances are nobody is out to get you, not personally, but it doesn't take much effect to look for a specific bug across the entire IPv4 internet.  Scanning the entire internet IPv4 address space happens in under 5 minutes these days.  Normal people have no idea that tools like Shodan exist.  Technical people often think that there are only 3 types of internet traffic - udp, tcp, and icmp.  There are many others, which can be abused, while still being completely valid packets.

There are mitigation strategies for most things that we are aware, but the amount of attacks that we are unaware is mind-blowing.

So, please pick one
1) Either a router OR
2) a NAS 
to build.  Not both on the same system. Please.

---

### Post by #&amp;thj^% on 2022-06-30
> **TheFu said:**
> 

but the amount of attacks that we are unaware is mind-blowing.

If they knew it would scare them plumb to death, at the very least raise the hairs on the back of their necks.

---

### Post by Doug S on 2022-06-30
For what it's worth: I have 2 static IP addresses. My ISP supplied device is a modem only. I do router/firewall, as mentioned in an earlier post. I only need one static IP address, similar to TheFu. I use the 2nd one for testing, and consider it insecure at times.

---

### Post by mIk3_08 on 2022-07-01
> **TheFu said:**
>  but the amount of attacks that we are unaware is mind-blowing.
> **1fallen said:**
> If they knew it would scare them plumb to death, at the very least raise the hairs on the back of their necks.
Yeah! This is True. I agree. You should be scared if you are doing it for something isn't right under the law of human nature. (This is a waste.) But if you use it for the purpose of helping every human race I think you should not be scared to that. 
It always feels better/good when you help someone specially when you know it that they need it so badly. Regards and cheers everyone.

---

### Post by josephchrzempiec on 2022-07-07
> **HermanAB said:**
> If this is a learning system and not a critical business system, then you can do it all on one machine.

Note that you can typically get old computer equipment at the local city dump for next to nothing. There is usually an enterprising city worker who rescues stuff.



This is for my personal use. In my homelab. 

Joseph

---

### Post by josephchrzempiec on 2022-07-26
hello all, Sorry for the late reply. I have been having health problems lately and some of it not so good. I just wanted to reply back and not leave everyone hanging. I did put this project of on hold into I was feeling better. I'm now back at it. What I decided to do was leave this 2 core 4 thread system alone as it was used as my router. However I did mange to find a 4 core 4 thread system I have in the Garage I totally forgot it was one of the first Gen i7 motherboard and processor. I'm using that as my file/nas system. I haven't worked on it yet due to the fact of my health problems. As soon as I'm feeling better I will work on the system. Thank you all for the help and trying to help me to figure out this problem. 

Joseph

---

