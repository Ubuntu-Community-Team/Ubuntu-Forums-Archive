---
title: "[SOLVED] Printer Issues - Setting up drivers"
date: 2007-05-19
forum: General Help
---

### Post by Beatbreaker on 2007-05-19
Hey i've just installed Ubuntu on my puter, i'm most impressed with it but im a little worried i won't be able to use it if i can't get my network printers to work on it.

basically i can see the 2 printers on the network in Ubuntu, it's the drivers i've got no idea i'll be able to get my hands on (or have i been looking in the wrong places?)

i need drivers for a Brother MFC-7420 and a HP PSC-2355

any help will be most appreciated

---

### Post by dbott67 on 2007-05-19
You can try using drivers from printers in the same printer family (try the HP PSC-2350).  For the Brother, try these instructions:

[http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html)

There's a link in the document referring to the MFC-7420 that takes you here:

[http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install5.html](http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install5.html)


-Dave

---

### Post by Beatbreaker on 2007-05-19
wow many thankx for pulling up those links, i'll give them a try and let you know how i go

---

### Post by Beatbreaker on 2007-05-20
holy crap that's hard, is this something that would take a beginner some time to get right?

---

### Post by The Pinny Parlour on 2007-05-20
Welcome to Ubuntu printing.  If you think that's hard don't start Networking with Samba.   
Come on Mr. Shuttleworth, make it happen easier.

---

### Post by volkswagner on 2007-05-20
I am in the same boat Brother MFC5440CN network printer.  I have both packages from brother 
1 lpr
2  cupswrapper

I install lpr then cupswrapper.  When i add printer my machine is recognized when i try to install it my model is not listed.  If i clik install driver i can't locate the ppd file.  It is not located where brother says it is.  I tried downloading file again....same problem.. Any advice

UBUNTU ROCKS MY LAPTOP MADE A DUAL BOOT MAY NEVER HAVE TO USE VISTA IF I CAN GET MY PRINTER WORKING AND SOUND CARD!

---

### Post by Beatbreaker on 2007-05-27
> **volkswagner said:**
> I am in the same boat Brother MFC5440CN network printer.  I have both packages from brother 
1 lpr
2  cupswrapper

I install lpr then cupswrapper.  When i add printer my machine is recognized when i try to install it my model is not listed.  If i clik install driver i can't locate the ppd file.  It is not located where brother says it is.  I tried downloading file again....same problem.. Any advice

UBUNTU ROCKS MY LAPTOP MADE A DUAL BOOT MAY NEVER HAVE TO USE VISTA IF I CAN GET MY PRINTER WORKING AND SOUND CARD!

i don't know if what i'm doingis right either, 

i downloaded the .deb file and installed it

then i went to add a printer, and browsed for the PPD file ...

 The PPD file is located in the directory: /usr/share/cups/model

i've done all that, but it still doesn't work

--> is it normally to hard to print through a LAN from linux to XP?

---

### Post by Beatbreaker on 2007-05-27
> **Beatbreaker said:**
> i don't know if what i'm doingis right either, 

i downloaded the .deb file and installed it

then i went to add a printer, and browsed for the PPD file ...

 The PPD file is located in the directory: /usr/share/cups/model

i've done all that, but it still doesn't work

--> is it normally to hard to print through a LAN from linux to XP?

HAHA oops, i forgot to install the LPR driver first - NOW the Brother printer works. It's the main printer so i'm not too fussed about the HP one working.

Many thanks to everyone who helped me with this one!

---

