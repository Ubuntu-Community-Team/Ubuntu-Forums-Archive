---
title: "&quot;shared internet connection&quot; vs. &quot;network&quot;"
date: 2007-06-03
forum: General Help
---

### Post by Scheater5 on 2007-06-03
There's something about networking I obviously don't understand.
Is there a difference between sharing an internet connection and a true "network" - either in terms of hardware or setup?  
I've got one desktop directly connected to a router (hub? I'm not sure of the difference).  This router is then connected to a wireless router that two laptops and an additional desktop connect to the internet through.  (one laptop windows, all others ubuntu)  However, none of these seem to be connected in any other way.  None of them show up when attempting to remotely login from the others.  Enabling a folder to be "shared" seemingly yields no results on the other computers.  
I'm trying to establish some remote connections - access computers in one end of the house from the other, be able to access home computers when away at college, use one desktop as a shared storage, that kind of thing.  But I get confused reading manuals on things like putty, ssh and vcn because I don't understand why the computers seem to be segregated.

---

### Post by djchandler on 2007-06-03
> **Scheater5 said:**
> There's something about networking I obviously don't understand.
Is there a difference between sharing an internet connection and a true "network" - either in terms of hardware or setup?  
I've got one desktop directly connected to a router (hub? I'm not sure of the difference).  This router is then connected to a wireless router that two laptops and an additional desktop connect to the internet through.  (one laptop windows, all others ubuntu)  However, none of these seem to be connected in any other way.  None of them show up when attempting to remotely login from the others.  Enabling a folder to be "shared" seemingly yields no results on the other computers.  
I'm trying to establish some remote connections - access computers in one end of the house from the other, be able to access home computers when away at college, use one desktop as a shared storage, that kind of thing.  But I get confused reading manuals on things like putty, ssh and vcn because I don't understand why the computers seem to be segregated.

I'm a little confused about the first desktop you mention, but it must currently be hardwired to a switch or hub. I do not think you need the hub. Turn everything off. Now, direct connect the first desktop to the wireless router at the same point as the hub or switch is now and remove the hub/switch from the configuration. Now you can re-power your router first, and then your computers. I would make sure the dhcp server, if available, is enabled on the router, and enable only as many ip addresses as the maximum number of connections you will ever possibly need.  Enable file sharing on the Windows laptop, and then select a Folder to share, or just make sure the Documents folder under the All Users Folder which is under Documents and Settings in the root directory of your C: drive is shared. Make the remote user enter a password to gain access to the shared directory. Make sure you also define a workgroup name on the windows laptop in the network settings and your laptop has been named, which it probably was when Windows was installed. You might want to change it to something else just so it makes sense to you. Try not to use names that are used elsewhere for networking or file system purposes. For instance, I don't think HOME is a good workgroup name, but HOMENET would probably be OK. The Linux systems now must have Samba installed in order to see the Windows laptop, and must know what workgroup to look under on your Windows network. The Linux computers should be able to find each other as well on the Windows network. Go to "Places" on your top menu bar, select network, and you should be able to see each computer that has share enabled, workgroup name(s), and protocols enabled, such as SMB on a folder for Samba, in a Nautilus window. It's not absolutely necessary to enable any other file sharing system unless you want to experiment once you have everything else working under Windows share. The fact that you have the Windows laptop in the mix is what makes me think you should go with Samba first. Got to the Samba website to learn to configure Samba once it has been installed on your Linux computers at [http://www.samba.org/](http://www.samba.org/) and that will get things rolling. They have their own forums for solving Samba specific problems. Since you're on WiFi, security is an issue. Make sure nobody driving by your house (wardriving) can see you LAN and log into it and use your internet connection. You may not be secure from that now. Check the settings on your WiFi router to make sure it is intruder proof.

---

