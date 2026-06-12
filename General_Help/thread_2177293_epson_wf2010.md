---
title: "epson wf2010"
date: 2013-09-28
forum: General Help
---

### Post by witblits19702 on 2013-09-28
Hi, i have recently bought the prinet Epson WF2010. i have set the priner up etc but can't get it to print at all. After a long time of scratching my close to getting bald head i amanged to get it to go through the printing motions and a short lived joyious expression i noticed a blank page. is there drivers for this priner as i ahve downloaded some from ol inetrnet but no joy? when i ran some of the drivers via synaptic and software centre i'm gracefully made aware sopme dependancies are missing. i managed to get the PPD file but even then no print success. :confused:
any ideas please, thanks

---

### Post by gordintoronto on 2013-09-28
The procedure varies by version and flavor, of Ubuntu, so that information might be helpful.

If it makes the print head move, but not print, you need to get rid of the things you have obtained, they will only interfere with the solution.

Then, the best way is to run the program "printers" or "printing," depending on version. There will be a plus-sign icon or the word Add, select it. If you have the WF2010 set up as a network printer, click on that option in the list, and wait a few seconds. The printer should appear in the list; click on it and select Yes, OK, Continue or whatever until the printer is installed. At the end it should let you print a test page.

If the printer does not appear, you might need to install cups.

---

### Post by witblits19702 on 2013-09-28
thanks, CUPS installed but no joy, printhead moves but no ink on paper! :(

---

### Post by Mark Phelps on 2013-09-28
Since this is a new printer (apparently), you need to read through the instructions that came with it to perform a self-test -- that will run the printer and print a test page, using only the information available in the printer.  If that self-test page does not print, it's a hardware problem with the printer and you won't be able to fix that from Linux or any other OS.

---

