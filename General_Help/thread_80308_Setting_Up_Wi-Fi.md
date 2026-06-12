---
title: "Setting Up Wi-Fi"
date: 2005-10-21
forum: General Help
---

### Post by TrumpetMan258 on 2005-10-21
I just installed Ubuntu and need help setting my Wi-Fi card.  It's from Dell, with a Broadcom chipset, and I've heard there are always problems with this.  I found a few guides showing how, but I just keep getting confused.  Can someone point me to an easy to understand and follow how-to or something?

---

### Post by ymmotrojam on 2005-10-21
Go to [B]System>Administration>Networking

[/B]...and verify the following things...
1) Does it list a "Wireless Connection"?
2) Does it have a red x next to it? (it means it's disabled)
3) Select Wireless Connetion and then click properties
4) Be sure that there is a network name filled in, and unless you hae enabled extra security, choose plain text
5) Then skip down and choose DHCP for the Configuration type
6) Click okay, and then go to the DNS tab and add the IP address of your wireless access point (usually)

:)

---

### Post by TrumpetMan258 on 2005-10-21
There's no wireless connection listed.  That's why I'm asking for help.  I need to do something to get the card working in the firstplace.

---

### Post by PaulBillett on 2005-10-22
[QUOTE=TrumpetMan258]There's no wireless connection listed.  That's why I'm asking for help.  I need to do something to get the card working in the firstplace.[/QUOTE]

The tool you need is ndiswrapper...  It's kinda complicated but once you come up with some more specific questions i'm sure the guys on the forum will help you out.  

I found this thread most helpful [https://wiki.ubuntu.com/NdiswrapperWithoutInternetAccessSlowFirefox](https://wiki.ubuntu.com/NdiswrapperWithoutInternetAccessSlowFirefox) it lead me to all the information i needed to setup my own broadcom wifi.

Paul

---

