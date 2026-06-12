---
title: "RemoteFX Server on Ubuntu"
date: 2018-07-06
forum: General Help
---

### Post by stevea3342 on 2018-07-06
I am at most an 'advanced beginner' with Linux, my question is probably more of an advanced question than a beginner question.  I come from the Windows world but usually I can find my way around command line and follow instructions pretty well.   I have a good use case for deploying dozens of Ubuntu VDI guests as opposed to Windows 10 guests and I'm all set on the broker,cloning and virtualization side of things.  Users will get a desktop gui with basic tools for AWS and SQL admin and RDP is the easiest way for them to connect to these guests.   It's not that difficult to get RDP working to the Ubuntu guests, the part I'm missing is that I want the Ubuntu guests to provide a RemoteFX experience using UDP.  We don't care about GPU or video, but RemoteFX is the only technology (at least with Windows) that can deliver a smooth experience from our users that will be up to 250ms of latency away.   Citrix ICA used to be the only way for them to work but we've had good luck with remote users on Windows 7 connecting to Windows 10 VDI's with RemoteFX over UDP.  Can something similar work with the Ubuntu guests?  We will not be using HyperV.

---

### Post by TheFu on 2018-07-06
**x2go** is the best of the free, secure, remote desktops to connect to Linux from any of the main 3 OSes. RDP is NOT secure without a VPN or ssh-tunnel.  x2go using ssh-keys or ssh-certs is secure enough for internet use.

If the clients are on the same LAN, you might be able to use SPICE, but that only works under KVM VMs to my knowledge.  Over the internet, it would require a full VPN to be secure, which usually makes the performance less  than great.  On the same LAN, there is always remote X11, which has been working for decades, but also has security issues so everyone uses X11Forwarding via ssh.  An X-server is required on each of the physical machines that uses sit behind for this to work.

No idea what RemoteFX is. Never touched Win10 or HyperV. Sorry.

---

### Post by stevea3342 on 2018-07-06
Clients are on the same WAN and will not be going over the public Internet.  The reason for RDP is that we don't want to install client software on end-user machines and the vdi broker is only able to spit out .rdp files based on guest IP's to users.   They are non persistent and created/destroyed based on demand.

I've been trying to find working instructions to get this module to work: librfxcodec  [http://manu.agat.net/dotclear/index.php/post/2015/07/23/Efficient-Remote-Desktop-on-linux](http://manu.agat.net/dotclear/index.php/post/2015/07/23/Efficient-Remote-Desktop-on-linux)

The I was able to get the git repository downloaded but all the 'make' commands said they couldn't find the make files.  The procedure documented above is probably a bit over my head right now and I'm probably missing a step or two.  On an 18.04 test machine I'm able to RDP to it - an  xrdp window pops up with an xorg session option.  It works, but it's not a UDP/RemoteFX connection.

---

