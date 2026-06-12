---
title: "CUPS - Officejet 4215 Problem - won't print"
date: 2007-07-29
forum: General Help
---

### Post by lespedeza on 2007-07-29
I recently upgraded to Feisty Fawn from Edgy Eft and I can no longer get my HP OfficeJet 4215 to print.

I've followed the procedure from [here]("https://help.ubuntu.com/community/HpAllInOne") using the hplip "hp-setup" program.  The wizard goes through fine, but when I go to print a test page, it says that it was sent to the printer successfully, but nothing happens.  The printer just sits there and does nothing.  I can view the job in KJobViewer and it shows as first being processed and then completed.

Pasted below is a section of the cups error log.  Anyone have any ideas on what's going on?

```
D [29/Jul/2007:16:55:27 -0400] cupsdAcceptClient: 10 from localhost (Domain)
D [29/Jul/2007:16:55:27 -0400] cupsdCloseClient: 11
D [29/Jul/2007:16:55:27 -0400] cupsdReadClient: 10 POST /printers/ HTTP/1.1
D [29/Jul/2007:16:55:27 -0400] cupsdAuthorize: username="root"
D [29/Jul/2007:16:55:27 -0400] CUPS-Get-Default
D [29/Jul/2007:16:55:27 -0400] cupsdProcessIPPRequest: 10 status_code=0 (successful-ok)
D [29/Jul/2007:16:55:27 -0400] cupsdAcceptClient: 11 from localhost (Domain)
D [29/Jul/2007:16:55:27 -0400] cupsdCloseClient: 10
D [29/Jul/2007:16:55:27 -0400] cupsdReadClient: 11 POST /printers/ HTTP/1.1
D [29/Jul/2007:16:55:27 -0400] cupsdAuthorize: username="root"
D [29/Jul/2007:16:55:27 -0400] Get-Printer-Attributes ipp://localhost:631/printers/officejet_4200
D [29/Jul/2007:16:55:27 -0400] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [29/Jul/2007:16:55:27 -0400] cupsdAcceptClient: 10 from localhost (Domain)
D [29/Jul/2007:16:55:27 -0400] cupsdCloseClient: 7
D [29/Jul/2007:16:55:27 -0400] cupsdCloseClient: 11
D [29/Jul/2007:16:55:27 -0400] cupsdReadClient: 10 POST / HTTP/1.1
D [29/Jul/2007:16:55:27 -0400] cupsdAuthorize: No authentication data provided.
D [29/Jul/2007:16:55:27 -0400] Get-Printer-Attributes ipp://localhost/printers/officejet_4200
D [29/Jul/2007:16:55:27 -0400] cupsdProcessIPPRequest: 10 status_code=0 (successful-ok)
D [29/Jul/2007:16:55:27 -0400] cupsdReadClient: 10 GET /printers/officejet_4200.ppd HTTP/1.1
D [29/Jul/2007:16:55:27 -0400] cupsdAuthorize: No authentication data provided.
D [29/Jul/2007:16:55:27 -0400] write_file: 10 file=7
D [29/Jul/2007:16:55:27 -0400] cupsdAcceptClient: 7 from localhost (Domain)
D [29/Jul/2007:16:55:27 -0400] cupsdReadClient: 7 POST / HTTP/1.1
D [29/Jul/2007:16:55:27 -0400] cupsdAuthorize: username="root"
D [29/Jul/2007:16:55:27 -0400] Get-Jobs ipp://localhost:631/printers/officejet_4200
D [29/Jul/2007:16:55:27 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [29/Jul/2007:16:55:27 -0400] cupsdCloseClient: 7
D [29/Jul/2007:16:55:32 -0400] cupsdAcceptClient: 7 from localhost (Domain)
D [29/Jul/2007:16:55:32 -0400] cupsdReadClient: 7 POST /printers/ HTTP/1.1
D [29/Jul/2007:16:55:32 -0400] cupsdAuthorize: username="root"
D [29/Jul/2007:16:55:32 -0400] CUPS-Get-Printers
D [29/Jul/2007:16:55:32 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [29/Jul/2007:16:55:32 -0400] cupsdAcceptClient: 11 from localhost (Domain)
D [29/Jul/2007:16:55:32 -0400] cupsdCloseClient: 7
D [29/Jul/2007:16:55:32 -0400] cupsdReadClient: 11 POST /classes/ HTTP/1.1
D [29/Jul/2007:16:55:32 -0400] cupsdAuthorize: username="root"
D [29/Jul/2007:16:55:32 -0400] CUPS-Get-Classes
D [29/Jul/2007:16:55:32 -0400] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [29/Jul/2007:16:55:32 -0400] cupsdAcceptClient: 7 from localhost (Domain)
D [29/Jul/2007:16:55:32 -0400] cupsdCloseClient: 11
D [29/Jul/2007:16:55:32 -0400] cupsdReadClient: 7 POST /printers/ HTTP/1.1
D [29/Jul/2007:16:55:32 -0400] cupsdAuthorize: username="root"
D [29/Jul/2007:16:55:32 -0400] CUPS-Get-Default
D [29/Jul/2007:16:55:32 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [29/Jul/2007:16:55:32 -0400] cupsdCloseClient: 7
D [29/Jul/2007:16:55:32 -0400] cupsdAcceptClient: 7 from localhost (Domain)
D [29/Jul/2007:16:55:32 -0400] cupsdReadClient: 7 POST /printers/ HTTP/1.1
D [29/Jul/2007:16:55:32 -0400] cupsdAuthorize: username="root"
D [29/Jul/2007:16:55:32 -0400] Get-Printer-Attributes ipp://localhost:631/printers/officejet_4200
D [29/Jul/2007:16:55:32 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [29/Jul/2007:16:55:32 -0400] cupsdAcceptClient: 11 from localhost (Domain)
D [29/Jul/2007:16:55:32 -0400] cupsdCloseClient: 10
D [29/Jul/2007:16:55:32 -0400] cupsdCloseClient: 7
D [29/Jul/2007:16:55:32 -0400] cupsdReadClient: 11 POST / HTTP/1.1
D [29/Jul/2007:16:55:32 -0400] cupsdAuthorize: No authentication data provided.
D [29/Jul/2007:16:55:32 -0400] Get-Printer-Attributes ipp://localhost/printers/officejet_4200
D [29/Jul/2007:16:55:32 -0400] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [29/Jul/2007:16:55:32 -0400] cupsdReadClient: 11 GET /printers/officejet_4200.ppd HTTP/1.1
D [29/Jul/2007:16:55:32 -0400] cupsdAuthorize: No authentication data provided.
D [29/Jul/2007:16:55:32 -0400] write_file: 11 file=7
D [29/Jul/2007:16:55:32 -0400] cupsdAcceptClient: 7 from localhost (Domain)
D [29/Jul/2007:16:55:32 -0400] cupsdReadClient: 7 POST / HTTP/1.1
D [29/Jul/2007:16:55:32 -0400] cupsdAuthorize: username="root"
D [29/Jul/2007:16:55:32 -0400] Get-Jobs ipp://localhost:631/printers/officejet_4200
D [29/Jul/2007:16:55:32 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [29/Jul/2007:16:55:32 -0400] cupsdCloseClient: 7

```

I've also tried installing the printer using the KDE System Settings interface and I get the same results.  I have other USB devices that are working fine, so I don't think that it's a USB communication problem.

Any ideas?  Thanks for your help.

Edit:

Problem solved.  Needed to install the following packages and everything worked fine.

hpijs 
foomatic-db-hpijs

---

