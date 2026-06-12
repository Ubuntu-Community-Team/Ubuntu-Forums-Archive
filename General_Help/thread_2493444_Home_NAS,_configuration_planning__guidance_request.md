---
title: "Home NAS, configuration planning / guidance requested"
date: 2023-12-15
forum: General Help
---

### Post by Scrumps on 2023-12-15
I put Ubuntu as the prefix, but, this could easily switch between Ubuntu Server and Ubuntu Desktop.

It has been some time since I have built a Ubuntu NAS system, my last build is about 9 years old (I think it was originally build with 16.04), and had constant hardware upgrades - but never a new build, though it is now running Ubuntu 22.04.X. But because of the large period of time that has elapsed, I wanted to do a brand new system, and update the architecture and infrastructure to be more modern, to make it easier to manage with some of the newer software that has come out.

Currently, the plan is to have:

[LIST]
[*]Ubuntu Desktop / Ubuntu Server 22.04 or 24.04 (whatever is available at the time of finishing and completing the build)
[*]Anything that can be dockerized, will be.
[LIST]
[*]Any service that isn't fundamental to the Operating System, my hope is, can and will be dockerized. For example, things like SMB/Samba, Plex, Hardware Monitoring tools, etc
[*]Right now, I have about 20 Dockerized Services
[/LIST]

[*]Have 100 TB ZFS pool, debating putting a SLOG, ZIL, or L2ARC on an Optane Drive
[*]Have a nvme "cache" drive for the services running on Docker (I have found that with my older NAS, the ZFS pool is not sufficient for data IO)
[*]Running the main OS on USB (or I might re-purpose an old 2.5 SSD).
[/LIST]

Current Hardware is:
[LIST]
[*]MSI Z790I Motherboard
[*]13600K
[*]64 GB of RAM (non-ECC)
[*]1x 2TB NVME drive
[*]1x Intel Optane Drive (128GB)
[*]5x WD Red Pro 22TB drives
[*]Silverstone SATA Expander NVME Card
[/LIST]

With that said, some of the features I am looking to do that I need advice on:
[LIST]
[*]Use guacamole to have a desktop interface if I ever need it / for ease of use when hooking up physical devices to the NAS
[LIST]
[*]Ideally, that doesn't attach to the main display, but auto creates a new session when authorized and authenticated and rebinds to existing display sessions where possible
[/LIST]

[*]Run a 100TB ZFS pool
[LIST]
[*]What is the most optimal configurations for ZFS now a days?
[*]Being used for photos, large file storage (EG: PSD, Video Editing), pdf documents
[/LIST]

[*]Hardware Monitoring
[LIST]
[*]Best use cases for SMART Monitoring, Power Efficiency Tweaking, Fan Speed tweaking, etc
[/LIST]
[/LIST]

And these are the things I need help with planning, not necessarily the whole configuration and everything - I have already written up the docker compose configuration for several of the services I plan on running/using, but for the services that are going to run on the bare metal OS, just understanding how I can achieve it or what is the most optimal way to configure it through the configuration files or new packages that may be have been released, or maybe to learn about some new configuration options that were not previously available 7 years ago.


For ZFS:

