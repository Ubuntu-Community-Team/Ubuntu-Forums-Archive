---
title: "Printing to Windows share makes enormous files, locks up printer"
date: 2006-10-22
forum: General Help
---

### Post by dwasifar on 2006-10-22
I'm helping out my neighbor who is trying to set up shared printing on his home network to an HP Officejet 4100 shared on a WinXP box.  All the other Windows boxes on the network print to it with no problem, but printing from Ubuntu never works.  

Ubuntu sees the Windows printer and can successfully queue to it, but even the simplest file creates a large file in the Windows queue (for example. an OpenOffice document containing only the two words "test page" creates a 7MB document in the queue).  The printer hangs.

I also see abnormally large documents in the queue on my home network when I print to Windows shares (though they usually print successfully).  Why does this happen?

---

### Post by dwasifar on 2006-10-23
bump

---

### Post by fred_scotland on 2006-11-13
Hi, 

You are lucky you can print at all, I have been messing around with this problem on and off for weeks, I can get the document to queue but the printer just hangs. I have a windows xp network and it runs well but you just cant get ubuntu to print to the HP1100 laser printer that is attached to an Xp machine. 

I have Ubuntu loaded onto a virtual computer using VMware Server on the XP machine and you can connect to it as a local printer and it prints no problem, but it won't go on the network. I am trying to get this going as i don't really want to carry on with microsoft, but you can see why a lot of people just load up linux find it doesn't work and buy another copy of windows.:( 


Fred

---

