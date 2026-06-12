---
title: "xsane /copy accumulate stopped printerjobs"
date: 2006-12-02
forum: General Help
---

### Post by randolph on 2006-12-02
It seems it's not only a cosmetic problem: when i copy (successful) a document with xsane the printer-symbol is laying around in the gnome-panel, status: "stopped:job-stopped". I have to manually delete every stopped job. Every copy of a document adds a "job-stopped". After a test with installed QuiteInsane there is no problem like this. Handling my scanner with xsane is my favorite, it would be nice to use xsane in future. Is there any explanation /solution from you?
Software: xsane 0.99, libsane 1.0.18-3, quiteinsane 0.10-11
Hardware: Epson Stylus C64 printer, Epson Perfection 1670 scanner
Adjustment in xsane/copy: command: lpr
I am using Ubuntu Dapper.

Completion 04.12.2006:

After a satisfiable copy of a document 2 files appeares in the folder /var/spool/cups. The first apparent is the jobnumber (c00053, 710 Byte, Typ unknown), the second is a PS-Document (d00053-001, 306,2 KB). This PS-Dokument at least is similar to the value of the printermessage in the gnome-panel (307,0 K, status: job-stopped). When i breake off the stopped-job the PS-Document in the folder /var/spool/cups is erased too and the printericon in the gnome-panel dissapears (that what i want).
Alignment of my Epson C64:
location: /dev/lp0, driver: high resolution picture(Gutenprint)(en)(commended), connection: printermodel local printer, (Parallel Port #1 (EPSON) or LPT #1, its never mind).
Weeks ago i toyed with CUPS in "localhost:631/admin", after that my printer was not recognized for some time, later i installed the printer satisfiable with the gnome-menu.
How can i prevent these bothersome PS-Documents? Maybe it is a CUPS-problem? and xsane is innocent of this?
Thanks for any idea! 

regards
randolph

---

