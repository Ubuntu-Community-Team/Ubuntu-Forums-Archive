---
title: "What's up with printing in Gutsy?"
date: 2007-12-19
forum: General Help
---

### Post by Ozor Mox on 2007-12-19
I've been using Gutsy for quite a while now but this is the first time I've had to set up printing in it, and I noticed that I didn't recognise the GUI at all. I've been trying to set it up for the HP Deskjet I have on my LAN, but none of the options would set up a configuration that worked. In the end, I had to turn on my other computer and look at what it put in the URI for the printer automatically with the old interface. Turns out it was socket://192.168.0.210 - presumably the IP of the printer...I would never have known that. I had to type in that URI manually in the new Gutsy interface. Quick Google search turned up that the old gnome-cups-manager interface was replaced with system-config-printer. How does one set up LAN printing with the new interface? I am very likely to forget the old way it did it automatically that I simply copied across!

---

### Post by RawMustard on 2007-12-21
Yep me too.  I have a hp laserjet on my lan that worked with every flavour of linux since back in the cave man days.  This new print thingy is borked.  I hate how they have to go and screw things that worked perfectly well for years and then claim thing just work, what a load of ********!  Gutsy is a disaster!

---

### Post by ronmarley1 on 2007-12-21
Hi,
I disagree with you (but am not looking for a flame war :)).  I'm just giving another perspective.  With the old CUPS manager, I had to ask my IT office for the IP address of the particular printer that I wanted to connect to.  With the new interface, I am able to browse the network at work and also mine at home and find the printer by name, load the driver, and print. 
Since the OP asked how to add a LAN printer, here's how I do it.  Bear in mind that in my work situation, I am printing through a Windows 2003 server.  At home, I am printing to a printer that is shared on a Windows XP box.  Both of the instances below are completed once I open the new Printing application.  I click on New printer button, wait for the search, and then click on Windows printer via SAMBA.  I then click the  Browse.. button.
At work (I teach high school), the printers are conveniently named by the room in which they are located.  I just find the printer by name and connect.
At home, the new interface "sees" my Windows workgroup and the computers of the workgoup.  Clicking on the twisty in front of the PC the printer is connected to reveals the printer by share name.  
I'm sorry it does not work for you.  I did not like the new app. at first, but changed my mind.

---

### Post by RawMustard on 2007-12-21
Well I did the same thing, it sees my network, sees my server, but does not see my printers no matter what I do.  I had to manually setup my printers through cups web interface.  Something I haven't needed to do in years!

Perhaps I wouldn't be so critical if several many other things weren't broken for me in Gutsy that worked fine in Feisty.  All in all, Gutsy has been a complete disaster for me :(

---

### Post by Ozor Mox on 2007-12-30
Well I suppose maybe this new interface does some things better and some things not so well, it was just a bit frustrating that something that worked automatically before suddenly did not work anymore and I had to rely on an older version of Ubuntu to give me the correct configuration for my printer.

Still, RawMustard, while we are still getting used to the new interface, I found that it is possible to simply install the old interface using apt-get. It's called gnome-cups-manager. Sorry about your other problems with Gutsy, I have to say this is one of my only ones so far.

---

