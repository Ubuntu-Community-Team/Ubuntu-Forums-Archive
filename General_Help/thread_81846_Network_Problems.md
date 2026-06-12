---
title: "Network Problems"
date: 2005-10-25
forum: General Help
---

### Post by chloran on 2005-10-25
I am trying Kubuntu live CD on a Fujitsu Lifebook, and I can't connect to the Internet on it, I have it wired in to a router and I know nothing is wrong with the ethernet cause I have it running right now with Windows XP Home SP2 and it is working just fine on the net.  I tried the PPC version of Kubuntu live CD and it worked just fine connecting to the internet with my iBook. When I go into the network settings it shows the eth0 connection for the ethernet and eth1 for the wireless card.  First I have to click on administrator access (which was hidden someone in the window but found it using the [tab] key) now that I am able to click on the eth0 connection I clicked enable and it would say enabling.  But after one second of being connected it would disconnect, the same goes for the eth1 connection.  Someone else in a different forum said to open the terminal and put in the following command (ifconfig eth0 up)  I get a message back saying that I don't have the right privileges.  Does anyone have any sugestions?

---

### Post by mlomker on 2005-10-25
> (ifconfig eth0 up)  I get a message back saying that I don't have the right privileges.  Does anyone have any sugestions?

You'd want to use **sudo ifconfig eth0 up** but I doubt that's the problem.  It sounds like it isn't loading the ethernet driver for whatever reason.  What kind of card is it?  Does it work from a Knoppix boot cd?

---

### Post by chloran on 2005-10-25
Yeah I forgot to mention I tried the sudo command too and still got nothing,  This is what Windows says it is (Broadcom 440x 10/100 Integrated Controller)

And no I have not tried Knoppix,  I am downloading the Ubuntu live cd as we speak, so in a few hours I will see about that one.

---

### Post by daller on 2005-10-26
[QUOTE=chloran]Yeah I forgot to mention I tried the sudo command too and still got nothing,  This is what Windows says it is (Broadcom 440x 10/100 Integrated Controller)

And no I have not tried Knoppix,  I am downloading the Ubuntu live cd as we speak, so in a few hours I will see about that one.[/QUOTE]

Concerning your network-connection, I'll bet that Ubuntu-Live doesn't perform better that Kubuntu...

Have you tried "sudo ifup eth0" ???

Maybe you will have more success with su???

sudo passwd

and then use "su" and then "ifup eth0"

...Your permission-problem seems odd!

---

### Post by Staesys on 2005-10-26
Broadcom chipsets and Linux do not play well together. More than likely, after an install, you will have to install ndiswrapper and use the windows driver under that to get your network going.

The live cd is more than likely NOT going to support this chipset either.

---

### Post by daller on 2005-10-26
Mine works great!

0000:02:00.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)

But well, networking in Linux gives me a headache!

Is it for a desktop machine? (Ethernet-cards are quite cheap! $5-6)

---

### Post by Copter on 2005-10-28
hi!

ive got the same problem with eth0 config. in my case it sounds little weirder though. it looks like this:

when i boot the system without cable plugged to my eth0 card i cant enable (turn on) eth0 network card in kcontrol. it acts the same as chloran's. i dont have any priviliges issues here though. another thing is setting up my wlan card. have no idea how to enable it also.

i wonder, if all this admin-mode problems are related to kde or ubuntu? it was the same thing in hoary. cant see any fixes in breezy atm. it seems that most of gui config tools are useless.

copter :]

---

### Post by Arevos on 2005-10-29
[QUOTE=chloran]Does anyone have any sugestions?[/QUOTE]
Does your network use static IPs, rather than DHCP? The Kubuntu networking module seems to allow you to manually set your gateway; but this doesn't work, and hasn't for some time. You have to manually edit /etc/network/interfaces and add in "gateway 192.168.0.1" (or whatever the IP of your router is), under the primary network interface options.

Of course, this assumes you're using static IPs, which most people aren't these days.

I also assume this is a KDE bug, rather than a Kubuntu one, or else it would probably be fixed by now.

---

