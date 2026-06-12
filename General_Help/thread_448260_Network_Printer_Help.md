---
title: "Network Printer Help"
date: 2007-05-18
forum: General Help
---

### Post by n8dude on 2007-05-18
Hey guys, right now i've spent the whole day trying to get my network printer to work. The printer works when i do a direct connect (HPLIP  0.9.5) but when i connect it to my print server
(see below)
[http://netgear.com/Products/PrintServers/WiredPrintServers/PS121.aspx]("http://netgear.com/Products/PrintServers/WiredPrintServers/PS121.aspx")
it won't print from it. it recognizes the printer which by the way is a HP officejet 5610 multi-function, but when i try to print from it it attempts to send the page to the printer but nothing happens, ive tried setting it up in the hplip util, but it doesnt work. if anyone could tell me what im doing wrong that would be great. thanks for the help.

---

### Post by mbradlcu on 2007-05-19
I'm guessing when you say it works connecting the printer directly you mean to the same machine as you're cups server is on,, and I'm assuming you're using cups-server.. you may most likely have looked into this but what does the cups web interface say the status of the printer is? you sound like you're pretty experienced so apologies if this isn't any help.

---

### Post by n8dude on 2007-05-19
i'm not using a cups server right now, i'm using the netgear print server. i've looked on their website for drivers, but there are none. when i launch hplip, it recognizes the printer but can't send printing jobs to it. i dont know if that made much sense, but it works on my apple laptop and my dads xp desktop, just having trouble getting it to work in linux. i think it might just be my settings, but i'm really a noob when it comes to networking.

---

### Post by strabes on 2007-05-19
I don't understand the point of that piece of equipment is. Why can't you just plug your printer into a computer on your network, share it, and add it via the URL on your ubuntu box? ```
http://host.ip.goes.here:631/printers/printername
```

---

### Post by Murwiz on 2007-05-20
> **strabes said:**
> I don't understand the point of that piece of equipment is. Why can't you just plug your printer into a computer on your network, share it, and add it via the URL on your ubuntu box? ```
http://host.ip.goes.here:631/printers/printername
```

Well, for one thing a computer uses a lot more energy than a print server. Even in hibernate mode, a PC uses some electricity, and if set up as a print server, "hibernate" isn't a very useful default state. For me, my printer is actually on a different floor of the house than my main PC, so trucking downstairs to power up the server-PC is a big hassle.

Another factor is USB-connected printers; they just don't "share" well without something specialized in between to keep the driver happy.

---

### Post by n8dude on 2007-05-28
well, i got it working. i basically used these settings:
```
lpd://Print servers IP goes here/PS1B88CD_P1
```
so if any of you are using this print server, use those settings in CUPS.
:D

---

### Post by strabes on 2007-05-28
I meant connect the printer to a computer that is already on your network that would be using electricity anyway.

---

### Post by n8dude on 2007-05-28
ah, i see now. but i got it working so i'm happy.
do you think i should post a how-to?

---

### Post by mbradlcu on 2007-05-29
speaking for myself,, heck yes! that's good info!

---

