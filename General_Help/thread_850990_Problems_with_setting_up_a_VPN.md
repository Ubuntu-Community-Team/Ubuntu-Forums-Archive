---
title: "Problems with setting up a VPN"
date: 2008-07-06
forum: General Help
---

### Post by YoungCthulhu on 2008-07-06
Right, now. Open your O'Reilly "Linux Desktop Hacks" with me to page 212, Hack #68 "Connect to a Microsoft PPTP VPN".

Stop sniggering down the back there Chan!  I can see you... :lolflag:

I want to set up a VPN so that I can access the server at work and also take control of my Dad's computer, across the Tasman in New Zealand.  The problem is that I don't really know what I am doing, and lost my video settings for a few hours (went to 640x480 CGA).  On checking I found that my /etc/X11/xorg.conf file had been over-written by one that had eveything set to default.  :confused:

I want to know why this should happen and what I did wrong so I will learn something from this debacle, so I would greatly appreciate any advice!

Following O'Reilly, I first set up a file /etc/ppp/peers/office whose contents is as follows:

> #PPTP office configuration file
#
#Enter login username etc...
#
<my_office_domain_name>\<my_office_username>
#
#
#get the rest of the info from this file:
#
file /etc/ppp/options


Next I edited /etc/ppp/options.pptp.  To be more accurate, I copied /etc/ppp/options to create options.pptp as this file did not exist.  Following O'Reilly again I made sure the following settings were made under the relevant headings:


#	Lock the port
lock

#	tunneling protocol server doesn't need to authenticate itself?
noauth

#	Turn off transmission protocols we won't be using:
nobsdcomp
nodeflate

#	We need MPPE
require-mppe


The last two headings were not present in the original /options file I used so I just tacked the last 3 commands at the end of the options.pptp file and saved it.

At this stage I think I might have done something wrong as the book recommends that MPPE support be built in to the kernel, so without properly checking, I ran 

$ modprobe ppp-compress-18

and nothing seemed to happen.  :(

I then edited etc/ppp/chap-secrets to contain

##	OUTBOUND CONNECTIONS
<my_office_domain_name\my_office_username> "*" <my_work_password_for_the_server>

The O'Reilly book then recommends you issue the following command to start the VPN

$ sudo pptp-command start office

And all I get is the familiar "Unknown file or directory" message.  The "pptp-command" looks sus to me; it doesn't seem to be a Linux command.  Do they mean you to substitute the PPTP invoking program relevant to your distro, vinagre perhaps??

How do I set up VPN to work and my father's computer?
What did I do wrong that would cause my screen to go to lo-res mode?

I would like to learn something from all this, as at the present I am just confused!

Cheers!

---

### Post by 505 on 2008-07-06
You don't need to go though all those files. Just left-click on the network applet (usually next to the clock), choose VPN connection and select Configure VPN. Here you can add a new connection. Choose PPTP tunnel and you can set all settings in the wizard.

---

### Post by YoungCthulhu on 2008-07-07
> **505 said:**
> You don't need to go though all those files. Just left-click on the network applet (usually next to the clock), choose VPN connection and select Configure VPN. Here you can add a new connection. Choose PPTP tunnel and you can set all settings in the wizard.

Thanks 505.  I am still having trouble though because the only "network applet" that seems to be available is called "Network Connections" and doesn't give the option to configure a VPN.  

I tried using System > Administration > Network to establish the link but it also does not provide the options you mention (VPN > Configure VPN > PPTP tunneling > etc )

Thanks for your assistance so far. :KS

Cheers

---

### Post by 505 on 2008-07-08
Install the package *network-manager-pptp* using Synaptic. You can also install *network-manager-vpnc* (Cisco VPN) or *network-manager-openvpn* if you need that VPN connection.

---

### Post by justleen on 2008-07-08
im using the cisco network-manager-vpnc  with the following config:
```

/etc/init.d/vpnclient_init start
sudo vpnclient connect <current connection name>  user <username>  

```
hope that helps...

---

### Post by YoungCthulhu on 2008-07-09
Thanks again 505 and Justleen,

I found this also on the Wiki, found network-manager-pptp was already downloaded to my system, re-installed it but then had problems getting it onto the desktop or panel.

i)Right clicking on the panel only gives the option of a "network monitor" Same logo, but not the right thing.
ii) Systems > Administration > Network does not give me the option of establishing a PPTP.

I found where network manager resides.  I am not at my home computer right now and am using an office Windows (cough) machine, but from memory it resides as /etc/network/NetworkManager with something like etc/network/NetworkManager/Despatcher/01onoff being the only executable file.  Should I establish a launching icon to this file on the desktop?  Entering it at the command line did nothing, as far as I know.  Perhaps it did, and right now a cat in Barcelona is chasing it's tail for no reason :-)

Cheers

---

### Post by pepposz on 2008-07-16
Hi,

I've recently switched to Ubuntu Linux from Windows, and I had a same problem as You. After reading Your problem and answers, I found a web page dealing with VPN on the following URL: [https://help.ubuntu.com/community/VPNClient#Installing%20and%20managing%20a%20VPN%20connection](https://help.ubuntu.com/community/VPNClient#Installing%20and%20managing%20a%20VPN%20connection)
To summarize the conclusion, if you have manually configured network, Network Manager does not handle VPN even if you installed the plugin.

As this document proposed, I saved /etc/network/interfaces file and edit it leaving only the first 2 line. After that, left click on network manager icon, I've got a menu with wired, possible wireless networks and VPN configuration possibilities.

It may work for You as well.


Cheers

Pepposz

PS: (There should be another question, how can we use VPN and manually configured networks at the same time.)

---

