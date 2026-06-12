---
title: "PPTP Help!"
date: 2007-09-19
forum: General Help
---

### Post by dontpannic on 2007-09-19
Hiya guys, I wonder if you can help.

Got rid of my dodgy Win 2003 server install a few months back and migrated my home server to Ubuntu. Set up email fine and the homepage works fine too, but one feature I loved with 2003 was the VPN feature. I could dial home from work and access the home internet connection and home network resources from the work network. All I did there was set up a VPN connection from work to home. I've found the daemon I needed and have installed it fine. Connected from work and hey presto, it works fine.  Set the PoPToP daemon to accept IP's in the range 192.168.1.70-80 (as they aren't included in DHCP address leases) and set up the windows client to connect to it. It connects fine, but doesn't recieve any packets and doesn't allow me to access resources or the internet. 

Being CISCO qualified I used my troubleshooting skills to diagnose the problem and have found out the PoPToP is giving out the client IP as a default gateway. Unfortunately in Windows there is no way to set the VPN gateway address... 

> ""C:\Documents and Settings\Nick>ipconfig

Windows IP Configuration


Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : xxxxxxxxxxx
        IP Address. . . . . . . . . . . . : 192.168.125.77
        Subnet Mask . . . . . . . . . . . : 255.255.252.0
        Default Gateway . . . . . . . . . : 192.168.125.254

Ethernet adapter Wireless Network Connection:

        Media State . . . . . . . . . . . : Media disconnected

PPP adapter burman.org.uk:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 192.168.1.70
        Subnet Mask . . . . . . . . . . . : 255.255.255.255
        Default Gateway . . . . . . . . . : 192.168.1.70

C:\Documents and Settings\Nick>""

Any clues as to how I can change this?

Cheers,

Nick

---

### Post by tenwiseman on 2007-09-27
Hi dontpannic,

Don't Panic... ;-)

I've been having a go at this today, and although I'm not a CISCO I think I've got a solution for this.

First to check on your post

[quote=dontpannic]
 .. It connects fine, but doesn't recieve any packets ...
[/quote]

Which packets, where? When connected from your windows machine can you at least ping the PPP interface ip address of your home server, that you specified as "localip" in /etc/pptpd.conf?

[quote=dontpannic]
... and doesn't allow me to access resources or the internet...
[/quote]

I'm assuming that statement applies to connectivity on your windows machine, that was there before the VPN was connecting. This denial of resources will be due to the replacement of the default LAN gateway for your windows machine by the one for your VPN - something that Microsoft implemented by default to avoid dangerous packets crossing from LAN to VPN.

OK, the following will undo all that, and enable what is known as a "split tunnel" - a known headache to system administrators. Google that term with "VPN security" if you want to know the story.

Anyway, to remove the VPN gateway and reinstate the existing LAN gateway while connected to your VPN, view the properties for the VPN connection in Window's 'Network connections' view. On the "Networking" tab, you'll need to click the properties button for the "Internet Protocol (TCP/IP)" entry in the list and you will see an "Advanced" button near the bottom of the "General" tab. Click that to view the "Advanced TCP/IP settings" and you will see on the "General" tab a tick in the "use default gateway on remote network". Clear that tick, and click OK as necessary to close all open dialogs.

Now all should work but you now don't have a gateway route to machines on your VPN'ed remote network. The following webpage will assist here in fixing that with a few additions to your windows machine routing table.

[INDENT]
[http://stevenharman.net/blog/archive/2007/01/26/VPN_Connections_and_Default_Gateways.aspx]("http://stevenharman.net/blog/archive/2007/01/26/VPN_Connections_and_Default_Gateways.aspx")
[/INDENT]

Hope that helps,

--
Adrian C

---

### Post by dontpannic on 2008-01-07
Thanks Adrian - I'll have a go tonight and let you know...

---

