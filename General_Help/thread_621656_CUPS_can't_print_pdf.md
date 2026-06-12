---
title: "CUPS can't print pdf"
date: 2007-11-23
forum: General Help
---

### Post by danCF on 2007-11-23
I do tech work for a business that uses a Win2k3 terminal server on a LAN with many Windows XP machines being used as terminals to the TS. The guy who I work for was having problems with viruses when people used to local XP IE to surf the web. I suggested to him that we install ubuntu because it will not get viruses, and has what he needs (RDP client and Firefox). 

The terminals also have printers which were mounted within win2k3 over the lan. I figured I could use CUPS with ubuntu to accomplish the same thing.

I installed ubuntu on the machines, then installed the printers via IPP. Everything looked good, until people began to find that they could not print pdf files to the CUPS hosted printers. Apparently there is some glitch which keeps pdfs from being printed to CUPS servers, which is well documented with a google search, although the CUPS faqs claims that pdfs print fine.

Being able to print PDFs is a necessity for this company. Does anyone know how to fix this bug, or of a CUPS alternative to host a printer on a network for a windows based machine? Thanks.

---

### Post by p_quarles on 2007-11-24
Are these .pdf documents not printing at all, or are they just printing incorrectly? (wrong margins, etc.). 

If it's the first, I would guess that CUPS is just configured wrong. If it's the latter (and I've experienced that on many occasions), then the problem is more likely the application sending the document to the printer. Even though .pdf is supposed to be an open format, many documents will only work correctly with Adobe's Acrobat Reader. Fortunately, Acrobat Reader *is *available for Ubuntu:
[http://www.medibuntu.org/](http://www.medibuntu.org/)

Look under the "packages" tab.

---

### Post by danCF on 2007-11-24
Hi thanks for the response. The pdf files are not printing at all. I do not think it is because CUPS is misconfigured because i can print 100% fine from any other program (openoffice, firefox, etc).

Also these pdfs are being printed from a win2k3 server over the network, so I don't think installing adobe acrobat reader on the ubuntu machine itself would solve the problem, or would it?

---

### Post by p_quarles on 2007-11-24
I see what you're saying. I didn't realize the printer was hooked up to the Win2003 server in this situation. Since I have no experience with that software, I'm not sure what to tell you. I'm guessing, though, that since the printer is connected to the Windows server, the problem has something to do with the app you're using to print pdf docs being unable to communicate with the Windows printer driver. 

I can suggest, though, that you could run a pretty high-capacity printserver on a box with minimal specs (e.g., PII, 64-128 MB RAM) running Linux and Samba. This would depend on the printer model having a good Linux driver, of course, but if you happen to have a throwaway box lying around, that could be a good solution.

---

### Post by danCF on 2007-11-24
Well I would like the ubuntu desktops to each run their own little print server, which only deals with the local printer connected to that desktop, that will accept print jobs sent from the win2k3 server.

Do you know of a tutorial to setup samba on linux to accept print jobs?

---

### Post by p_quarles on 2007-11-24
This is a good starting point for using CUPS as a network printer driver:
[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu?highlight=%28printserver%29](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu?highlight=%28printserver%29)

For setting up Samba, I would recommend searching at howtoforge.com

That said, if these printers are all connected to individual workstations, it would make more sense to cut out the middle-man (W2k3 server) and run the printers directly from the Ubuntu boxes. You described them as "terminals," but they're obviously not thin clients (unless you're running them all from VMWare), so they should be able to handle their own printers. 

CUPS also allows you to set quotas, so employee waste/"borrowing" of resources is something that can be worked around.

---

### Post by danCF on 2007-11-24
> **p_quarles said:**
> 
That said, if these printers are all connected to individual workstations, it would make more sense to cut out the middle-man (W2k3 server) and run the printers directly from the Ubuntu boxes. You described them as "terminals," but they're obviously not thin clients (unless you're running them all from VMWare), so they should be able to handle their own printers. 

Sorry, my brain is fried, and I am explaining things horribly.

The printers are connected to the workstations, which are running ubuntu. However, employees sitting at these ubuntu workstations are also using "tsclient" to connect to a win2k3 server which is on the same LAN as all the ubuntu workstations. When the employees are working on the terminal 2k3 server from their ubuntu workstations, they need to be able to print to the printers that are connected to their ubuntu workstations.

I had CUPS configured on each ubuntu workstation. Then I set up each printer on the win2k3 server by entering "http://workstation_ip:631/printer/hp_laserjet" in the add networked printer wizard. This relay from win2k3 to the ubuntu machine via cups, and then from ubuntu to the printer worked fine, except when it came to pdf files.

---

### Post by p_quarles on 2007-11-24
> **danCF said:**
> Sorry, my brain is fried, and I am explaining things horribly.
Well, hey, that makes two of us. :)

> The printers are connected to the workstations, which are running ubuntu. However, employees sitting at these ubuntu workstations are also using "tsclient" to connect to a win2k3 server which is on the same LAN as all the ubuntu workstations. When the employees are working on the terminal 2k3 server from their ubuntu workstations, they need to be able to print to the printers that are connected to their ubuntu workstations.

I had CUPS configured on each ubuntu workstation. Then I set up each printer on the win2k3 server by entering "http://workstation_ip:631/printer/hp_laserjet" in the add networked printer wizard. This relay from win2k3 to the ubuntu machine via cups, and then from ubuntu to the printer worked fine, except when it came to pdf files.
I *think* I see what you're saying now. These are Ubuntu boxes, but they're using the Windows OS and apps via the tsclient? If that's right, now I understand why you'd want to setup Samba printservers on each workstation. This is a decent tutorial:
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

You won't need to set up each computer as a public fileserver, but the other parts of the tutorial are all relevant. And, again, for more information I'd suggest howtoforge.com. That site has a number of guides, and more than likely one of them will fit. 

Also, since you're using HP printers, do double-check that you have the HPLIP packages installed on each machine. These are open source drivers made available by HP, and in my experience they work very well.

---

### Post by danCF on 2007-11-24
> **p_quarles said:**
> Well, hey, that makes two of us. :)

Lol, well I can't really complain when I am getting free tech support at 2:30am. :) That site looks like it has what I need. I will go through it and if I still have problems I will post back here. Thanks so much for the help.

---

