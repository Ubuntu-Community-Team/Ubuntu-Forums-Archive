---
title: "Print unfiltered (Raw mode)"
date: 2014-06-04
forum: General Help
---

### Post by nipol-m on 2014-06-04
Hi all. I have no experience in linux systems and I wonder if someone can help me.  I need to print in raw mode in an EPSON FX2190, so as I've read I've tryed to intall it in Generic - Raw Queue, but wen I send to print a document only rare symbols are printed. Installins as "EPSON - 9 pin or Dot Matriz - Epson 9 pin series" and in terminal trying with "lp -d EPSON_PRINTER -o raw Archivo.prt" I can print the ascii document. I wonder if it is possible to configure the printer to print in raw mode automatically so I can print the files generated from my old DOS emulated app in DOSBox from any text editor like Geany or Gedit.  Any help please...  PD. I am holding this solution beacuse even though DOSBOx SVN Daum can print in LPT port but my printer is USB. :(. (I am using Ubuntu 14.04)

---

### Post by oldfred on 2014-06-04
Often Zebra printers needed Raw mode as you send it control codes for bar codes, similar to the old dot printers like your Epson.

I have not done this but it should be similar:
Zebra & raw print device:
[http://code.google.com/p/jzebra/](http://code.google.com/p/jzebra/)
[http://qzindustries.com/download](http://qzindustries.com/download)
[http://code.google.com/p/jzebra/wiki/TutorialRawUbuntu](http://code.google.com/p/jzebra/wiki/TutorialRawUbuntu)
[http://qzindustries.com/TutorialRawUbuntu](http://qzindustries.com/TutorialRawUbuntu)

---

### Post by nipol-m on 2014-06-04
Thanks for your fast reply.  About the first two links, they said that is "to send raw (industry/production) printer commands to your printer with php, jsp, ASP or JavaScript . jZebra is an open-source and open-API alternative.", I don't think it can help, or maybe I'm wrong. Respect the last two, is what I tryied and don't work, I'v read that it worked with and Epson LX-300 but didn't work too with a FX2190.

---

### Post by oldfred on 2014-06-04
I thought there were instructions on just configuring a printer?

Printing Raw out of a port should be the same regardless of printer, but are you using different ports?

Otherwise I cannot help.

If I do not have my USB printer on, it only gives a choice to install using Lpt0.
But if I turn on my printer I can select it. It wants to use the default driver, but I am able to choose RAW and have another print option for the same printer.

I used cups to configure printer.

---

### Post by lite.m.finocchiaro on 2014-12-14
Generally speaking, you will have to "add a printer" to your computer, even if the one connected to it is already installed with an Ubuntu-supplied or downloaded driver. I have an Epson TM-T88V connected to my Ubuntu install, and I can have a printer queue for that printer using the normal driver, a queue for the raw/generic driver, or both at the same time. I only use my receipt printer to test raw print jobs, so I only have the one queue now, but it's completely normal to have two queues for the same printer if you're using raw printing. Once you have your printer hooked up, the raw queue will want to talk to the same USB port each time, so moving the USB to another port will make the computer believe it's not connected.

I also recommend trying [demo.qzindustries.com](demo.qzindustries.com) to test your raw printing. This employs a trusted java applet to send the print jobs, but many printers are supported from that page, including your Zebra. It's also important to know which markup language your printer needs. My Epson and many Star printers use ESCP or ESC/P2, but FGL, ZPL, ZPL2, and others exist, and none of them are interchangeable with any of the others.

---