As an example, I have been reading several more recent posts:
[https://forums.servethehome.com/index.php?threads/zfs-slog-zil-drives-in-2023.40773/](https://forums.servethehome.com/index.php?threads/zfs-slog-zil-drives-in-2023.40773/)
[https://www.reddit.com/r/zfs/comments/12dywm2/now_that_intel_stopped_making_optane_what_are_the/](https://www.reddit.com/r/zfs/comments/12dywm2/now_that_intel_stopped_making_optane_what_are_the/)
[https://www.servethehome.com/what-is-the-zfs-zil-slog-and-what-makes-a-good-one/](https://www.servethehome.com/what-is-the-zfs-zil-slog-and-what-makes-a-good-one/)

And it seems like the idea of having the ZIL or SLOG is overall better, though I am not entirely sure if there are any performance tweaks, or changes I need to make in any of this configuration for the intended use case. 
The last time I built the ZFS pool above, I got heavily invested in needing to tweak very specific ZFS settings, but, not sure if that is still needed now a days for home nas use? If I was running a production business-critical system, I would imagine so.

For Guacamole:

Honestly, I am not sure where to begin. I am aware that Ubuntu can run a desktop environment over a VNC port or equivalent, but, not sure if there is newer protocols that can be used to also provide sound, better UX capabilities (such as file transferring, copy paste, etc). 

I have been reading: 
[https://guacamole.apache.org/doc/0.9.2/gug/installing-guacamole.html](https://guacamole.apache.org/doc/0.9.2/gug/installing-guacamole.html)
[https://www.linuxbabe.com/ubuntu/apache-guacamole-remote-desktop-ubuntu-20-04](https://www.linuxbabe.com/ubuntu/apache-guacamole-remote-desktop-ubuntu-20-04)
[https://www.linode.com/docs/guides/installing-apache-guacamole-on-ubuntu-and-debian/](https://www.linode.com/docs/guides/installing-apache-guacamole-on-ubuntu-and-debian/)

And honestly a few others, I also just don't want to keep posting links - as I am worried it might flag a spam filter or something, but, what I see are a lot of things focusing solely on just getting the web interface and VNC or RDP session up and running, and not focusing on extra or additional features (such as file transfer, copy / paste, or audio). Are there any guides or anything that I need to go out of my way for to get up and running on the host itself (I had planned on running Guacamole on a container). 

I think the hardest / most difficult situation here, is that I want Guacamole to spin up new desktop environments rather than connect to the main display session, and when reading - it seems that most people are connecting to the main session.


For Hardware Monitoring / Tweaking:
I am honestly trying to keep this very simple, I don't expect to run TIG, ELK, or any other stack initially, but, I do want decent hardware monitoring and alerting for basic things like:
[LIST]
[*]SMART status / failures
[*]Temperature / Overheating Issues
[*]Power Consumption tweaking
[/LIST]

For SMART tools, I have looked at services like Scrutiny ([https://github.com/AnalogJ/scrutiny](https://github.com/AnalogJ/scrutiny)), and it looks like it would work well, but, as I have not been able to test it out yet - not sure if it can also send email alerts, hook into push notification services, use webhooks, etc. So not entirely sure if I need to actually do anything.

For temp monitoring, I was thinking of using NetData initially, and then when I have the time / priority to run TIG/ELK effectively, then switch over to that. But is there anything specific that anyone could recommend?

Power Consumption tweaking, I used powertop quite some time ago (even before the older NAS build), but, am not sure if it is still maintained or useful? ArchLinux's site seems to have documentation on it still, but, is there anything that needs to be done with it, other than running it with --auto-tune flag?


I am sure I am overthinking or over planning, a lot of this stuff, but, just trying to be thorough in what I am doing and researching - so I can have a fairly stable and long lasting system that I won't have to break-fix a lot of the time. 

Really appreciate any solutions or offers for advice here, I might have some more questions as I come closer to finalizing the build.

---

### Post by TheFu on 2023-12-15
You've made some choices that I'd never make for different reasons.

I'd never use docker over security defaults that undermine the best aspects of Linux containers. I'd use lxd/lxc instead. By default, lxc is more secure. [https://cheatsheetseries.owasp.org/cheatsheets/Docker_Security_Cheat_Sheet.html](https://cheatsheetseries.owasp.org/cheatsheets/Docker_Security_Cheat_Sheet.html) is a start.

I left Plex to gain more privacy.  Jellyfin is the replacement and has much better support for F/LOSS audio files, if that matters to you.  The layout for media is basically the same.  Jellyfin isn't as polished, but it does easily hook into OTA recording if you have HDHR hardware.  I always disliked the Plex playback clients.  They were slow and bloated on my systems and didn't play 90% of my audio files.  Jellyfin has clients and DLNA support, so my playback devices are raspberry pi devices.  1 supports 4K playback and the other just 1080p.  Considering I don't have any 4K screens in the house, it isn't THAT important to support 4K, but new video hardware I've bought the last year all supports 4K @ 60 HZ for the day that happens.  I've been watching for a 36inch-42inch 4K monitor a few years.  We don't have TVs and our projectors are 720p, 720p, 1080p and 1080p devices.  75 inch screens just seem too small.

I see no mention of backup storage.  Backups are more important than any RAIDx level.  Sometimes the only fix for a corrupted RAID system is to wipe it and restore from backups.

Remote desktop - on the same LAN, just use **ssh -X**. Over the internet, use x2go or another NX-based tool.  Avoid RDP or VNC for their less than good lack of security.  Similarly, I'd never, ever, make a remote desktop on a webserver.  That's just asking to be hacked.

For monitoring, I use munin and SMART.  2 sides of the same need.  Because I'm on Ryzen CPUs, temperature monitoring is completely different than for Intel CPUs.

If you don't need a desktop, don't install one. They just make more software less secure and reduce overall support periods.

I don't know what a "13600K" is.  Is that a Core i3?  What are the passmarks?  I moved from a 3500 passmark system to a 19500 passmark system to better support transcoding for different clients.  I don't have any RAID at all on my VM+NAS.

We don't use Samba, just NFS.  NFS is built-into the kernel, so it is native-fast to my other clients, especially media clients.  All our playback devices are wired. I used to deploy wifi for companies and learned to never use wifi unless there is no other choice.  Connecting floors of the house, I use powerline, though I'd happily switch to 2.5Gbps MoCA if I needed more bandwidth. Most rooms here have coax already.  The drop in powerline performance between rooms and floors is so bad as to not be funny, but it is stable bandwidth, which matters for streaming use.

I've had a few WD-Red drives fail over the years.  About 4 yrs ago, I stopped buying RED and switched to Black for primary storage.  I only use USB storage for backup use, never primary storage.  Infiniband, eSATA and SATA storage for primary.  

I don't have as much storage as you, but a respectable 40TB+.  About 50% of that is for backups.
I like the idea of ZFS, but still use LVM+ext4.  The file systems are limited to 4TB chunks, since that was what I could easily backup using K.I.S.S. methods.

My 2 physical systems are nearly identical and use less than 50% of the CPU on each, with the intent that when 1 fails, the entire load will run on a single system as replacement/upgrade parts are shipped.  Same RAM, same CPU, same on-board iGPU, same libvirt virtual devices setup (bridges), NICs, etc.

For my photos, I have a customized website that I modified for my specific needs.  It runs under a virtual machine, not a container.  That VM is also my reverse proxy for nearly all the websites I host for internal/external views.  For example,  I have a nextcloud LXC using the nextcloud snap package.  Nextcloud isn't available outside the LAN, without using my self-hosted VPN (wireguard).  With a remote client on wireguard from anywhere in the world, I have full access, just like being on the LAN. This works for Jellyfin, nextcloud, and about 20 other websites and other servers, like email.  I do have an email gateway system that handles all inbound/outbound SMTP, but doesn't actually hold any email more than a few seconds or while the main email server is off line for maintenance.

For epub, pdf, and other reference documents, I run Calibre. This hooks into my tablet.  The tablet also connects to a read-it-later clone called wallabag for off line reading of old web articles and recipes I've found.  Taking the tablet into the kitchen for more complex cooking instructions has been good.  My eyesight doesn't work like it did 20 yrs ago, so a phone just isn't large enough.

I'm not about "new". I'm all about "stable" and "secure".

I suspect others will have more ideas for your specific needs.  Just thought I'd share so you know going in a completely different architecture is fine too.

---

### Post by MAFoElffen on 2023-12-16
My recommends... I chose MSI for my own...

Look around at MSI's other Z790 boards... I passed on that one. It only supports 96GB of RAM, has 4 x SATA ports, limited 3 x M.2 gen 3&4 slots and only 1 PCIex16 slot. You say you have 5 20TB drives, but that board only has 4 SATA ports... Using an HBA in the PCIe X 16 slot?

I have an MSI MPG Z790 Edge Wifi. Supports 192GB RAM, 5 x M.2 NVMe slots (Gen 4 & 5), 7 SATA drives (really only 6, 7th is shared w/ NVMe_3) 2 x PCIex16 slots (Gen 4 & 5).

I have 6 SATA's and 9 NVMe drives in it. I have 4 of the NVMe's on a Quad PCIe M.2 NVMe Birfucation Card. ZFS-On-Root. I do my SLOG & L2ARC on NVMe.

Those boards no longer support Intel Optane, as Intel abandoned that technology.

I do a lot of ZFS and have for many years. for 100TB of pool,that would be 8GB based ram and 1GB per TB = for at least 108GB of RAM... You say that board only supports 96GB... 

With 100TB of vdev for that pool. I would do at least RAIDZ2, possibly RAIDZ3. That's about 90TB of max storage cap for that pool. About 72TB before it affects performance. With my tuning test benchmarks, I do ashift = 13 and recordsize = 128K. That gives me the best performance for what I do.

I was trying out Sanoid/Syncoid for backup's, but lately have gone back to my own scripts that do the same with ZFS snapshots, ZFS Send/Recieve to other pools, based on what I want to check and keep track of. My own scripts do better for checking and managing storage spaces. Lessons learned.

---

### Post by TheFu on 2023-12-16
MAFoElffen does point out something important that I completely missed. Use a quality HBA.  That means going with a name brand that is respected.  LSI has some SAS HBAs that I've been watching. If you go with consumer SATA, then each SAS connector supports 4 SATA drives.

When looking for an HBA, I look at what works well and is recommended by the NAS people running BSD-based NAS systems. If it works well with BSD, it almost certainly will work well with Linux.  
"Supermicro AOC-SAS2LP-MV8 Add-on Card, 8-Channel SAS/SATA Adapter with 600MB/s per Channel" and similar have been on my shopping list for some time. Add in some cables and for JBOD connected storage like Linux RAID or ZFS, it will be fantastic.

I have add-on HBAs in my storage systems.  Besides the 6 SATA slots built into the motherboard, my case has room for 10 HDDs thanks to using a few 4 HDD in 3 slot cages.  The cages are hot-swap for convenience.  They make steal and plastic cages like this.  The steal cages aren't hot-swap, but they are cheaper (under $30). I like the plastic ones because they have a caddy system that makes accessing the HDDs simple ... and they have blue lights for each HDD. ;)

---

### Post by Scrumps on 2023-12-16
Apologies if I was unclear, the hardware I already have - and don't have much of an opportunity to return or change it up for some things. That window is closing soon for others RAM, NVME, and Intel Optane drive, WD Red Pro drives are still within the return period. The CPU, Case, Motherboard, cannot be returned now. I could try and resell it in the country I am living in (I am sure it would be a few dollars in profit) but, let's assume I don't in this case for sake of convenience or at least for planning - because the last thing I need is to upend the motherboard and CPU pieces.

The case, which I didn't originally mention, is a Jonsbo N2 case - as dimensions wise, it is the only thing that will fit in the space that I have to work with to not upset anyone :P. So I am limited to a 5 drive bay. I know the Jonsbo N3 exists, but, when measuring the space, I don't think the N3 would have fit, nor do I have the money to buy 8 drives. Which also means I am limited to ITX boards and can't expand on to ATX or similar.

Going to try and tackle some of the key things in the posts above, but, not going to quote everything.

> [COLOR=#000000]I left Plex to gain more privacy. Jellyfin is the replacement and has much better support for F/LOSS audio files, if that matters to you. [/COLOR]

I have thought about, and looked at it - and could run it in tandem - but most of my stuff is built around Plex. Would consider it though, and it is actually commented out currently in my docker file. 

> [COLOR=#000000]I don't know what a "13600K" is. [/COLOR]
It is an Intel i5 CPU. [https://ark.intel.com/content/www/us/en/ark/products/230493/intel-core-i5-13600k-processor-24m-cache-up-to-5-10-ghz.html](https://ark.intel.com/content/www/us/en/ark/products/230493/intel-core-i5-13600k-processor-24m-cache-up-to-5-10-ghz.html)

> [COLOR=#000000]I see no mention of backup storage. Backups are more important than any RAIDx level. Sometimes the only fix for a corrupted RAID system is to wipe it and restore from backups.[/COLOR]
Agreed, some of this stuff that is in the 100TB is not necessary to do backups on, but the stuff that is - goes to an offsite backup system in another country, and also (though limited in backup space) to Google Drive to meet the 5TB requirements they are beginning to implement on accounts. This is primarily for very specific files and content, like Images, PDFs, documents, etc. 

I can always re-rip my music collection or Blu-Ray collection, so I am not worried about the data loss from that. However, photos, and other things will get backed up to offsite/external storage mediums.

> [COLOR=#000000]If you don't need a desktop, don't install one. They just make more software less secure and reduce overall support periods.[/COLOR]

I am thinking the use case is more for when I want to easily hook up cameras, or use software that does require a GUI, or more easily manage the file/folder structure (that CLI could do - but, is clunky with). Honestly, have thought about installing the base Ubuntu Server, and then when/if I feel comfortable or have the need - then installing the DE on top.

> [COLOR=#000000]Using an HBA in the PCIe X 16 slot[/COLOR]
Yes, the plan is to use a Silverstone 5port HBA Adapter in one of the 3 nvme slots ([https://www.tomshardware.com/news/silverstone-turns-one-m2-slot-into-five-sata-ports-ecs07-adapter](https://www.tomshardware.com/news/silverstone-turns-one-m2-slot-into-five-sata-ports-ecs07-adapter)). Alternatively, I could use a PCIE low profile card, but, I figured that the NVME was already in use. 

Any suggestions on that line of thinking (also because of the next quoted piece around the Intel Optane)?

The plan was: Samsung 990 Pro in slot 1, Intel Optane in slot 2, and the Silverstone in Slot 3 (top most slot) - plugging hard drives from the Jonsbo N2 hotplane into the HBA ports. 


> [COLOR=#000000]Those boards no longer support Intel Optane, as Intel abandoned that technology.[/COLOR]

When you say, this, do you mean that the Intel Optane will just not work, or, that the BIOS/UEFI no longer has additional configurations for Optane SSDs? Would it be better off to get another NVME drive for the ZIL/SLOG? Is there a performance hit when it comes to Optane vs NVME? I wouldn't be opposed to getting an NVME based drive, but it seemed like everything I read on ZIL/SLOG was based on Optane. 

> [COLOR=#000000]for 100TB of pool,that would be 8GB based ram and 1GB per TB = for at least 108GB of RAM[/COLOR]
The board in question only has 2 RAM Slots, so at this point, I have maxed it out with what I can find, which is 2x 32GB RAM Slots totalling 64. 

> [COLOR=#000000]I do ashift = 13 and recordsize = 128K[/COLOR]

This is currently something similar to what I did with my old NAS setup I recall, so I guess if that is still the generally approved recommendation, I will keep at it with that. Thanks very much for this bit!

> [COLOR=#000000]MAFoElffen does point out something important that I completely missed. Use a quality HBA.[/COLOR]

I have an Enterprise grade LSI HBA in my old server that I could repurpose, but wasn't planning on using it. Can't recall the exact name at the moment, but, it was one of the commonly found on ebay ones. 9620 or something like it.


EDIT: 

The reason for wanting to avoid the hardware in the current NAS, is that after such a long period of time... it has started to have hardware failure - and I don't have the time, energy, or live where it is - to be able to actually invest in troubleshooting the issue (and it is running ESXi as a host OS with Ubuntu Server as the Guests). So while I can take some hardware from there, if it ends up causing issues in this new build - I won't be able to do much other than take it out, so I don't want to count on any of that as usable hardware.

---

### Post by TheFu on 2023-12-16
You'll want to keep up with VMware ESXi announcements. They completely changed their support model earlier this week.  They tried something massive in 2010 too.  We stopped using VMware stuff the last time they did something like this and actively moved our clients off VMware to save them hassle and money.  

OTOH, if a client can't pay $12K for VMware, how will they ever pay us?  The way clients think - F/LOSS is free and the knowledge to setup using it is somehow less valuable, so it should pay less.  VMware architects were earning $150K+ back then.  F/LOSS architects more like $90K at the time.  Sad, but true. 

I haven't been in the job market in over a decade, does VMware skills return a premium salary still?

When we moved to kvm/qemu + libvirt, all sorts of things just worked.  One of the best decisions I've ever made.  I started in virtualization in the late 1990s. Tried all the options until around 2012 when KVM/QEMU became enterprise ready and just worked. Never looked back.  I certainly don't miss the VMware bills nor the $1000 addon software to make common things workable in VMware.

---

### Post by Tadaen_Sylvermane on 2023-12-16
> I am thinking the use case is more for when I want to easily hook up  cameras, or use software that does require a GUI, or more easily manage  the file/folder structure (that CLI could do - but, is clunky with).  Honestly, have thought about installing the base Ubuntu Server, and then  when/if I feel comfortable or have the need - then installing the DE on  top.

I don't know what you intend to use for software for this. I put together a Zoneminder docker. I don't know if it's any good of course, but it works for me. The entire gui to it is a web interface. I don't use it anymore and haven't for awhile so I'm not 100% that this will build properly. But it's a place to start. This way you don't need to do the DE, at least for cameras and such.

[https://gitlab.com/jmgibson1981/homescripts/-/tree/master/docker/zoneminder?ref_type=heads](https://gitlab.com/jmgibson1981/homescripts/-/tree/master/docker/zoneminder?ref_type=heads)

---

### Post by TheFu on 2023-12-16
Nobody ever _needs_ a DE.  A Window Manager, WM, is all that is needed to have a GUI on Linux.  Often, using just a WM will save 500MB of RAM.
Also, if you plan to use remote access to manage the system, you can use Cockpit webapp (this is actively being worked by Canonical and Redhat) on the LAN or even x2go as a remote desktop over a secure NX connection from anywhere in the world.

---

### Post by MAFoElffen on 2023-12-16
For ZFS performance tuning, search this Forum on my user name. For backups, search on TheFu's username.

Yes, you'll want to keep that large storage pool on the same HBA. Distributing it across multiple bus'es sometimes adds a bottleneck, if you try to stripe them in a RAID array. I really like and believe in ZFS RAIDZ. It's done me well integrity and performance wise.

I mean that new boards don't support Intel Optane any more. Intel abandoned Intel Optane as a project January 2021. Micron sold off the 3D XPoint fab immediately after that in 2021. Any chance of buying those Optane Modules now is quickly drying up. Any board made after 2021, stopped following that offering as a new technology.

You really need to read the MSI Owners Manual in detail. I have with mine. MSI and ASUS tend to hide details about how their PCIe and SATA buses are laid out, and if any of them are shared across the same bus, where if you use an M.2 or SATA in a certain slot, that it turns off other things. That also goes for some M.2 slots only recognizing SATA instead of PCIe M.2 NVMe drives. The tech on that is still new, so on some models they ended up doing some weird things.

96GB is going to be tight for that 100GB pool. Especially if you are storing 4K media. I would tune your ARC to 48GB max limit. The NAS Forums think that it automatically stops at half memory. That is no true. Then do a 1TB L2ARC. I do a 1TB SLOG. I do both those on just on one single 2TB NVMe, with two partitions. The people in the NAS forums will try to tell you that SLOG will not use more than 16GB. I don't know where they got that number. I ignored that, and tested that on my own. (Show me the data!) It not only does use it, the performance kept climbing until the 1TB mark, where anything larger than that, then it crested and started to fall on sizes larger than that. Disk caches will help greatly with your memory.

There's a few trick I have for flushing the caches if you run into a memory problem...

You can still do a lot with what you have. Pay attention to what you have on a gen 3 bus. That board has both Gen3 and Gen 4. Your HDD's will do fine on Gen3. Keep your NVMe's on Gen4.

I don't claim to know everything. I have just been exposed to a lot of things. Lots of those things have been self-inflicted. I've only worked with ZFS since 2005. I tend to want to see things for myself, sometimes to see what really happens when I do something. That has been fun!

---

### Post by Scrumps on 2023-12-17
> **MAFoElffen said:**
> For ZFS performance tuning, search this Forum on my user name. For backups, search on TheFu's username.

Yes, you'll want to keep that large storage pool on the same HBA. Distributing it across multiple bus'es sometimes adds a bottleneck, if you try to stripe them in a RAID array. I really like and believe in ZFS RAIDZ. It's done me well integrity and performance wise.

[QUOTE=MAFoElffen;14169607]
I mean that new boards don't support Intel Optane any more. Intel abandoned Intel Optane as a project January 2021. Micron sold off the 3D XPoint fab immediately after that in 2021. Any chance of buying those Optane Modules now is quickly drying up. Any board made after 2021, stopped following that offering as a new technology.


Hm, yeah, I realized that some special features may be disabled, but, the overall functionality of what the NVME drives had configured without the special software would still assist there.

> **MAFoElffen said:**
> 
You really need to read the MSI Owners Manual in detail. I have with mine. MSI and ASUS tend to hide details about how their PCIe and SATA buses are laid out, and if any of them are shared across the same bus, where if you use an M.2 or SATA in a certain slot, that it turns off other things. That also goes for some M.2 slots only recognizing SATA instead of PCIe M.2 NVMe drives. The tech on that is still new, so on some models they ended up doing some weird things.
[/qutote]

Unfortunately, I have, the only thing I can't figure out specifically with this board on the PCIE side is how it is laid out, but also if it supports splitting or Bifurcation at all. 
[https://www.msi.com/Motherboard/MPG-Z790I-EDGE-WIFI/Specification](https://www.msi.com/Motherboard/MPG-Z790I-EDGE-WIFI/Specification)

Doesn't list anything, nor does: [https://download.msi.com/archive/mnu_exe/mb/MPGZ790IEDGEWIFI.pdf](https://download.msi.com/archive/mnu_exe/mb/MPGZ790IEDGEWIFI.pdf)
The only bit is this: 


SLOT	1x PCI-E x16 slot
PCI_E1 Gen PCIe 5.0 supports up to x16 (From CPU)

But that doesn't go into how the channels are working with the rest of the system, or if there are limitations when everything is enabled/used.

[QUOTE=MAFoElffen;14169607]
96GB is going to be tight for that 100GB pool. Especially if you are storing 4K media. I would tune your ARC to 48GB max limit. The NAS Forums think that it automatically stops at half memory. That is no true. Then do a 1TB L2ARC. I do a 1TB SLOG. I do both those on just on one single 2TB NVMe, with two partitions. The people in the NAS forums will try to tell you that SLOG will not use more than 16GB. I don't know where they got that number. I ignored that, and tested that on my own. (Show me the data!) It not only does use it, the performance kept climbing until the 1TB mark, where anything larger than that, then it crested and started to fall on sizes larger than that. Disk caches will help greatly with your memory.




Any suggestions on the NVME drives? Such as partitioning under the total storage size so that you don't hit any limitations with NVME read / write - or does that matter?

What are your drive writes/endurance looking like after a year, 2 years, 3 years, etc? That was one of the initial reasons I went with the Optane, since it is rated for 1200TBW , compared to the 990 Pros being rated in TB.



> **MAFoElffen said:**
> 
There's a few trick I have for flushing the caches if you run into a memory problem...

You can still do a lot with what you have. Pay attention to what you have on a gen 3 bus. That board has both Gen3 and Gen 4. Your HDD's will do fine on Gen3. Keep your NVMe's on Gen4.

I don't claim to know everything. I have just been exposed to a lot of things. Lots of those things have been self-inflicted. I've only worked with ZFS since 2005. I tend to want to see things for myself, sometimes to see what really happens when I do something. That has been fun!

I might ask you for those, when I am closer to assembling the system.

Yeah, that is the plan, with the current board to have the HDDs on the M2_2 slot,with the rest being on M2_1, and M2_3. 

Fully understand, I mean, everything is a path of learning.

---

### Post by MAFoElffen on 2023-12-17
Forgot... I was looking at those M.2 to SATA adapter cards for another application I was playing with... What I would recommend on that... use is on M.2_2... That is the port that is Gen3, where the other two are Gen4. But... that would actually be the only slot it would really work in because of the way the M.2 slots are laid out on that MB, right.

Mentioning that, I have a question for you, since that is an EU board and I haven't seen that here...

M.2_1 and M.2_2, between the CPU and PCIe slot. M.2_3 is under the MB on the bottom, ending up between the MB and the case. It looks like in the manual, that M.2_1 is from a slot on the MB, but that M.2_2 is on a riser card, that is plugged in, on top of the M.2_1 card(?)... Doing things that way, sandwiching those two M.2 cards *like tha*t, then is the cover on top of those not used as a heatsink. like it is on mine? And having those laid out like that, that would prevent using anything as a heatsink with any M.2 drives on that motherboard right?

EDIT: 
On silicon storage, I tend to stay with Samsung. 

When silicoon storage first came out, I was skeptical about if I could wear a silicon disk out and it's life span... I kept hearing "stories" of the what if's and what might be's. Actually it was my youngest brother who set that to rest for me. His company does stop motion video for a major television network and has a datacenter full of silicon storage, with 70 SSD's per box... And has never ran into that problem. His projected lifespan is 10 years before he rotates those out.

---

### Post by Scrumps on 2023-12-18
> 
since that is an EU board and I haven't seen that here...


I bought the motherboard in the US (on Amazon) and plan on taking it back with me to the EU. Though in the EU, you can also find it on Amazon and other suppliers pages. 

Othewise, not sure where you are seeing EU specific information from. 

> that M.2_1 is from a slot on the MB, but that M.2_2 is on a riser card, that is plugged in, on top of the M.2_1 card(?)... Doing things that way, sandwiching those two M.2 cards like that, then is the cover on top of those not used as a heatsink. like it is on mine? And having those laid out like that, that would prevent using anything as a heatsink with any M.2 drives on that motherboard right?

Yeah, the riser card acts as the heatsink and would prevent the ability to have a heatsink on the SSD itself. TBF, I haven't actually looked at that part of the board yet - the only thing I inspected on the board was if the pins were damaged in anyway before putting it back in the box. But that is the general ideal.

---

### Post by Scrumps on 2024-01-24
Hey all again,

[COLOR=#22231F][FONT=&amp]I finally got all the pieces to build this out, and settled back home. When I initially got the drives, I ran a long test and everything came back fine. Today after getting the rest of the hardware and bringing it overseas before setting it up into a ZFS array, I did another long test and I am seeing a drive fail out and I can't tell if it is the HBA / SATA card, or the drive itself. Attached is a log file of ata12 and /dev/sdf: [/FONT][/COLOR][https://pastebin.ubuntu.com/p/yFJpTMHSqh/](https://pastebin.ubuntu.com/p/yFJpTMHSqh/)

[COLOR=#22231F][FONT=&amp]I was trying to make this a low-power consumption server, so it could be that powertop or a BIOS configuration caused this, but, I just wanted to be absolutely sure that it wasn't the drive itself failing before I dig in any further.

Apart from a restart, what is the best way to "power on" a drive that has been powered off in the error message above, I assume due to udisksctl? I also saw another drive fail with a "SmartSelfTestStatus: Interrupted" message, so my hope here is that the actual NVME to ACHI/SATA adapter is failing, and needs replacement, and not the drives itself. 


The smartctl test results of the Interrupted drive is shown below:

[/FONT][/COLOR]```
=== START OF READ SMART DATA SECTION ===SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x80)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (  37)    The self-test routine was interrupted
                    by the host with a hard or soft reset.
Total time to complete Offline 
data collection:         (    0) seconds.
Offline data collection
capabilities:              (0x5b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    No Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      (2621) minutes.
SCT capabilities:            (0x003d)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAGS    VALUE WORST THRESH FAIL RAW_VALUE
  1 Raw_Read_Error_Rate     PO-R--   100   100   001    -    0
  2 Throughput_Performance  --S---   148   148   000    -    48
  3 Spin_Up_Time            POS---   086   086   001    -    328 (Average 295)
  4 Start_Stop_Count        -O--C-   100   100   000    -    12
  5 Reallocated_Sector_Ct   PO--CK   100   100   001    -    0
  7 Seek_Error_Rate         -O-R--   091   091   000    -    6
  8 Seek_Time_Performance   --S---   140   140   000    -    15
  9 Power_On_Hours          -O--C-   100   100   000    -    54
 10 Spin_Retry_Count        -O--C-   100   100   000    -    0
 12 Power_Cycle_Count       -O--CK   100   100   000    -    10
 22 Unknown_Attribute       PO---K   100   100   025    -    6553700
 71 Unknown_Attribute       P-----   100   100   001    -    0
 90 Unknown_Attribute       P---CK   100   100   001    -    493921239040
192 Power-Off_Retract_Count -O--CK   100   100   000    -    19
193 Load_Cycle_Count        -O--C-   100   100   000    -    19
194 Temperature_Celsius     -O----   065   065   000    -    31 (Min/Max 18/39)
196 Reallocated_Event_Count -O--CK   100   100   000    -    0
197 Current_Pending_Sector  -O---K   100   100   000    -    0
198 Offline_Uncorrectable   ---R--   100   100   000    -    0
199 UDMA_CRC_Error_Count    -O-R--   100   100   000    -    0
                            ||||||_ K auto-keep
                            |||||__ C event count
                            ||||___ R error rate
                            |||____ S speed/performance
                            ||_____ O updated online
                            |______ P prefailure warning


General Purpose Log Directory Version 1
SMART           Log Directory Version 1 [multi-sector log support]
Address    Access  R/W   Size  Description
0x00       GPL,SL  R/O      1  Log Directory
0x01           SL  R/O      1  Summary SMART error log
0x02           SL  R/O      1  Comprehensive SMART error log
0x03       GPL     R/O      1  Ext. Comprehensive SMART error log
0x04       GPL     R/O    256  Device Statistics log
0x04       SL      R/O    255  Device Statistics log
0x06           SL  R/O      1  SMART self-test log
0x07       GPL     R/O      1  Extended self-test log
0x08       GPL     R/O      2  Power Conditions log
0x09           SL  R/W      1  Selective self-test log
0x0c       GPL     R/O  19043  Pending Defects log
0x10       GPL     R/O      1  NCQ Command Error log
0x11       GPL     R/O      1  SATA Phy Event Counters log
0x12       GPL     R/O      1  SATA NCQ Non-Data log
0x13       GPL     R/O      1  SATA NCQ Send and Receive log
0x15       GPL     R/W      1  Rebuild Assist log
0x21       GPL     R/O      1  Write stream error log
0x22       GPL     R/O      1  Read stream error log
0x24       GPL     R/O    256  Current Device Internal Status Data log
0x25       GPL     R/O    256  Saved Device Internal Status Data log
0x2f       GPL     -        1  Set Sector Configuration
0x30       GPL,SL  R/O      9  IDENTIFY DEVICE data log
0x80-0x9f  GPL,SL  R/W     16  Host vendor specific log
0xb7           SL  VS       1  Device vendor specific log
0xd8-0xd9  GPL,SL  VS       1  Device vendor specific log
0xe0       GPL,SL  R/W      1  SCT Command/Status
0xe1       GPL,SL  R/W      1  SCT Data Transfer


SMART Extended Comprehensive Error Log Version: 1 (1 sectors)
No Errors Logged


SMART Error Log Version: 1
No Errors Logged


SMART Extended Self-test Log Version: 1 (1 sectors)
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Interrupted (host reset)      50%        50         -
# 2  Short offline       Completed without error       00%        35         -
# 3  Extended offline    Completed without error       00%        30         -


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Interrupted (host reset)      50%        50         -
# 2  Short offline       Completed without error       00%        35         -
# 3  Extended offline    Completed without error       00%        30         -


SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.


SCT Status Version:                  3
SCT Version (vendor specific):       256 (0x0100)
Device State:                        Active (0)
Current Temperature:                    31 Celsius
Power Cycle Min/Max Temperature:     22/34 Celsius
Lifetime    Min/Max Temperature:     18/39 Celsius
Under/Over Temperature Limit Count:   0/0
SMART Status:                        0xc24f (PASSED)
Minimum supported ERC Time Limit:    70 (7,0 seconds)


SCT Temperature History Version:     2
Temperature Sampling Period:         1 minute
Temperature Logging Interval:        1 minute
Min/Max recommended Temperature:      0/60 Celsius
Min/Max Temperature Limit:           -40/70 Celsius
Temperature History Size (Index):    128 (53)


Index    Estimated Time   Temperature Celsius
  54    2024-01-24 12:24    31  ************
  55    2024-01-24 12:25    31  ************
  56    2024-01-24 12:26    31  ************
  57    2024-01-24 12:27    32  *************
  58    2024-01-24 12:28    31  ************
 ...    ..( 96 skipped).    ..  ************
  27    2024-01-24 14:05    31  ************
  28    2024-01-24 14:06    32  *************
  29    2024-01-24 14:07    31  ************
  30    2024-01-24 14:08    32  *************
 ...    ..( 20 skipped).    ..  *************
  51    2024-01-24 14:29    32  *************
  52    2024-01-24 14:30    31  ************
  53    2024-01-24 14:31    31  ************


SCT Error Recovery Control:
           Read:     70 (7,0 seconds)
          Write:     70 (7,0 seconds)


Device Statistics (GP Log 0x04)
Page  Offset Size        Value Flags Description
0x01  =====  =               =  ===  == General Statistics (rev 1) ==
0x01  0x008  4              10  ---  Lifetime Power-On Resets
0x01  0x010  4              54  ---  Power-on Hours
0x01  0x018  6               0  ---  Logical Sectors Written
0x01  0x020  6               0  ---  Number of Write Commands
0x01  0x028  6           47049  ---  Logical Sectors Read
0x01  0x030  6            1752  ---  Number of Read Commands
0x01  0x038  6       197655650  ---  Date and Time TimeStamp
0x03  =====  =               =  ===  == Rotating Media Statistics (rev 1) ==
0x03  0x008  4              54  ---  Spindle Motor Power-on Hours
0x03  0x010  4              54  ---  Head Flying Hours
0x03  0x018  4              19  ---  Head Load Events
0x03  0x020  4               0  ---  Number of Reallocated Logical Sectors
0x03  0x028  4               0  ---  Read Recovery Attempts
0x03  0x030  4              28  ---  Number of Mechanical Start Failures
0x04  =====  =               =  ===  == General Errors Statistics (rev 1) ==
0x04  0x008  4               0  ---  Number of Reported Uncorrectable Errors
0x04  0x010  4               0  ---  Resets Between Cmd Acceptance and Completion
0x05  =====  =               =  ===  == Temperature Statistics (rev 1) ==
0x05  0x008  1              31  ---  Current Temperature
0x05  0x010  1              32  N--  Average Short Term Temperature
0x05  0x018  1               -  N--  Average Long Term Temperature
0x05  0x020  1              39  ---  Highest Temperature
0x05  0x028  1              18  ---  Lowest Temperature
0x05  0x030  1              37  N--  Highest Average Short Term Temperature
0x05  0x038  1              25  N--  Lowest Average Short Term Temperature
0x05  0x040  1               -  N--  Highest Average Long Term Temperature
0x05  0x048  1               -  N--  Lowest Average Long Term Temperature
0x05  0x050  4               0  ---  Time in Over-Temperature
0x05  0x058  1              60  ---  Specified Maximum Operating Temperature
0x05  0x060  4               0  ---  Time in Under-Temperature
0x05  0x068  1               0  ---  Specified Minimum Operating Temperature
0x06  =====  =               =  ===  == Transport Statistics (rev 1) ==
0x06  0x008  4              22  ---  Number of Hardware Resets
0x06  0x010  4               6  ---  Number of ASR Events
0x06  0x018  4               0  ---  Number of Interface CRC Errors
0xff  =====  =               =  ===  == Vendor Specific Statistics (rev 1) ==
0xff  0x040  7               0  ---  Vendor Specific
0xff  0x048  7               0  ---  Vendor Specific
0xff  0x050  7               0  ---  Vendor Specific
0xff  0x058  7               0  ---  Vendor Specific
0xff  0x060  7               0  ---  Vendor Specific
0xff  0x068  7               0  ---  Vendor Specific
0xff  0x070  7               0  ---  Vendor Specific
0xff  0x078  7               0  ---  Vendor Specific
0xff  0x080  7               0  ---  Vendor Specific
                                |||_ C monitored condition met
                                ||__ D supports DSN
                                |___ N normalized value


Pending Defects log (GP Log 0x0c)
No Defects Logged


SATA Phy Event Counters (GP Log 0x11)
ID      Size     Value  Description
0x0001  2            0  Command failed due to ICRC error
0x0002  2            0  R_ERR response for data FIS
0x0003  2            0  R_ERR response for device-to-host data FIS
0x0004  2            0  R_ERR response for host-to-device data FIS
0x0005  2            0  R_ERR response for non-data FIS
0x0006  2            0  R_ERR response for device-to-host non-data FIS
0x0007  2            0  R_ERR response for host-to-device non-data FIS
0x0008  2            0  Device-to-host non-data FIS retries
0x0009  2        65535+ Transition from drive PhyRdy to drive PhyNRdy
0x000a  2            3  Device-to-host register FISes sent due to a COMRESET
0x000b  2            0  CRC errors within host-to-device FIS
0x000d  2            0  Non-CRC errors within host-to-device FIS



```[COLOR=#22231F][FONT=&amp]


[/FONT][/COLOR]

---

