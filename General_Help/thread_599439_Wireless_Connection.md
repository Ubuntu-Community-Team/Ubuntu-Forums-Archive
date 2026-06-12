---
title: "Wireless Connection"
date: 2007-11-01
forum: General Help
---

### Post by Graeme2804 on 2007-11-01
I can connect via my ethernet cable but the computer just can't find a wireless connection.  My wireless switch is on but it wont find anything.

I rang BT and they tried to remote assist and they don't support Linux.

They said to get help from Linux so here I am lol

I think i knocked the switch because I was connected a few hours ago and i found the switch off, so I switched it back on and it just isn't finding anything.


Anyone got any ideas?  I'm happy to allow remote assistance if thats possible, just want it sorting lol

---

### Post by Folk Theory on 2007-11-01
maybe you dont have a driver for the wireless device? i used to have a similar problem. you might wanna check what wireless device you have and wether there is a driver for it. if so get it if not then you might have to get ndiswrapper (from your disk or from internet) and get your windows driver for it.

---

### Post by ddrichardson on 2007-11-01
Hi,

If you go through the system help (the question icon on the taskbar) there is a guide to wireless. You can post back any difficulties you encounter.

---

### Post by Graeme2804 on 2007-11-01
> **Folk Theory said:**
> maybe you dont have a driver for the wireless device? i used to have a similar problem. you might wanna check what wireless device you have and wether there is a driver for it. if so get it if not then you might have to get ndiswrapper (from your disk or from internet) and get your windows driver for it.


driver for the wireless device?

i've used this computer for months wirelessly, and i've used linux for roughly 10 hours and it's worked fine wirelessly until about 1 hour ago.

---

### Post by Graeme2804 on 2007-11-01
I've not a clue where to start looking for help on wireless.

Not familiar with Linux yet.

---

### Post by ddrichardson on 2007-11-01
Like I said, in the help system System -> Help & Support there is a  section on troubleshooting wireless, however you didn't mention it dropped out an hour ago and was previously working. Have you checked the wireless access point or router you connect to to see if its operating?

---

### Post by ddrichardson on 2007-11-01
I'm going to assume you have a BT home hub here am I right?

---

### Post by Graeme2804 on 2007-11-01
You assume right, even though I really don't want a BT Home Hub ;) lol

---

### Post by ddrichardson on 2007-11-01
Reset the damn thing. I've got one and every now and again it crashes - looks like it's working but it doesn't. BT tech support are hopeless, based in a call centre in India with non-technical people running through a script solely for Windows.

---

### Post by Graeme2804 on 2007-11-01
It is working, step dad is using a laptop in the other room and he's connected.

I'm right next to the friggen thing using this ethernet cable.

argh I loath BT.


I've already tried the technical solution (switch on and off) and it's not worked.  Any ideas?

---

### Post by Graeme2804 on 2007-11-01
I've attatched a screenie of my network connections, there is no wireless there! :(

and the switch is on :S

---

### Post by ddrichardson on 2007-11-01
Have a look on the routers page [http://bthomehub.home/](http://bthomehub.home/) and check under devices to see if its seen your laptop.

---

### Post by Graeme2804 on 2007-11-01
> **ddrichardson said:**
> Have a look on the routers page [http://bthomehub.home/](http://bthomehub.home/) and check under devices to see if its seen your laptop.

My home network	
Devices currently connected to your BT Home Hub.
Wireless:	*****
Wireless:	*****
Ethernet:	*****
Ethernet:	Graemes-Laptop
Ethernet:	*****
USB:	No devices detected


***** = other comps

---

### Post by ddrichardson on 2007-11-01
Whats the output from iwconfig?

---

### Post by Graeme2804 on 2007-11-01
> **ddrichardson said:**
> Whats the output from iwconfig?

lo        no wireless extensions.

eth0      no wireless extensions.


thanks for the quick replys btw.

---

### Post by ddrichardson on 2007-11-01
Have you rebooted?

---

### Post by Graeme2804 on 2007-11-01
> **ddrichardson said:**
> Have you rebooted?

Both my laptop and the hub.

---

### Post by ddrichardson on 2007-11-01
What's the output of```
lspci | grep Network
```

---

### Post by Graeme2804 on 2007-11-01
> **ddrichardson said:**
> What's the output of```
lspci | grep Network
```

nothing :S

graeme@graeme:~$ lspci | grep Network
graeme@graeme:~$ lspci | grep Network
graeme@graeme:~$

---

### Post by ddrichardson on 2007-11-01
OK, is there any reference to a wireless card when you do lspci? If noot I'd check if the card is a mini-pci that it is still seated correctly.

---

### Post by Graeme2804 on 2007-11-01
> **ddrichardson said:**
> OK, is there any reference to a wireless card when you do lspci? If noot I'd check if the card is a mini-pci that it is still seated correctly.

in english?

lol

means nothing to me that, speak simpleten :)

---

### Post by Maestro23 on 2007-11-01
> **Graeme2804 said:**
> in english?

lol

means nothing to me that, speak simpleten :)

Open a terminal(Apps>>Accessories>>Terminal) and type:

> lspci

Look for any reference to your card.

---

### Post by ddrichardson on 2007-11-01
Yes, sorry - we need to see the output of```
lspci
```

---

### Post by Graeme2804 on 2007-11-01
ARGH!

lol

just re-booted computer because firefox was running very slow and it connected to wireless!

weird thing, i'll change title of the post to [SOLVED]

---

