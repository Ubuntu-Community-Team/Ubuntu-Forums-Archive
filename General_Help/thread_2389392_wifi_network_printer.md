---
title: "wifi network printer"
date: 2018-04-16
forum: General Help
---

### Post by Bob_Younkin on 2018-04-16
I do tech support for a non-profit that does income taxes for seniors and the economically disadvantaged (VITA/TCE).  Twice a week, we set up a network of 5 computers (3 with Ubuntu 16.04, one with Mint, one with Ubuntu 17.10) and 1 or more Win10 computers from volunteers that bring their own machines.  We use the password protected wifi of the Senior Center offices nearby. The printer is attached to one of the 16.04 computers and "shared".  I have re-establish the network each time I set it up.  The other computers don't "remember" the shared printer.  The Windows people also can't find it. When we log in to the Senior Center, all of the computers automatically "discover" 4 network printers that the senior center has.  There are reasons we can't use those printers. I need something "plug and play" that my septuagenarian volunteers can just plug in and go, without my being there to set up the printer each time.  My sense is that this is about IP addresses.  The IP address of the "print server" is different each time.  I think I need a wireless printer that I can install on the network with a fixed IP address.  I don't want to drop $200 dollars of donated money and have it not work.  Thoughts/suggestions?

Bob

---

### Post by Autodave on 2018-04-16
Everyone here will have a different opinion of what works easily and what doesn't. Personally, I like HP printers and have never had an issue getting any HP printer to work. There will be a couple of files to install, but that goes w/o a hitch......at least in my experience.

---

### Post by Bob_Younkin on 2018-04-16
Me too, but hp-lip is installed on all the computers.  The problem is not that I can't install and share the printer.  The problem is that it is not persisitent.

Bob

---

### Post by Autodave on 2018-04-16
Maybe I am misunderstanding you.  I thought that the problem was with the printers that someone else owns and that you were thinking about buying your own printer?

I have 3 PCs here that all share the same wireless printer. Plus another laptop that occasionally uses it. All but one of the machines are shutdown at times and never have an issue reconnecting when finally powered on.

---

### Post by ajgreeny on 2018-04-16
You will need to make sure that the printer has a static IP address or the computers will keep trying to connect to an incorrect IP.

I simply add my printer to the list of reserved IPs in my router admin page, which I assume is possible for any router these days, and then setup the printer connection using hplip-toolbox which asks for manual setup of that static IP.

---

