---
title: "Network Printer - Edgy - WinXP"
date: 2007-09-10
forum: General Help
---

### Post by JimS on 2007-09-10
...
Printer = HP-1320 laser printer setup on lpt1 and works fine w/ Edgy PC.
Printer = HP-2210 all-in-one on USB.  Also works fine, printing and scanning w/ Edgy.
PC = Dell 4100 (ca 2000) duel boot WinME and Edgy on separate HDs.
Network = 3 PCs wired to Linksys router.
ISP is a cable provider.  
Also have 2 Lingo VoIPs, one connected to cable modem, other to router.
I.e. a daisy chain, modem, 1st VoIP box, router, 2nd VoIP box.   All work fine.

Networked Computers:
1.  The old Dell 4100, has both printers connected.
2.  Compaq desktop (ca 2004) WinXP/  No printer connected.
3.  Toshiba notebook (ca 2005) WinXP and Xubuntu Feisty.  No printer connected.

Issue:
I want to be able to print from WinXP PCs to the HP-1320 and HP-2210..
How do I setup the old Dell w/ Edgy?  (Old Dell is connected to both printers)
Will I need Samba to be able to print from WinXP boxes?
...
Thanks,
JimS
...

---

### Post by sumguy231 on 2007-09-10
Instead of using Samba to print from Windows, you can just use CUPS sharing. You will of course need the Windows printer drivers for the printer you're using. You can get those from HP's website. 
1.) Go to [http://localhost:631](http://localhost:631) in your web browser.
2.) Go to 'printers'.
3.) Click on the printer you want. Copy the url. Mine looks like this at this point:
[http://localhost:631/printers/Agent_Q](http://localhost:631/printers/Agent_Q)
4.) Go through the add printer Wizard on Windows XP. Select 'network printer', and then select the third option there. Put in the url you got, except replace localhost with the IP address of the computer connected to the printer. For example:
[http://192.168.1.5:631/printers/Agent_Q](http://192.168.1.5:631/printers/Agent_Q)
5.) Finish the wizard, install the drivers. You're done. You may repeat this with the other printer.

> How do I setup the old Dell w/ Edgy? (Old Dell is connected to both printers)
I'm a little confused here. Is the old Different from the one already connected to the printer?

---

### Post by JimS on 2007-09-27
///
You procedure worked for my XP box.
Thanks

But not for my laptop w/ Xubuntu.
All I get is a 6-line message on the printout.
The first line is:
-12345X@PJL SET PAGEPROTECT=AUTO
The rest is resolution, density, duplex, and language followed by a long line of code.
///

---

