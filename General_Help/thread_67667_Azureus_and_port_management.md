---
title: "Azureus and port management"
date: 2005-09-20
forum: General Help
---

### Post by Blue1k on 2005-09-20
I can't seem to get Azureus to show a "green light" when downloading.
I am behind a router but it is set up statically to allow Azureus to access incoming/outcoming through a specific port I set. I just installed Ubuntu onto my home box and now it doesn't work (worked in every other linux I have tried)

I installed Firestarter and changed inbound to allow my port to be open but there is nothing for outbound.

Do I have to use firestarter in Ubuntu to regulate which ports are open or is there another way? 

Thanks..I basically can't download anything until I get this sorted out.

---

### Post by Blue1k on 2005-09-20
I'm also getting a NAT error.

This was never a problem in Kanotix. What setting do I need to change?

---

### Post by bored2k on 2005-09-20
You are behind a router and you have azureus' ports forwarded? Go to pcflank.com and do an advanced port scan using those ports. If they are open, they will show. If you are sure you have them open and they still show closed or stealthed, you should allow firestarter/firewall to use those ports.

NAT error ? Usually comes from unforwarded ports.
> So when you get the error message "NAT Error", this means that your router is NOT translating the IP address from your computer to and from the outside world IP address of your router. And this is why no information or downloads can occur until this is sorted out, because information can not pass between your computer and the router, and thus cannot pass to and from the outside world of the internet.
[http://azureus.aelitis.com/wiki/index.php/PortForwarding#NAT](http://azureus.aelitis.com/wiki/index.php/PortForwarding#NAT)

---

### Post by Blue1k on 2005-09-22
No, the ports ARE open. I know that because I set up the system myself (on 6 different distros). I also checked. After reboot, the NAT error disappears but my downloads are still very slow. I have tried 6 random torrents all with lots of seeds and peers.

Any ideas?

---

### Post by bored2k on 2005-09-22
1. Can you try removing Firestarter? If anything, it will block/stealth your ports, not the other way around.

2. Are those torrents working correctly in the other distributions/operating systems? 

3. Can't you check if the system is opening your ports in pcflank.com (adv port scan)? Remember, do the test while downloading in the ports you selected azureus to.

---

### Post by Blue1k on 2005-09-22
Yes the torrents work beautifully in WInXP (120-200+kb/s) and in Kanotix. But not in Ubuntu.

I guess what I am asking is not about port forwarding. I understand that-the router is optimized to my internal IP with the proper ports opened. What I need to know is there any settings in Ubuntu that I need to change?

And yes, I uninstalled firestarter with no change

Thanks! :) 

..I'm tempted to just through Breezy in and see what happens. 5kbs/s downloading just sucks

---

### Post by bored2k on 2005-09-22
There really is not any settings in Ubuntu. It's a clear plug and play distribution. I am also a BitTorrent maniac and besides my own portforwarding trouble, Ubuntu works gracefully for me and others. At the moment, the only thing I would recommend is to try other BitTorrent clients and see how they behave (a verbose client like BitTornado perhaps).

---

### Post by Blue1k on 2005-09-22
LOL..I have tried every one I could install. All sucked. Weird huh?

Well I guess I will HAVE to try Breezy now.  :-P

---

### Post by bored2k on 2005-09-22
[QUOTE=Blue1k]LOL..I have tried every one I could install. All sucked. Weird huh?

Well I guess I will HAVE to try Breezy now.  :-P[/QUOTE]
 Did you check with pcflank.com? You need to know if Ubuntu is or not blocking your ports.

---

### Post by Blue1k on 2005-09-22
It shows my set port as open.

---

### Post by bionnaki on 2005-09-23
azureus works fine for me. 

I think firestarter has something to do with this.
did you do a complete removal?

---

### Post by Blue1k on 2005-09-23
Ok the problem seems to have disappeared (so far). I decided to install Breezy (WOW) but the problem was still there.


1. I installed Ktorrent since it supports multple downloads. (no effect)
2. I changed my Ethernet connection to my second Ethernet controller ( I have different ones on my MB)--That seems to have fixed it!

Wierd thing is my max download speed on my first ethernet controller is around 1100kb/s, but all my torrent downloads were stuck aorund 5-10Kb/s

The second controller is a tad slower (not by much though) but the tested torrent is now back to 80kb/s which was the same for this torrent in Kanotix.

Weird but it works.

Thanks to all that tried to help me! :)

---

### Post by Blue1k on 2005-10-02
Well that didn't last long. The problem is back

I spent an entire afternoon trying different torrents from 2 different sites with very poor results. Most had well over 200 peers and 30 seeds so the speed should be quick (as witnessed in Kanotix)

