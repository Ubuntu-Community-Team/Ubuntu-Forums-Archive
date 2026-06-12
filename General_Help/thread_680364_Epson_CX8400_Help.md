---
title: "Epson CX8400 Help"
date: 2008-01-27
forum: General Help
---

### Post by omarzipan on 2008-01-27
Hi, I am new to Ubuntu. I currently have the latest upgrade for my distribution, and I recently bought a new printer. The problem I have is when I attempt to print something, the printer just spits out paper. Are there anymore upgrades I need to install?
*I've never connected a printer to my Ubuntu computer, so maybe I need a certain program to configure my CX8400?

---

### Post by sfink16 on 2008-01-29
Here is the thread with details on the procedure to perform, particularly post by Weston (#24) downloading the ppd file to /usr/share/cups/model folder:

[http://ubuntuforums.org/showthread.php?t=568268&highlight=cx8400&page=3](http://ubuntuforums.org/showthread.php?t=568268&highlight=cx8400&page=3)

I tried this and was returned a "rastertopips failed" unfortunately.

Then I saw somewhere that installing the older CUPS driver from CX7800 instead of trying CX8400.  To do this go to Administration/Printers (this is from memory so I hope I'm correct in the terms).  The add a new printer (CX7800) and try using it.  

Then I went to [http://local:631](http://local:631) and made the necessary CUPS changes.  I can now print from the internet.

What I can't print from is any software app such as GIMP or .txt files.  I haven't tried the iScan changes for the scanner portion yet.

Hope someone can help you further!

Steve

---

