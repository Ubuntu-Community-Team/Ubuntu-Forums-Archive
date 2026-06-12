---
title: "Wireless Card/USB"
date: 2008-05-23
forum: General Help
---

### Post by oligray on 2008-05-23
Hi i have two wireless adaptors for my pc

its new to me but not new.

im just installing windows.. but after that ubuntu will go on

:):):)



so in ubuntu.. i have  a belkin notebook card ( the computer has a slot)

and a usb netgear thing. will both of these work as soon as i plug them in if not which one will be easier to configure.

---

### Post by Monicker on 2008-05-23
Can you give some more information?  We need to know the specific model and revision numbers for the wireless adapters.

You can also take a look here: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")

---

### Post by bwhite82 on 2008-05-23
You can try searching Google with the following terms and see what you get:

belkin [model number] ubuntu
or
belkin [model number] linux

and do the same for the netgear.

In some cases you may need to know the chipset of the cards. Post if/when you have problems connecting so that we can help you more.

-Cheers

---

### Post by oligray on 2008-05-23
belkin F5D8010

and it says

"Follow instructions at [WWW] Welcome to Ubuntu for installation instructions. NetAni.inf file download available from site in a tar.gz form. Confirmed working for 6.10 Edgy Eft or later."

[http://welcometoubuntu.blogspot.com/2007/10/howto-get-airgo-based-wifi-enabled.html](http://welcometoubuntu.blogspot.com/2007/10/howto-get-airgo-based-wifi-enabled.html)


[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D8010?action=show&redirect=F5D8010](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D8010?action=show&redirect=F5D8010)


on those it tells me to download something.. does thayt mean at this point i have wireless... lol 

i dont think it does but tht means i will have to download it here and put it on tht computer

---

### Post by oligray on 2008-05-23
Not Good..

this was my grandads old pc and i reinstalled windows... it is a desktop 

and i think he installed the notebook card slot at a later date so i cant use it unless i take it out reinstall windows then put it back in.. loll

in ubuntu will it pick this up.. it could be because i used a dell cd. cos i didnt hav the  cd for this pc.. and it didnt have this note bookcard

will i be able to find the notebook card slot when i install ubuntu


im burning the disk now

---

### Post by bwhite82 on 2008-05-23
Yes, the slot will be recognized, its the card/s you *may* have problems with. The best thing to do is to install Ubuntu first, then, with the card/s inserted, boot into Ubuntu. You'll know right away whether one or both of them are working when you issue the command (from a terminal):

> ifconfig -a

The linux kernel contains a lot of drivers for some very obscure hardware, so you may be quite surprised if they work just fine.

---

