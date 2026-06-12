---
title: "HP PSC-2175 driver on XP Client tricks"
date: 2007-08-13
forum: General Help
---

### Post by Purplecatty on 2007-08-13
Anyone who are struggling with HP PSC 2175 All-in-One printer driver on XP client machine while Ubuntu Feisty Fawn 7.04 which is connected to printer. The XP Client machine don't have driver for it and it cannot find driver from HP PSC 2170 serie CDrom.  

    I found a way to get it working.  Best thing is to install HP PSC 2175 driver from CDrom on Client XP machine first.  Just check radio button "proceed installation without plugging in USB".  After installation.  then follow this instruction below..

On XP machine.  Navigate to Printers and faxes in Control Panel or Start Menu (if listed), Click "Add Printer" and choose Network Printer and then choose radio button "Connect to a printer on an internet..." and type URL

"http://<printserver name>:631/printers/psc-2175"  
(Printserver name is what on your Ubuntu box like example "John-Desktop" or "Kitty-Desktop"..  You can find Ubuntu's server name on XP Client's  network printer browse for quicker reference..  Be sure to add ":631" on the end before "/printers/psc-2175")

select driver on pop up driver list "HP-- PSC-950" (it is necessary to get em shut up!)and click OK

Once new default printer icon showed up on Printers and Faxes Window.

Right click new icon for drop down menu.  Click Property.

Here's the MAGIC!!!

On tabs, Choose ADVANCED and click Driver

Scroll down and BINGO!! here is HP PSC 2170 serie driver.  Click on it and click OK to change the driver

Then test your printer.  It should print out with no problem! (It'll show Windows XP printer driver blah blah on printout from PSC 2175 through Ubuntu print server)

If you had different model printer and can't get driver for XP client, just Install it from CDrom and setup network printer then change the driver AFTER that!!
:grin::grin::grin:

---