### Post by Scheater5 on 2007-06-03
When I said "directly connected" I meant connected with an ethernet cable.  And I think I need the router since my connection is DSL - the cable that connects to the internet is the shape of a phone cable, not ethernet, and there's no connection on the wireless router for it.  
And how do you define a workgroup name on a computer that's already installed?

---

### Post by dbott67 on 2007-06-03
> **Scheater5 said:**
> There's something about networking I obviously don't understand.
Is there a difference between sharing an internet connection and a true "network" - either in terms of hardware or setup?  

No.  Networking in it's simplest terms means sharing resources across the network.  It could be a printer, a folder containing files or your internet connection.

> **Scheater5 said:**
>  I've got one desktop directly connected to a router (hub? I'm not sure of the difference).

Hubs are a "shared-medium" device, meaning that only one device can transmit data at any given time.  If you have lots of computers all trying to communicate, it can lead to contention issues (poor performance).  In a nutshell, a hub receives a packet from on of the ports and broadcasts it out every port in hopes that the destination computer receives it.

A switch, on the other hand, learns the MAC address of every computer plugged into each port and will only forward the packet to the appropriate device.  This leads to increased performance.

A router is used to pass information from one network to another network.  Most home routers (like D-Link, Linksys, Netgear, etc.) operate like one-way valves, meaning that they let you send data (i.e. surf the 'net", but do not allow unsolicited inbound traffic in (thereby acting like a firewall.  Most home routers have an integrated 4-port switch.

> **Scheater5 said:**
>  This router is then connected to a wireless router that two laptops and an additional desktop connect to the internet through.  (one laptop windows, all others ubuntu)  However, none of these seem to be connected in any other way.  None of them show up when attempting to remotely login from the others.  Enabling a folder to be "shared" seemingly yields no results on the other computers.  

In order for these devices to "see" each other, they need to be on the same LAN segment (i.e. their IP address must be in the same network such as 192.168.1.xxx, and they should be attached to the same hub/switch/router).  If not, the computers may not be able to see each other due to routing issues.

> **Scheater5 said:**
> I'm trying to establish some remote connections - access computers in one end of the house from the other, be able to access home computers when away at college, use one desktop as a shared storage, that kind of thing.  But I get confused reading manuals on things like putty, ssh and vcn because I don't understand why the computers seem to be segregated.

This can all be done.  I routinely connect from work to home (and vice-versa) using things like VNC, SSH, WinSCP, Terminal Services, NX Machine, etc.

It just takes a little knowledge of the network layout & devices.

If you can post a diagram of the network including things such as:

1. Physical layout of the network.
2. IP addresses on internal devices.
3. Makes & models of any routers/hubs/switches.

I'm attaching a few screenshots to help explain (these are examples only).

-Dave

---

### Post by Scheater5 on 2007-06-03
> Quote:
 Originally Posted by Scheater5 View Post 
 This router is then connected to a wireless router that two laptops and an additional desktop connect to the internet through. (one laptop windows, all others ubuntu) However, none of these seem to be connected in any other way. None of them show up when attempting to remotely login from the others. Enabling a folder to be "shared" seemingly yields no results on the other computers.
In order for these devices to "see" each other, they need to be on the same LAN segment (i.e. their IP address must be in the same network such as 192.168.1.xxx, and they should be attached to the same hub/switch/router). If not, the computers may not be able to see each other due to routing issues.
 
Ah, so they would all need static IP addresses, then?  All computers are currently on DHCP.  
As for the hardware, the two desktops are Compaq Presarios, one Toshiba laptop and one Dell Inspiron - the DSL router is Netgear and the wireless router is a Belkin G+.  I can have more specific makes and models by the end of the day.  
As for the diagram...well, I stink at using graphics programs, but perhaps I still get the point across.  

Internet connection comes into the house.  Goes into DSL router.  From there to two places - one desktop via ethernet and one wireless router.
From wireless router internet connection goes via wifi to two laptops and an additional desktop.

---

### Post by dbott67 on 2007-06-03
I think I've got the picture.  I've posted 2 screenshots below.  The first one is what I think your network looks like.  Please correct me if I've made any errors.

The second one is what it should look like (with DHCP disabled on the Belkin & NOT using the WAN port on the Belkin router).

Basically, the problem is this.  This current setup has 2 different networks: one provided by the Netgear router and the other provided by the Belkin wireless router.  The issue arises from the fact that simple network discover tools tend not to look beyond the local subnet, meaning that you cannot "browse" to other devices by name or by looking in the Network Neighbourhood (although, you could connect from the Belkin network to the Netgear network using IP address, but not from Netgear to Belkin due to the built-in firewall).  So, the 2 laptops & 1 desktop may be able to see shared resources one the Belkin network (assuming firewalls are disabled or configured properly), but they won't see the other subnet.

While we could configure the Belkin to forward ports so that you could go from the Netgear network to the Belkin, the setup can be painstaking for the non-network gurus in the crowd.

The best option is this: turn off DHCP on the Belkin router and unplug the network cable from the WAN/Internet port and move it into one of the 4 LAN ports.  Essentially, we'll be using the Belkin as a wireless switch and disabling the routing/firewall capabilities, instead relying on the Netgear to do it all.  [COLOR=Red]See the attached screenshot #2.[/COLOR]

This will put all 4 computers on the same subnet and local resource sharing should be quite easy to setup.

-Dave

---

### Post by Scheater5 on 2007-06-03
Yes, that is my setup, except that desktop #2 is also connected via wifi through a usb adapter, not ethernet.  
Thanks for all your help guys.  I'm going to try your suggestions now dbott67.

---

### Post by Scheater5 on 2007-06-03
Alright, I'm having some issues configuring static IP addresses.  I've never used anything besides dhcp.  
Is it absolutely necessary to get access to the router?  The ISP set a password on it and neglected to leave a copy of the documentation.  According to the instruction manual, the ip of the router is 192.168.1.254.

Any attempts I've made to configure via static IP have failed.  (As a side note, now knetworkmanger does not show that I am connected via a wireless connection on the kubuntu laptop, although it has a working connection when I set it back to dhcp)

O, and I made some errors in reporting the setup.  It has been tucked away in a corner of a computer room and I reported from memory.  My appologies.  
The DSL router is Netopia, not Netgear, and the desktop that is connected via ethernet is connected to the wireless router not the DSL router.  
Also, connecting the DSL router to a regular connection didn't work.  The Belkin router's wan connection is labled "connection to modem" and only through this connection do the computers seem to have internet access.

---

### Post by Scheater5 on 2007-06-03
Alright, I think I have another problem.  I tried to access the router and there was a password and username that I didn't know - so I called tech support for my ISP, and discovered the connection is PPPoE.  According to the tech support, it may not be possible to set up static IP.  I accessed the Belkin router, turned DHCP off, and could not configure static IP successfully.  Anyone have any ideas?

---

### Post by dbott67 on 2007-06-03
Does the Netopia have a DHCP server in it?  If so, you can use it to supply DHCP addresses to your wireless devices (the Belkin will just pass on the DHCP requests to the Netopia).

If the Netopia does not have a DHCP server, then revert to the original setup and connect all computers to the Belkin (re-enabling DHCP on the Belkin).  Doing so, would ensure that all devices are on the "Belkin" subnet and from here we can work on sharing files, printers and whatever else you want.

Just make sure that all devices can access the internet.

-Dave

---

### Post by Scheater5 on 2007-06-04
I'll check in the morning - that will require calling tech support again and getting my username and password for that router.  When I asked about it the first time I called the tech support merely replied by saying you couldn't set PPPoE for static IP.

---

### Post by djchandler on 2007-06-04
> **Scheater5 said:**
> I'll check in the morning - that will require calling tech support again and getting my username and password for that router.  When I asked about it the first time I called the tech support merely replied by saying you couldn't set PPPoE for static IP.

Hey, Scheater5. Simplifying the connections is the way to go. You need to make a firm decision about the hardware by which the whole network is connected and then stick with it. I know there are trade-offs no matter which way you go, but I'm so confused by the hardware topology that I'm stepping out of this.  And the USB wrinkle is beyond my ability to cope with due to zero experience with USB connected networking. I'm strictly a twisted pair kind of guy. If it isn't physically connected via ethernet cables and PCI or PC-card adapters, this is beyond my experience. I'm just a little old-fashioned. I hope dbott67 can help, but you supplying diagrams as he suggests is probably a must short of getting an on-site tech. Give it your best shot on the diagrams. I'll lurk to see if something comes to mind, but this seems too confusing for me. Good luck!

Regards,
D. J. Chandler

---

### Post by dbott67 on 2007-06-04
> **Scheater5 said:**
> I'll check in the morning - that will require calling tech support again and getting my username and password for that router.  When I asked about it the first time I called the tech support merely replied by saying you couldn't set PPPoE for static IP.

You don't need a static IP for your PPPoE connection, as it is the external IP.  Internally, you can use static to help maintain name-to-IP-address mappings, but again, it's not required.

For a little more info on name resolution, see this thread (post #3):
[http://ubuntuforums.org/showthread.php?p=2745616#post2745616](http://ubuntuforums.org/showthread.php?p=2745616#post2745616)

I hope this isn't getting too confusing for you.  The best course of action is this:

1. Provide a network diagram of the hardware topology.
2. Provide a list of some of the things you'd like to do (file share, printer share, etc.)
3. Provide any other pertinent info.

This will help us choose the best course of action for your setup.

-Dave

---

### Post by Scheater5 on 2007-06-06
Guys, I thank you all for your help.  The problem has not been resolved, but many of the barriers have been illuminated.  I am currently scouring the net for more information on this topic.  It may be some time before I figure out just exactly what am I doing wrong, but at least I think I have found some direction.  It is quite likely that this project will be temporally abandoned before it is solved.  But I thought you guys at least deserved a thank you.  I'll let the forum know how things progress - maybe post an idiot's/novice's  howto if I ever get it figured out.  (I did one of those with Beryl once, only to find out someone beat me to it by just a few days...such is life)  NEway, thanks again.

---

### Post by Scheater5 on 2007-06-08
Massive breakthrough.  
Alright, so I still don't get static-vs-dynamic IP.  BUT I have apparently found a workaround.  
Followed the instructions [here]("http://ubuntuforums.org/showthread.php?t=218630") to get file transfers working, and succeeded.  I now have one computer in the computer room that I can access from one kubuntu laptop.  And now I can remotely access this same computer.  I have yet to completely test it - I have accessed it, but not logged in (currently that computer is logged in, and I won't have access to it until the morning).  I will test it tomorrow and report here.

---

### Post by Scheater5 on 2007-06-09
If anyone is following this still, one of the things I wanted to do has now been done sucessfully.  I took the desktop connected via ethernet to the Belkin Router and signed off.  I can now sign onto this computer remotely via the kubuntu laptop.  :D:D:D:D

...now I've just gotta figure out how to do that from the net if I'm not on the same network.

---

### Post by dbott67 on 2007-06-09
Glad you've got things working.  Here's a post I wrote about 'port-forwarding' which is what you need to do on your router.

[http://ubuntuforums.org/showpost.php?p=1912795](http://ubuntuforums.org/showpost.php?p=1912795)

The key things to note are:

1. Which application do you want to use to connect to your home computer?  For example, SSH uses port 22; VNC uses 5900; RDP uses 3389, etc.  You would need to forward the appropriate external port to the IP address of the internal computer.

2. You need to know your external IP address.  Most ISPs grant dynamic IP addresses, so you always have a moving target.  Fortunately, there are free services such as DynamicDNS that offer an easy way to connect to your home computer.  There's a link in my referenced post.

-Dave

---

