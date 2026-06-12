---
title: "Building an Ubuntu server - serveral questions regarding PCI-E cards &amp; sleep/hib mode"
date: 2023-02-08
forum: General Help
---

### Post by richd1011 on 2023-02-08
Dear Ubuntu users/fanatics, 

1st: English is not my first language so there might be some weird grammatical errors within my text :) 

So for the last 10 years i have been using a Synology NAS, and it worked great for the purposes i used it for.
However the system did have it restraints, 4 bays and i was full (so the only option was going for bigger disks) and with 1 transfer going the CPU & RAM was almost 100% in use. it didn't support Plex and lately i have been tinkering with VM's a bit (which it also didn't have support for). 

So i was looking for something with a bit more power. 
Since i build my own Gaming PC about 1,5 years ago (which i really enjoyed) i was like: why not also build a DIY NAS? 
Well looking for OS'es i think i want to go for an Ubuntu based system. 

I already have some basic knowledge of Ubuntu, i have used it in the past to access drives when Windows would'nt boot for example, or to format drives into specific formats that Windows does not support. 

while i am still looking into it some things (like if i am going for Ubuntu Server or Ubuntu Desktop made into an server / the exact specifications i need on the hardware) i was wondering the following things: 

1. My house is fully gigabit cabled, so when transferring files to my current NAS it does so with a speed of about 110-120mbs. 
i mainly transfer files from my windows system to my NAS, so if possible i would like that connection to be a bit faster. 
So a random idea i got: if i stick a 2,5gb network card in the PCI-E slot of my PC and my Ubuntu based NAS and run a Cat6 cable directly between the 2, would that work to establish a faster connection between the 2? is such a thing relativly easy to set-up?
For all other connections the NAS will also have gigabit connection on the motherboard itself that will be plugged into my network splitter. 

2. Does Ubuntu support sleep/hibernate mode? sometimes i access my NAS multiple times a day and sometimes i do not access it for a whole week. 
So energy wise i think it would be nice if it supports sleep/hibernate mode and wakes up when my PC (SMB) or TV (Plex) tries to access it. 

Maybe there will be more questions coming, but if anyone can help me out with the first 2 that would be much appreciated!

---

### Post by TheFu on 2023-02-08
Your English is excellent as far as this native speaker can tell. Much better than I am in any non-English language (I know some of 3 other languages) and tool classes in each. ;)

> **richd1011 said:**
> 
1. My house is fully gigabit cabled, so when transferring files to my current NAS it does so with a speed of about 110-120mbs. 
i mainly transfer files from my windows system to my NAS, so if possible i would like that connection to be a bit faster. 
So a random idea i got: if i stick a 2,5gb network card in the PCI-E slot of my PC and my Ubuntu based NAS and run a Cat6 cable directly between the 2, would that work to establish a faster connection between the 2? is such a thing relativly easy to set-up?

You won't exceed the slowest part of your network connectivity.  Haven't a NIC with 2.5Gbps can't make a GigE switch/router faster.  That would be the limiting factor, assuming you used CAT6 cables that were rated for the higher speeds.  Direct connections don't "automatically" work.  You'd need to setup dedicated routing between both systems.  I'd pay $100 for a 2.5Gbps router to avoid that, assuming one can be had for that price, unless you really like to know how IP networking works.  Let's just say - a DHCP server and a router are amazing things and you should WANT to use them.

But, if you like pain, you can directly connect 2 systems, manually setup IPs, manually setup routes, and manually setup hostnames for the specific IPs (different from the other names you use on the network to see things).  Network/DNS names must be unique for each IP.

> **richd1011 said:**
> 
For all other connections the NAS will also have gigabit connection on the motherboard itself that will be plugged into my network splitter. 

Not sure I know what a "network splitter" is.  Do you mean a switch?  A switch without a router is only slightly more convenient.

> **richd1011 said:**
> 
2. Does Ubuntu support sleep/hibernate mode? sometimes i access my NAS multiple times a day and sometimes i do not access it for a whole week. 
So energy wise i think it would be nice if it supports sleep/hibernate mode and wakes up when my PC (SMB) or TV (Plex) tries to access it. 

