---
title: "Web / Network &gt; Security whilst web browsing ?"
date: 2015-08-05
forum: General Help
---

### Post by noobtechninja on 2015-08-05
Hi there.

Right, I was wondering about security (web and network) whilst surfing the web.

So my set up is as follows -

Cable modem > switch > PC + Laptop + NAS box.
All of this is hardwired with ethernet.
(My NAS contains all of my media and my photos. I don't want the slightest chance
of anything happening to it !)

When I want to look at porn, I will do the following -

1. Use my main PC (but using a live CD/DVD linux distro)

2. Turn off / disconect all other devices connected to the network when I am looking
   at porn. (Both hardwired and Wi-Fi)


Once I have finished, I will reboot the modem and then reconnect/turn on all of my
other devices once again.

I realise that this might sound a bit extreme, however I've never had any viruses or
malware in the last 5+ years of using Linux and this method of secure browsing.

In addition I am fully aware that Linux isn't going to be affected by Windows malware
(But as I dual boot, it is a cause for concern).


So if I was surfing the web (looking at porn) and other naughty websites,
my questions are as follows -

Q1. Do I have to shut down/unplug other devices, PCs, tablets, (NAS especially)
whilst I am surfing porn on my PC (whilst using a live CD/DVD) ?

Q2. If I left my NAS turned on/connected to the main network, Is it possible to for my
NAS to become infected, if I am surfing the web on a live disc ?

Q3. What other precautions do you take when doing the same types of things ?


I am looking for serious answers please guys.

TIA for any help or advice.

---

### Post by efflandt on 2015-08-05
Unless you have an Internet plan that allows you to get multiple public IP addresses through a single cable modem, I suspect that your modem is actually a modem/router or gateway which automatically does NAT and provides IP addresses in a private range on its LAN side. Otherwise a simple switch would not work in your scenario. So as long as you have no ports forwarded in, or no private IP set as DMZ on your modem/router, nothing should come in from the Internet that is not a reply to an outgoing connection.

A live/install iso without persistence booted from CD/DVD is booted from a fixed compressed file system that cannot be altered from itself (to alter it, the original iso would need to be altered before burning the disc). I suppose if someone was determined enough and knew exactly what you were running, they might find a way in while the CD/DVD was booted. But it would be temporary for that session only and would die when the system was shut down. But I have been running various Linux versions for at least 20 years and have never had Linux infected. I have an old headless PC in my basement that has been running Linux 24/7 since 2003, last updated in 2005, but the only things ever open to the Internet (port forwarded to it, or open when it was my DSL router) were apache (including while IIS worms were running rampant), ssh (keys only, no passwords), and briefly sendmail or postfix sending and receiving to learn how to configure those. It has been running almost continuously for over 12 years (other than briefly shutting down for configuration changes or long power failures). It ran 5 years straight without rebooting between a power failure July 2006 and when I shut it down during a 14 hour power failure July 2011.

So I primarily run Linux at home without any fear of being infected by Windows exploits. It boots much quicker than Windows and does everything I need to do (including Linux Steam games).

---

