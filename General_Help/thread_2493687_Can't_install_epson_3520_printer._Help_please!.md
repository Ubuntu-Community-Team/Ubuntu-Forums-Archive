---
title: "Can't install epson 3520 printer. Help please!"
date: 2023-12-21
forum: General Help
---

### Post by wally1960 on 2023-12-21
Hello all, I've just installed Lubuntu 22.04 on my old dell desktop. First I installed the printer-driver-escpr from the repository. This didn't work. Second I downloaded the proper epson debian driver from their website and installed, no joy. These are the two methods I found with internet searches (openprinting.org, stackexchange, etc.).

1. How do I check which driver is recognized by my system?
2. What am I doing wrong?

This is a simple usb printer, hooked up to my computer. Not a network printer.

Any help would be appreciated.

---

### Post by yancek on 2023-12-21
How did you try to configure the printer?  I would suggest you read the instructions at the link below and try them if you haven't.  Also, saying things like 'didn't work' and 'no joy' are not going to help you get help.  You need to explain exactly what happens when you try to print.  Do you get any messages about the print failure?  Does it show success and nothing prints?  When you go to the Settings menu and printer, does your printer show up?

---

### Post by MAFoElffen on 2023-12-21
Did you look for the Linux driver at Epson Support Downloads? 

RE: [http://download.ebz.epson.net/dsc/search/01/search/](http://download.ebz.epson.net/dsc/search/01/search/)
```

[TABLE="class: searchResTbl"]
[TR]
[TD]WF-3520 Series
[/TD]
 			[TD]Printer Driver[/TD]
 			[TD]Linux
[/TD]
 			[TD]latest
[/TD]
 			[TD]ESC/P Driver (full feature)[/TD]
 			[TD]All language
[/TD]
 			[TD]09-18-2012[/TD]
 			[TD] 			
[/TD]
[/TR]
[TR]
 			[TD]WF-3520 Series
[/TD]
 			[TD]Printer Driver[/TD]
 			[TD]Linux
[/TD]
 			[TD]1.8.2
[/TD]
 			[TD]Epson Inkjet Printer Driver (ESC/P-R) for Linux[/TD]
 			[TD]All language
[/TD]
 			[TD]11-09-2023[/TD]
 			[TD] 			
[/TD]
[/TR]
[TR]
 			[TD]WF-3520 Series
[/TD]
 			[TD]Printer Driver[/TD]
 			[TD]Linux
[/TD]
 			[TD]1.1.2
[/TD]
 			[TD]Epson Printer Utility for Linux[/TD]
 			[TD]All language
[/TD]
 			[TD]11-09-2023[/TD]
 			[TD] 			
[/TD]
[/TR]
[TR]
 			[TD]WF-3520 Series
[/TD]
 			[TD]Printer Driver[/TD]
 			[TD]Linux
[/TD]
 			[TD]1.1.1
[/TD]
 			[TD]Epson PC-Fax Driver for Linux[/TD]
 			[TD]All language
[/TD]
 			[TD]11-08-2023[/TD]
 			[TD] 			
[/TD]
[/TR]
[TR]
 			[TD]WF-3520 Series
[/TD]
 			[TD]Scanner Driver[/TD]
 			[TD]Linux
[/TD]
 			[TD]2.30.4
[/TD]
 			[TD]All-in-one package[/TD]
 			[TD]All language
[/TD]
 			[TD]03-31-202[/TD]
[/TR]
[/TABLE]

```
Those are all Linux Drivers for that printer...

---

### Post by wally1960 on 2023-12-22
Yancek, either using the Printer-driver-escpr from the repos or the epson driver 201212w_1.0.0-1lsb3.2_from their website, the cups gui recognizes the printer but when printing a test page dosn't print. The printer sounds like it's printing, but there is nothing printed. I've installed a new printer cartridge, so that's not the problem. As I've already said this is a simple usb printer. 
Going online to localhost:631 shows the printer and the epson driver installed, but can't print anything. No ink on paper!
Anyone have any ideas

---

### Post by ActionParsnip on 2023-12-22
In future please give FULL product details you most likely have an "Epson WorkForce WF-3520DWF" not an "Epson 3520". Accuracy is awesome :guitar:

---

### Post by wally1960 on 2023-12-22
The label says epson wf-3520. Any idea what the solution is?

---