The issues with sleep aren't that of ubuntu, but of the hardware and BIOS of the computer.  Hibernation really shouldn't be used.  Again, it is dependent on the hardware in the system supporting it.

SMB!!!!!!   NOOOOOOOOOOOOO!   I joke.  Of course, if your clients are all MS-Windows, then you'd probably want to use CIFS and at least version 3 or better.  For any Unix-based OS, use NFS.

Plex clients can access the plex server directly.  I suppose suggesting that you replace Plex with Jellyfin which is a F/LOSS media center that respects your privacy won't go far.  Just be aware that Jellyfin exists, doesn't need payment, has good clients for nearly any platform, has better support for audio file codecs than plex does and it doesn't send tattle on users about everything they listen and watch back to the Plex mothership.  

> **richd1011 said:**
> 
Maybe there will be more questions coming, but if anyone can help me out with the first 2 that would be much appreciated!
I leave my Jellyfin/NAS on all the time, but that's because it is also the network main backup server and runs a number of Linux containers and VMs.  Backups happen overnight.  I used to use Plex.  Jellyfin connects to my OTA TV tuners and supports recording TV ... no added cost, like Plex.

In 2012, my media center was a $100 AMD E350 box with a 4TB HDD. It couldn't handle playback of 1080p content or do any transcoding, so ... 

In 2015, I replaced it with a $126 Pentium G3258 system and started adding HDDs over the years.  Then an external array.  the Pentium could transcode 1 stream and was running a few VMs fine.  

Eventually, I had too many computers (again) and wanted to consolidate back down to 2 main systems, 1 laptop, and a few media playing devices around the house.  About 14 months ago, I swapped the Motherboard+CPU+RAM in the same case for a Ryzen 5600G (65W).  Passmarks were around 3500, now nearly 20,000.  About 10 HDDs are connected ... 6 internal and 4 external in a disk array connected via eSATA-PM.  About 50% of the storage is used as delayed backups.  I'm down to 3 computers again.  Just need to migrate off a 2010 Core i5 that does some backups for old systems still and is running some internal-only CGI websites and a RAID array.

All of these have some version of Ubuntu on them.  If you aren't really good with Linux, you'll want a light desktop.  I've been a Unix/Linux admin for 30 yrs, so doing things like this myself isn't a major undertaking.  However, for someone who isn't an admin and just wants things to work, I'd strongly suggest not rolling your own from a general OS like Ubuntu.  

Find a NAS+hypervisor distro, perhaps TrueNAS, and load that up. [https://www.truenas.com/truenas-core/](https://www.truenas.com/truenas-core/)   TrueNAS is built on Linux and ZFS.  It supports KVM VMs and Linux Containers which are a lighter way to do things.  There are containers packaged for TrueNAS like Plex Server, NextCloud, and a few others.  I think every family should have a LAN-only Nextcloud server.  They also make setting up a VPN for your family to use relatively easy and it will be secure enough to provide access to the home LAN/Storage to your family from anywhere in the world.  [https://www.truenas.com/docs/core/gettingstarted/corehardwareguide/](https://www.truenas.com/docs/core/gettingstarted/corehardwareguide/) has the minimum hardware requirements, but if you are building your own, you can make a pretty capable server for about $400, if you have a case and PSU to reuse.

I'd honestly worry less about network speed and more about everything else.  BTW, a new MB will likely ship with a 2.5Gbps NIC.  I'd strongly push you to get an Intel NIC on the motherboard and avoid RealTek.  Intel NICs handle more of the packet pushing work and are just better supported for more OSes.  With Linux, the easiest way to get good hardware that will be supported is to look for hardware that has BSD (OpenBSD) support, then Linux support is nearly guaranteed.  You'll get lazy, we all do and you'll get burned with hardware that is nasty towards Linux, we all do.  Life is too short to deal with crappy hardware that doesn't just work.

---

