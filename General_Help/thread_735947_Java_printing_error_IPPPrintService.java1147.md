---
title: "Java printing error IPPPrintService.java:1147"
date: 2008-03-26
forum: General Help
---

### Post by elio.mussi on 2008-03-26
Printing from Java 1.6 gets the following error
        at sun.print.IPPPrintService.isAttributeValueSupported(IPPPrintService.java:1147)

It's an already known problem on Ubuntu 7.10. I've found an article on the net
[http://techxplorer.com/2008/02/21/printing-issues-with-java-on-linux/](http://techxplorer.com/2008/02/21/printing-issues-with-java-on-linux/)
where the author has fixed this problem changing "Orientation" to "Portrait" in the 
panel System.Administration.Printing for every prinetr defined.

Some people claim this fixed their problem. Unfortunately it didn't fix mine.

Anyone else is experiencing this ? Fixes? Comments? 
Does anyone has already printed under Ubuntu 8.04 with Java SE 1.6?

Thanks anyone in advance
Elio

---

### Post by elio.mussi on 2008-03-26
Do apologize for this post. It was my fault.
I was assuming I could print to the printing queue while the printer is not attached!
Java SE 1.6 under Ubuntu 7.10 do prints.(with a printer attached and ready)

---