I'm totally lost with why this is happening but if I can't get this to work, Ubuntu and I will have to say goodbye :(

---

### Post by Pettman on 2005-10-03
I have the same problem. Can not get Azureus to work. On start-up of Azureus I get the following > Failed to establish listen on port UDP:2355.
Check that other applications aren't already using this port.
Also check for another copy of Azureus running. I have just as Blue1k
 tried to uninstall Firestarter and it didn't help. Some peopel I have asked hints it have with the IP tables to do.

EDIT: It works for me too, but I get annoyed by the nat error text

---

### Post by Blue1k on 2005-10-04
My problem isn't really the same as yours. My NAT test shows an open port and I haven't gotten an error message. What sucks is my download speed.

---

### Post by joshuapurcell on 2005-10-04
I had the same problem with downloading torrents, and it was related to my router not forwarding ports like I needed it to. Azureus by default requests that ports 6881-6999 are open for use (from reading their support information), and I wouldn't be surprised if this is not a standard for all torrent clients (but I could be wrong). Either you have those ports open or you don't. One other thing to check though is your speed/duplex settings (using **sudo ethtool eth0**). With most routers and NIC cards this is automagically set to the correct setting (which is usually 100/full), but some Cisco equipment and also older stuff doesn't do it right. The only other things you can try is another torrent client, but I would really double-check that the ports are open... I can't imagine it being anything else other than that.

EDIT: I had my connection in Azureus showing up as the yellow icon until I realized that I needed to open up ports 6881 through 6999 on my router.

---

### Post by skirkpatrick on 2005-10-04
I wish there was a way to open up ports to multiple computers.  There are 3 computers here that may want to use bittorrent at the same time.

---

### Post by Pettman on 2005-10-04
[QUOTE=skirkpatrick]I wish there was a way to open up ports to multiple computers.  There are 3 computers here that may want to use bittorrent at the same time.[/QUOTE]
It is just to use a client that lets you select port and then use diffrent ports.;)
EDIT: For the diffrent coputers.

---

### Post by skirkpatrick on 2005-10-04
Yes but the problem comes when your router only has 10 forwarding slots and you've got 3+ computers that want bittorrent, IM file transfers, etc.  Of course I could always turn my file server into a router and get all kinds of capability :)

---

### Post by Pettman on 2005-10-04
[QUOTE=skirkpatrick]Yes but the problem comes when your router only has 10 forwarding slots and you've got 3+ computers that want bittorrent, IM file transfers, etc.  Of course I could always turn my file server into a router and get all kinds of capability :)[/QUOTE]
Just a thougth, would it be possible to use the same portrange for one IM protocoll and bittorrent?

---

### Post by skirkpatrick on 2005-10-04
I think it depends on the IM.  Some are not changable.

---

### Post by Pettman on 2005-10-05
But you can change bittorrent so it will be next to the IM's standard portrange.

---

### Post by awtomlinson on 2005-10-06
i'm having the exact same issue with bittorrent clients, but i don't use a router.  my upload status light is always yellow, indicating that some sort of nat is blocking the tracker.  i have tried bittornado, azureus, and gnome bittorrent client.  they all behave the same.  downloading torrents is fine, but uploading is the issue.  i thought that firestarter may be the problem, so i shut the program down, but the results are the same.  obviously, the built in iptables is blocking my torrent uploads.  how can i open the necessary ports to be able to upload with a bittorrent client?  i have visited various port scanning/security websites, and all of my ports appear as stealthed, not closed.  torrent uploads function properly on the same computer when i am booted in windows xp.  additionally, this issue never happened when i was using warty, only since upgrading to hoary.

---

### Post by bored2k on 2005-10-06
You can allow the bittorrent ports using Firestarter (allowing their services in the Inbount traffc policy tab).

---

### Post by awtomlinson on 2005-10-06
i'm familiar with firewalls, but can you give me explicit directions?  i allowed udp port 6881 but it didn't help.  i think that i need to allow a whole range of ports to be open, but according to the azureus website, the latest versions of azureus require that only port 6881 be open.  do you know what that port range is?  i think i remember seeing something about port 6969 being necessary for torrent trackers.

---

### Post by Pettman on 2005-10-12
[QUOTE=awtomlinson]i'm familiar with firewalls, but can you give me explicit directions?  i allowed udp port 6881 but it didn't help.  i think that i need to allow a whole range of ports to be open, but according to the azureus website, the latest versions of azureus require that only port 6881 be open.  do you know what that port range is?  i think i remember seeing something about port 6969 being necessary for torrent trackers.[/QUOTE]
It requires the specified port to be open, that could how ever be any port from 1024 to something really huge number that I don't remember.

---

### Post by Blue1k on 2005-10-19
I run a huge number (say 50000) as my open UDP port and it works fine. My ISP is throttling torrents so I decided to stay away from using more common ports.

By the way:
I reset the router because we were having problems and all my settings stayed the same EXCEPT for my DHCP setting which was originally set to static, but reset to DHCP. After changing that, I am able to download torrents again :rolleyes:

Thanks for all the help. I feel like a newb

---

### Post by Blue1k on 2005-10-29
After trying Kubuntu for a week or so and hating it, I went back to Ubuntu (fresh install). Now I can't download ANY torrents. NADA...all my downloads show tons of peers and seeds but 0 connections. Settings are the same

Any idea??????:(

---

### Post by MattressVon on 2008-06-03
So I'm having the same issue with Azureus working great in windows but not working at all in Hardy Heron. i can't upload and my downloads are a trickle 9probably due to my leecher status due to blocked uploads). I have tried everything from iptable editing via "sudo iptables -A INPUT -p tcp --dport 6881 -j ACCEPT" terminal command with 6881 replaced by different high range ports; to installing and configuring fire starter, to uninstalling fire starter, to flushing my iptables, to using four different bittorrent clients. I can't get more than 5kb of download and no upload. What's up? I had no issues in windows xp with the same machine in the same network. static IP address does nothing,going bald to the web directly wih no firewall and no router does nothing. Any ideas or things I could have missed?:confused:

---

