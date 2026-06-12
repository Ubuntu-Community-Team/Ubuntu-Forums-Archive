---
title: "cupsys: Unable to accept client connection - Too many open files."
date: 2007-06-05
forum: General Help
---

### Post by Flane on 2007-06-05
Hi,

we have a serious problem using cupsys 1.2.8-0ubuntu8 from samba.
At first everything works fine and we can print to the attached HP Laserjet 4L without any problems.

But suddently printing failed with the error message
Unable to accept client connection - Too many open files.

I switch to verbose level and got the following log file (don't know how to reproduce but it fails every 2-4 days)

```

D [05/Jun/2007:09:14:36 +0200] [Job 77] File 0 is complete.
D [05/Jun/2007:09:14:36 +0200] Discarding unused printer-state-changed event...
D [05/Jun/2007:09:14:36 +0200] Discarding unused job-completed event...
D [05/Jun/2007:09:14:37 +0200] Unloading job 77...
D [05/Jun/2007:09:22:01 +0200] cupsdAcceptClient: 1023 from localhost (Domain)
D [05/Jun/2007:09:22:01 +0200] cupsdReadClient: 1023 POST / HTTP/1.1
D [05/Jun/2007:09:22:01 +0200] cupsdAuthorize: No authentication data provided.
D [05/Jun/2007:09:22:01 +0200] CUPS-Get-Printers
D [05/Jun/2007:09:22:01 +0200] cupsdProcessIPPRequest: 1023 status_code=0 (successful-ok)
D [05/Jun/2007:09:22:01 +0200] cupsdReadClient: 1023 POST / HTTP/1.1
D [05/Jun/2007:09:22:01 +0200] cupsdAuthorize: No authentication data provided.
D [05/Jun/2007:09:22:01 +0200] CUPS-Get-Classes
D [05/Jun/2007:09:22:01 +0200] cupsdProcessIPPRequest: 1023 status_code=0 (successful-ok)
D [05/Jun/2007:09:22:01 +0200] cupsdCloseClient: 1023
D [05/Jun/2007:09:24:21 +0200] cupsdAcceptClient: 1023 from localhost (Domain)
D [05/Jun/2007:09:24:21 +0200] cupsdReadClient: 1023 POST / HTTP/1.1
D [05/Jun/2007:09:24:21 +0200] cupsdAuthorize: No authentication data provided.
D [05/Jun/2007:09:24:21 +0200] Get-Jobs ipp://localhost/printers/lp_gelb
D [05/Jun/2007:09:24:21 +0200] cupsdProcessIPPRequest: 1023 status_code=0 (successful-ok)
D [05/Jun/2007:09:24:21 +0200] cupsdReadClient: 1023 POST / HTTP/1.1
D [05/Jun/2007:09:24:21 +0200] cupsdAuthorize: No authentication data provided.
D [05/Jun/2007:09:24:21 +0200] Get-Printer-Attributes ipp://localhost/printers/lp_gelb
D [05/Jun/2007:09:24:21 +0200] cupsdProcessIPPRequest: 1023 status_code=0 (successful-ok)
E [05/Jun/2007:09:24:21 +0200] Unable to accept client connection - Too many open files.
D [05/Jun/2007:09:24:21 +0200] cupsdCloseClient: 1023
D [05/Jun/2007:09:24:21 +0200] cupsdAcceptClient: 1023 from localhost (Domain)
D [05/Jun/2007:09:24:21 +0200] cupsdReadClient: 1023 POST / HTTP/1.1
D [05/Jun/2007:09:24:21 +0200] cupsdAuthorize: No authentication data provided.
D [05/Jun/2007:09:24:21 +0200] Get-Jobs ipp://localhost/printers/lp
D [05/Jun/2007:09:24:21 +0200] cupsdProcessIPPRequest: 1023 status_code=0 (successful-ok)
D [05/Jun/2007:09:24:21 +0200] cupsdReadClient: 1023 POST / HTTP/1.1
D [05/Jun/2007:09:24:21 +0200] cupsdAuthorize: No authentication data provided.
D [05/Jun/2007:09:24:21 +0200] Get-Printer-Attributes ipp://localhost/printers/lp
D [05/Jun/2007:09:24:21 +0200] cupsdProcessIPPRequest: 1023 status_code=0 (successful-ok)
D [05/Jun/2007:09:24:21 +0200] cupsdCloseClient: 1023
D [05/Jun/2007:09:27:57 +0200] cupsdAcceptClient: 1023 from localhost (Domain)
D [05/Jun/2007:09:27:57 +0200] cupsdReadClient: 1023 POST / HTTP/1.1
D [05/Jun/2007:09:27:57 +0200] cupsdAuthorize: No authentication data provided.
D [05/Jun/2007:09:27:57 +0200] Get-Jobs ipp://localhost/printers/lp
D [05/Jun/2007:09:27:57 +0200] cupsdProcessIPPRequest: 1023 status_code=0 (successful-ok)
D [05/Jun/2007:09:27:57 +0200] cupsdReadClient: 1023 POST / HTTP/1.1
D [05/Jun/2007:09:27:57 +0200] cupsdAuthorize: No authentication data provided.
D [05/Jun/2007:09:27:57 +0200] Get-Printer-Attributes ipp://localhost/printers/lp
D [05/Jun/2007:09:27:57 +0200] cupsdProcessIPPRequest: 1023 status_code=0 (successful-ok)
D [05/Jun/2007:09:27:57 +0200] cupsdCloseClient: 1023
D [05/Jun/2007:09:27:59 +0200] cupsdAcceptClient: 1023 from localhost (Domain)
D [05/Jun/2007:09:27:59 +0200] cupsdReadClient: 1023 POST /printers/lp HTTP/1.1
D [05/Jun/2007:09:27:59 +0200] cupsdAuthorize: No authentication data provided.
D [05/Jun/2007:09:27:59 +0200] cupsdSendError: 1023 code=413 (Request Entity Too Large)
D [05/Jun/2007:09:27:59 +0200] cupsdCloseClient: 1023
D [05/Jun/2007:09:29:03 +0200] cupsdAcceptClient: 1023 from localhost (Domain)
D [05/Jun/2007:09:29:03 +0200] cupsdReadClient: 1023 POST / HTTP/1.1
D [05/Jun/2007:09:29:03 +0200] cupsdAuthorize: No authentication data provided.
D [05/Jun/2007:09:29:03 +0200] Get-Jobs ipp://localhost/printers/lp
D [05/Jun/2007:09:29:03 +0200] cupsdProcessIPPRequest: 1023 status_code=0 (successful-ok)
D [05/Jun/2007:09:29:03 +0200] cupsdReadClient: 1023 POST / HTTP/1.1
D [05/Jun/2007:09:29:03 +0200] cupsdAuthorize: No authentication data provided.
D [05/Jun/2007:09:29:03 +0200] Get-Printer-Attributes ipp://localhost/printers/lp
D [05/Jun/2007:09:29:03 +0200] cupsdProcessIPPRequest: 1023 status_code=0 (successful-ok)
D [05/Jun/2007:09:29:03 +0200] cupsdCloseClient: 1023
D [05/Jun/2007:09:29:06 +0200] cupsdAcceptClient: 1023 from localhost (Domain)
D [05/Jun/2007:09:29:06 +0200] cupsdReadClient: 1023 POST /printers/lp HTTP/1.1
D [05/Jun/2007:09:29:06 +0200] cupsdAuthorize: No authentication data provided.
D [05/Jun/2007:09:29:06 +0200] cupsdSendError: 1023 code=413 (Request Entity Too Large)
E [05/Jun/2007:09:29:06 +0200] cupsdReadClient: Unable to write 32768 bytes to /var/spool/cups/00000002: Bad file descriptor
D [05/Jun/2007:09:29:06 +0200] cupsdSendError: 1023 code=413 (Request Entity Too Large)
D [05/Jun/2007:09:29:06 +0200] cupsdCloseClient: 1023
D [05/Jun/2007:09:29:22 +0200] cupsdAcceptClient: 1023 from localhost (Domain)
D [05/Jun/2007:09:29:22 +0200] cupsdReadClient: 1023 POST / HTTP/1.1
D [05/Jun/2007:09:29:22 +0200] cupsdAuthorize: No authentication data provided.
D [05/Jun/2007:09:29:22 +0200] CUPS-Get-Printers
D [05/Jun/2007:09:29:22 +0200] cupsdProcessIPPRequest: 1023 status_code=0 (successful-ok)
D [05/Jun/2007:09:29:22 +0200] cupsdReadClient: 1023 POST / HTTP/1.1
D [05/Jun/2007:09:29:22 +0200] cupsdAuthorize: No authentication data provided.
D [05/Jun/2007:09:29:22 +0200] CUPS-Get-Classes
D [05/Jun/2007:09:29:22 +0200] cupsdProcessIPPRequest: 1023 status_code=0 (successful-ok)
D [05/Jun/2007:09:29:22 +0200] cupsdReadClient: 1023 POST / HTTP/1.1
D [05/Jun/2007:09:29:22 +0200] cupsdAuthorize: No authentication data provided.
D [05/Jun/2007:09:29:22 +0200] CUPS-Get-Default
D [05/Jun/2007:09:29:22 +0200] cupsdProcessIPPRequest: 1023 status_code=0 (successful-ok)
D [05/Jun/2007:09:29:23 +0200] cupsdReadClient: 1023 POST / HTTP/1.1
D [05/Jun/2007:09:29:23 +0200] cupsdAuthorize: No authentication data provided.
D [05/Jun/2007:09:29:23 +0200] Get-Printer-Attributes ipp://localhost/printers/lp
D [05/Jun/2007:09:29:23 +0200] cupsdProcessIPPRequest: 1023 status_code=0 (successful-ok)
D [05/Jun/2007:09:29:23 +0200] cupsdReadClient: 1023 POST / HTTP/1.1
D [05/Jun/2007:09:29:23 +0200] cupsdAuthorize: No authentication data provided.
D [05/Jun/2007:09:29:23 +0200] Get-Jobs ipp://localhost/printers/lp
D [05/Jun/2007:09:29:23 +0200] cupsdProcessIPPRequest: 1023 status_code=0 (successful-ok)
D [05/Jun/2007:09:29:23 +0200] cupsdCloseClient: 1023
I [05/Jun/2007:09:29:30 +0200] Scheduler shutting down normally.
I [05/Jun/2007:09:29:30 +0200] Saving remote.cache...
I [05/Jun/2007:09:29:30 +0200] Saving job cache file "/var/cache/cups/job.cache"...

```

The first 4 lines show up the last successfull printing job. 
The next time trying to print fails. After restarting cupsys (last lines) everything works fine again...

Any suggestions?

Thanks a lot

Flane

---

