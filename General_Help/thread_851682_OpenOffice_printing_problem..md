---
title: "OpenOffice printing problem."
date: 2008-07-06
forum: General Help
---

### Post by JillSwift on 2008-07-06
I've been stumped by an odd little problem.

I'm printing from Kubuntu 8.04 and OpenOffice through CUPS to an HP Color LaserJet2600n on the network. This setup works just dandy save for one caveat:

If the print job is greater than about 603Kb it fails, silently. Kjobviewer shows these jobs has having successfully printed with 0 pages. CUPS shows these jobs as completes with "Unknown" pages.

If I export the document as a PDF and print it via KPDF the PDF prints fine (and the PDF jobs are larger than 603K - averaging 625K for the documents that failed to print from OOo).

I've checked and re-checked the settings, re-started CUPS and the printer, looked over the logs for CUPS (nothing!). I'm confused >.>;

---

### Post by JillSwift on 2008-07-07
Bump?

---

### Post by VMC on 2008-07-07
The only time I had trouble printing, was when I could only print one page or 1/2 a page. I then checked "System > Administration  > Printing", and clicked on the "Settings > Make and Model" and clicked on change. It then showed options and the default was different then the one I had selected. I then clicked it and it started working.

Check your printer status for any thing that might help:
```
lpstat -a -l -p
```

Also I installed HPLIP Toolbox.

there's a lot of info on this output:
```
sudo hp-check -r
```

---

### Post by JillSwift on 2008-07-08
> **VMC said:**
> The only time I had trouble printing, was when I could only print one page or 1/2 a page. I then checked "System > Administration  > Printing", and clicked on the "Settings > Make and Model" and clicked on change. It then showed options and the default was different then the one I had selected. I then clicked it and it started working.

Check your printer status for any thing that might help:
```
lpstat -a -l -p
```Also I installed HPLIP Toolbox.

there's a lot of info on this output:
```
sudo hp-check -r
```
Thanks for the hints. So far I've turned up nothing that would explain the behavior.

I'm kind-of thinking it may be running out of memory or some-such, but at this point I'm really just guessing. :(

---

### Post by VMC on 2008-07-08
I just re-read your first post. Maybe the problem lies in the network setup. How is the printer assigned through the network? Do you have other devices attached. 

I wouldn't think memory would be an issue as most printers have a stop code when the buffer is full.

---

### Post by JillSwift on 2008-07-09
> **VMC said:**
> I just re-read your first post. Maybe the problem lies in the network setup. How is the printer assigned through the network? Do you have other devices attached. 

I wouldn't think memory would be an issue as most printers have a stop code when the buffer is full.
I don't think I understand the first question. The printer is an HP with HP's lil built-in service. CUPS knows it as a socket://<address>:9100

Several other machines can print to it problem-free, two others running Kubuntu, one Ubuntu and one Windows XP. (All the Ubuntu/Kubuntu machines are 8.04)

I'm suspecting memory because I can re-create the problem from OOo by just building a document that creates a print job larger than 603k.

I don't think it's the printer itself as both it prints from other machines (including the documents that fail from this one machine) and the job never gets sent, it dies in processing.

---

### Post by catonano on 2008-07-14
> **VMC said:**
> I just re-read your first post. Maybe the problem lies in the network setup. How is the printer assigned through the network? Do you have other devices attached. 

I wouldn't think memory would be an issue as most printers have a stop code when the buffer is full.

Hello,

I have a similar problem with an hp laserjet 2500n

It works fine but if we print from OpenOffice it will only print in grays. NO color.

Printing from Gimp, printing pdf files from the document viewer goes fine. From OO ? No color.

I tried to move around the color settings in the print dialog window with no success.

If you want I can post output from any diagnostic tool you want.

Please help.
Thanks for any hint
bye
Cato

---

### Post by catonano on 2008-07-14
> **catonano said:**
> Hello,

I have a similar problem with an hp laserjet 2500n

It works fine but if we print from OpenOffice it will only print in grays. NO color.

Printing from Gimp, printing pdf files from the document viewer goes fine. From OO ? No color.

I tried to move around the color settings in the print dialog window with no success.


I reply to myself

I found the solution [here]("https://answers.launchpad.net/ubuntu/+source/openoffice.org/+question/5240")

It was about to set the option "greys" to off in the System->Administration->Printing windw instead than from the print options dialog window that's inside OpenOffice

It has to be a way in wich the apps relate with the centra settings. All the other apps force their own options, OpenOffice, as far as it seems, does not.

Thanks anyhow, for reading ;-)

---

### Post by JoBangles on 2008-09-03
Hi,
My problem is: Since update, all printer output is shrunk to approx. one third actual
size. Tried changing global and Application printer settings with no
effect.
System: Ubuntu 8.04 (hardy)
Kernel Linux 2.6.24-19-generic
Gnome 2.22.3
Memory: 1.9 GiB
AMD Athlon(tm) 64x2 Dual Core Processor 6000+
openoffice.org-core 1:2.4.1-lubuntu2. Mon Jun 30 11:50:15 UTC 2008
Printer: Epson Stylus C61 - CUPS+Gutenprint v5.0.2 Simplified

Have reported as Bug: 
[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/264523](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/264523)

Any suggestions?
Thanks in advance for any help.

---

### Post by JoBangles on 2008-09-03
The problem appears not to be OpenOffice as I just installed Koffice and the print reduction is still the same. Gedit prints O.K. Any clues please?
Thanks.

---

### Post by JoBangles on 2008-09-06
I have found that printing to pdf file then to printer works fine. I still would like to fix the glitch.
Thanks.

---

