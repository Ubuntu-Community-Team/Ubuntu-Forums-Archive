---
title: "Printer Not Working"
date: 2007-11-02
forum: General Help
---

### Post by BenHill on 2007-11-02
Greetings, all.

I am having some problems printing to my Lexmark X7170.  Ubuntu discovered it when I installed (I also tried to install it from scratch).

I set the error logging to verbose, and here is the output when printing a test page.  Any help would be most appreciated!

Ben

___



D [02/Nov/2007:06:22:42 +0000] cupsdAcceptClient: 10 from localhost (Domain)
D [02/Nov/2007:06:22:42 +0000] cupsdReadClient: 10 POST / HTTP/1.1
D [02/Nov/2007:06:22:42 +0000] cupsdAuthorize: No authentication data provided.
D [02/Nov/2007:06:22:42 +0000] CUPS-Get-Printers
D [02/Nov/2007:06:22:42 +0000] cupsdProcessIPPRequest: 10 status_code=0 (successful-ok)
D [02/Nov/2007:06:22:42 +0000] cupsdCloseClient: 10
D [02/Nov/2007:06:22:42 +0000] cupsdAcceptClient: 10 from localhost (Domain)
D [02/Nov/2007:06:22:42 +0000] cupsdReadClient: 10 POST / HTTP/1.1
D [02/Nov/2007:06:22:42 +0000] cupsdAuthorize: No authentication data provided.
D [02/Nov/2007:06:22:42 +0000] Get-Jobs ipp://localhost/jobs/
D [02/Nov/2007:06:22:42 +0000] cupsdProcessIPPRequest: 10 status_code=0 (successful-ok)
D [02/Nov/2007:06:22:42 +0000] cupsdReadClient: 10 POST / HTTP/1.1
D [02/Nov/2007:06:22:42 +0000] cupsdAuthorize: No authentication data provided.
D [02/Nov/2007:06:22:42 +0000] CUPS-Get-Printers
D [02/Nov/2007:06:22:42 +0000] cupsdProcessIPPRequest: 10 status_code=0 (successful-ok)
D [02/Nov/2007:06:22:42 +0000] cupsdCloseClient: 10
D [02/Nov/2007:06:23:03 +0000] cupsdAcceptClient: 10 from localhost (Domain)
D [02/Nov/2007:06:23:04 +0000] cupsdReadClient: 10 POST / HTTP/1.1
D [02/Nov/2007:06:23:04 +0000] cupsdAuthorize: No authentication data provided.
D [02/Nov/2007:06:23:04 +0000] CUPS-Get-Printers
D [02/Nov/2007:06:23:04 +0000] cupsdProcessIPPRequest: 10 status_code=0 (successful-ok)
D [02/Nov/2007:06:23:04 +0000] cupsdReadClient: 10 POST / HTTP/1.1
D [02/Nov/2007:06:23:04 +0000] cupsdAuthorize: No authentication data provided.
D [02/Nov/2007:06:23:04 +0000] CUPS-Get-Classes
D [02/Nov/2007:06:23:04 +0000] cupsdProcessIPPRequest: 10 status_code=0 (successful-ok)
D [02/Nov/2007:06:23:04 +0000] cupsdReadClient: 10 POST / HTTP/1.1
D [02/Nov/2007:06:23:04 +0000] cupsdAuthorize: No authentication data provided.
D [02/Nov/2007:06:23:04 +0000] Get-Printer-Attributes ipp://localhost/printers/_7100_Series
D [02/Nov/2007:06:23:04 +0000] cupsdProcessIPPRequest: 10 status_code=0 (successful-ok)
D [02/Nov/2007:06:23:04 +0000] cupsdReadClient: 10 POST / HTTP/1.1
D [02/Nov/2007:06:23:04 +0000] cupsdAuthorize: No authentication data provided.
D [02/Nov/2007:06:23:04 +0000] Get-Printer-Attributes ipp://localhost/printers/_7100_Series
D [02/Nov/2007:06:23:04 +0000] cupsdProcessIPPRequest: 10 status_code=0 (successful-ok)
D [02/Nov/2007:06:23:04 +0000] cupsdReadClient: 10 GET /printers/_7100_Series.ppd HTTP/1.1
D [02/Nov/2007:06:23:04 +0000] cupsdAuthorize: No authentication data provided.
D [02/Nov/2007:06:23:04 +0000] cupsdReadClient: 10 POST / HTTP/1.1
D [02/Nov/2007:06:23:04 +0000] cupsdAuthorize: No authentication data provided.
D [02/Nov/2007:06:23:04 +0000] Get-Jobs ipp://localhost/jobs/
D [02/Nov/2007:06:23:04 +0000] cupsdProcessIPPRequest: 10 status_code=0 (successful-ok)
D [02/Nov/2007:06:23:05 +0000] cupsdReadClient: 10 POST / HTTP/1.1
D [02/Nov/2007:06:23:05 +0000] cupsdAuthorize: No authentication data provided.
D [02/Nov/2007:06:23:05 +0000] Get-Jobs ipp://localhost/jobs/
D [02/Nov/2007:06:23:05 +0000] cupsdProcessIPPRequest: 10 status_code=0 (successful-ok)
D [02/Nov/2007:06:23:05 +0000] cupsdReadClient: 10 POST /jobs/ HTTP/1.1
D [02/Nov/2007:06:23:05 +0000] cupsdAuthorize: No authentication data provided.
D [02/Nov/2007:06:23:05 +0000] Cancel-Job ipp://localhost/jobs/15
D [02/Nov/2007:06:23:05 +0000] cupsdIsAuthorized: requesting-user-name="benhill"
D [02/Nov/2007:06:23:05 +0000] Discarding unused printer-state-changed event...
D [02/Nov/2007:06:23:05 +0000] Discarding unused job-completed event...
I [02/Nov/2007:06:23:05 +0000] [Job 15] Canceled by "benhill".
D [02/Nov/2007:06:23:05 +0000] cupsdProcessIPPRequest: 10 status_code=0 (successful-ok)
D [02/Nov/2007:06:23:05 +0000] cupsdAcceptClient: 11 from localhost (Domain)
D [02/Nov/2007:06:23:05 +0000] PID 10633 (/usr/lib/cups/backend/usb) exited with no errors.
D [02/Nov/2007:06:23:05 +0000] cupsdReadClient: 11 POST / HTTP/1.1
D [02/Nov/2007:06:23:05 +0000] cupsdAuthorize: No authentication data provided.
D [02/Nov/2007:06:23:05 +0000] Get-Jobs ipp://localhost/jobs/
D [02/Nov/2007:06:23:05 +0000] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [02/Nov/2007:06:23:05 +0000] cupsdReadClient: 11 POST / HTTP/1.1
D [02/Nov/2007:06:23:05 +0000] cupsdAuthorize: No authentication data provided.
D [02/Nov/2007:06:23:05 +0000] CUPS-Get-Printers
D [02/Nov/2007:06:23:05 +0000] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [02/Nov/2007:06:23:05 +0000] cupsdReadClient: 10 POST / HTTP/1.1
D [02/Nov/2007:06:23:05 +0000] cupsdAuthorize: No authentication data provided.
D [02/Nov/2007:06:23:05 +0000] Get-Jobs ipp://localhost/jobs/
D [02/Nov/2007:06:23:05 +0000] cupsdProcessIPPRequest: 10 status_code=0 (successful-ok)
D [02/Nov/2007:06:23:05 +0000] cupsdCloseClient: 11
D [02/Nov/2007:06:23:05 +0000] PID 10632 (/usr/lib/cups/filter/foomatic-rip) exited with no errors.
D [02/Nov/2007:06:23:06 +0000] cupsdReadClient: 10 POST /printers/_7100_Series HTTP/1.1
D [02/Nov/2007:06:23:06 +0000] cupsdAuthorize: No authentication data provided.
D [02/Nov/2007:06:23:06 +0000] Print-Job ipp://localhost/printers/_7100_Series
D [02/Nov/2007:06:23:06 +0000] add_job: requesting-user-name="guest"
D [02/Nov/2007:06:23:06 +0000] Adding default job-sheets values "none,none"...
I [02/Nov/2007:06:23:06 +0000] [Job 17] Adding start banner page "none".
D [02/Nov/2007:06:23:06 +0000] Discarding unused job-created event...
I [02/Nov/2007:06:23:06 +0000] [Job 17] Adding job file of type application/postscript.
I [02/Nov/2007:06:23:06 +0000] [Job 17] Adding end banner page "none".
I [02/Nov/2007:06:23:06 +0000] [Job 17] Queued on "_7100_Series" by "guest".
D [02/Nov/2007:06:23:06 +0000] [Job 17] hold_until = 0
D [02/Nov/2007:06:23:06 +0000] Discarding unused printer-state-changed event...
D [02/Nov/2007:06:23:06 +0000] [Job 17] job-sheets=none,none
D [02/Nov/2007:06:23:06 +0000] [Job 17] banner_page = 0
D [02/Nov/2007:06:23:06 +0000] [Job 17] argv[0]="_7100_Series"
D [02/Nov/2007:06:23:06 +0000] [Job 17] argv[1]="17"
D [02/Nov/2007:06:23:06 +0000] [Job 17] argv[2]="guest"
D [02/Nov/2007:06:23:06 +0000] [Job 17] argv[3]="Test Page"
D [02/Nov/2007:06:23:06 +0000] [Job 17] argv[4]="1"
D [02/Nov/2007:06:23:06 +0000] [Job 17] argv[5]="job-uuid=urn:uuid:3306a12e-dccd-3d2b-74c3-e63885ad1f18 lpi=5.700000"
D [02/Nov/2007:06:23:06 +0000] [Job 17] argv[6]="/var/spool/cups/d00017-001"
D [02/Nov/2007:06:23:06 +0000] [Job 17] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [02/Nov/2007:06:23:06 +0000] [Job 17] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [02/Nov/2007:06:23:06 +0000] [Job 17] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [02/Nov/2007:06:23:06 +0000] [Job 17] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [02/Nov/2007:06:23:06 +0000] [Job 17] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [02/Nov/2007:06:23:06 +0000] [Job 17] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [02/Nov/2007:06:23:06 +0000] [Job 17] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [02/Nov/2007:06:23:06 +0000] [Job 17] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [02/Nov/2007:06:23:06 +0000] [Job 17] envp[8]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [02/Nov/2007:06:23:06 +0000] [Job 17] envp[9]="SERVER_ADMIN=root@elrond"
D [02/Nov/2007:06:23:06 +0000] [Job 17] envp[10]="SOFTWARE=CUPS/1.3.2"
D [02/Nov/2007:06:23:06 +0000] [Job 17] envp[11]="TMPDIR=/var/spool/cups/tmp"
D [02/Nov/2007:06:23:06 +0000] [Job 17] envp[12]="TZ=User defined"
D [02/Nov/2007:06:23:06 +0000] [Job 17] envp[13]="USER=root"
D [02/Nov/2007:06:23:06 +0000] [Job 17] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [02/Nov/2007:06:23:06 +0000] [Job 17] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [02/Nov/2007:06:23:06 +0000] [Job 17] envp[16]="IPP_PORT=631"
D [02/Nov/2007:06:23:06 +0000] [Job 17] envp[17]="CHARSET=utf-8"
D [02/Nov/2007:06:23:06 +0000] [Job 17] envp[18]="LANG=en_US"
D [02/Nov/2007:06:23:06 +0000] [Job 17] envp[19]="PPD=/etc/cups/ppd/_7100_Series.ppd"
D [02/Nov/2007:06:23:06 +0000] [Job 17] envp[20]="RIP_MAX_CACHE=8m"
D [02/Nov/2007:06:23:06 +0000] [Job 17] envp[21]="CONTENT_TYPE=application/postscript"
D [02/Nov/2007:06:23:06 +0000] [Job 17] envp[22]="DEVICE_URI=usb://Lexmark/7100%20Series"
D [02/Nov/2007:06:23:06 +0000] [Job 17] envp[23]="PRINTER=_7100_Series"
D [02/Nov/2007:06:23:06 +0000] [Job 17] envp[24]="FINAL_CONTENT_TYPE=printer/_7100_Series"
I [02/Nov/2007:06:23:06 +0000] [Job 17] Started filter /usr/lib/cups/filter/pstops (PID 10678)
I [02/Nov/2007:06:23:06 +0000] [Job 17] Started filter /usr/lib/cups/filter/foomatic-rip (PID 10679)
I [02/Nov/2007:06:23:06 +0000] [Job 17] Started backend /usr/lib/cups/backend/usb (PID 10680)
D [02/Nov/2007:06:23:06 +0000] Discarding unused job-state event...
D [02/Nov/2007:06:23:06 +0000] cupsdProcessIPPRequest: 10 status_code=0 (successful-ok)
D [02/Nov/2007:06:23:06 +0000] [Job 17] Page = 612x792; 18,36 to 594,756
D [02/Nov/2007:06:23:06 +0000] [Job 17] slow_collate=0, slow_duplex=0, slow_order=0
D [02/Nov/2007:06:23:06 +0000] [Job 17] Before copy_comments - %!PS-Adobe-3.0
D [02/Nov/2007:06:23:06 +0000] [Job 17] %!PS-Adobe-3.0
D [02/Nov/2007:06:23:06 +0000] [Job 17] %%Title: PPR Test Page
D [02/Nov/2007:06:23:06 +0000] [Job 17] %%Pages: 1
D [02/Nov/2007:06:23:06 +0000] [Job 17] %%DocumentNeededResources: font Helvetica
D [02/Nov/2007:06:23:06 +0000] [Job 17] %%EndComments
E [02/Nov/2007:06:23:06 +0000] [Job 17] No %%BoundingBox: comment in header!
D [02/Nov/2007:06:23:06 +0000] [Job 17] Before copy_prolog - %%BeginProlog
D [02/Nov/2007:06:23:06 +0000] [Job 17] Before copy_setup - %%BeginSetup
D [02/Nov/2007:06:23:06 +0000] [Job 17] Before page loop - %%Page: 1 1
D [02/Nov/2007:06:23:06 +0000] [Job 17] Copying page 1...
D [02/Nov/2007:06:23:06 +0000] [Job 17] pagew = 576.0, pagel = 720.0
D [02/Nov/2007:06:23:06 +0000] [Job 17] bboxw = 612, bboxl = 792
D [02/Nov/2007:06:23:06 +0000] [Job 17] PageLeft = 18.0, PageRight = 594.0
D [02/Nov/2007:06:23:06 +0000] [Job 17] PageTop = 756.0, PageBottom = 36.0
D [02/Nov/2007:06:23:06 +0000] [Job 17] PageWidth = 612.0, PageLength = 792.0
D [02/Nov/2007:06:23:06 +0000] [Job 17] perl: warning: Setting locale failed.
D [02/Nov/2007:06:23:06 +0000] [Job 17] perl: warning: Please check that your locale settings:
D [02/Nov/2007:06:23:06 +0000] [Job 17] LANGUAGE = (unset),
D [02/Nov/2007:06:23:06 +0000] [Job 17] LC_ALL = (unset),
D [02/Nov/2007:06:23:06 +0000] [Job 17] LANG = "en_US"
D [02/Nov/2007:06:23:06 +0000] [Job 17] are supported and installed on your system.
D [02/Nov/2007:06:23:06 +0000] [Job 17] perl: warning: Falling back to the standard locale ("C").
D [02/Nov/2007:06:23:06 +0000] Discarding unused printer-state-changed event...
D [02/Nov/2007:06:23:06 +0000] cupsdReadClient: 10 POST / HTTP/1.1
D [02/Nov/2007:06:23:06 +0000] cupsdAuthorize: No authentication data provided.
D [02/Nov/2007:06:23:06 +0000] Get-Jobs ipp://localhost/jobs/
D [02/Nov/2007:06:23:06 +0000] cupsdProcessIPPRequest: 10 status_code=0 (successful-ok)
D [02/Nov/2007:06:23:07 +0000] [Job 17] foomatic-rip version $Revision$ running...
D [02/Nov/2007:06:23:07 +0000] [Job 17] Parsing PPD file ...
D [02/Nov/2007:06:23:07 +0000] [Job 17] *cupsFilter: "application/vnd.cups-postscript 0 foomatic-rip"
D [02/Nov/2007:06:23:07 +0000] [Job 17] Added option ColorSpace
D [02/Nov/2007:06:23:07 +0000] [Job 17] Added option PageSize
D [02/Nov/2007:06:23:07 +0000] [Job 17] Added option PageRegion
D [02/Nov/2007:06:23:07 +0000] [Job 17] Added option ImageableArea
D [02/Nov/2007:06:23:07 +0000] [Job 17] Added option PaperDimension
D [02/Nov/2007:06:23:07 +0000] [Job 17] Added option Resolution
D [02/Nov/2007:06:23:07 +0000] [Job 17] Added option Font
D [02/Nov/2007:06:23:07 +0000] [Job 17] 
D [02/Nov/2007:06:23:07 +0000] [Job 17] Parameter Summary
D [02/Nov/2007:06:23:07 +0000] [Job 17] -----------------
D [02/Nov/2007:06:23:07 +0000] [Job 17] 
D [02/Nov/2007:06:23:07 +0000] [Job 17] Spooler: cups
D [02/Nov/2007:06:23:07 +0000] [Job 17] Printer: _7100_Series
D [02/Nov/2007:06:23:07 +0000] [Job 17] Shell: /bin/bash
D [02/Nov/2007:06:23:07 +0000] [Job 17] PPD file: /etc/cups/ppd/_7100_Series.ppd
D [02/Nov/2007:06:23:07 +0000] [Job 17] ATTR file: 
D [02/Nov/2007:06:23:07 +0000] [Job 17] Printer model: Lexmark 7000 Foomatic/lex7000 (recommended)
D [02/Nov/2007:06:23:07 +0000] [Job 17] Job title: Test Page
D [02/Nov/2007:06:23:07 +0000] [Job 17] File(s) to be printed: 
D [02/Nov/2007:06:23:07 +0000] [Job 17] <STDIN>
D [02/Nov/2007:06:23:07 +0000] [Job 17] 
D [02/Nov/2007:06:23:07 +0000] [Job 17] GhostScript extra search path ('GS_LIB'): /usr/share/cups/fonts
D [02/Nov/2007:06:23:07 +0000] [Job 17] Pondering option 'job-uuid=urn:uuid:3306a12e-dccd-3d2b-74c3-e63885ad1f18'
D [02/Nov/2007:06:23:07 +0000] [Job 17] Unknown option job-uuid=urn:uuid:3306a12e-dccd-3d2b-74c3-e63885ad1f18.
D [02/Nov/2007:06:23:07 +0000] [Job 17] Pondering option 'lpi=5.700000'
D [02/Nov/2007:06:23:07 +0000] [Job 17] Unknown option lpi=5.700000.
D [02/Nov/2007:06:23:07 +0000] [Job 17] 
D [02/Nov/2007:06:23:07 +0000] [Job 17] ================================================
D [02/Nov/2007:06:23:07 +0000] [Job 17] 
D [02/Nov/2007:06:23:07 +0000] [Job 17] File: <STDIN>
D [02/Nov/2007:06:23:07 +0000] [Job 17] 
D [02/Nov/2007:06:23:07 +0000] [Job 17] ================================================
D [02/Nov/2007:06:23:07 +0000] [Job 17] 
D [02/Nov/2007:06:23:07 +0000] [Job 17] Reading PostScript input ...
D [02/Nov/2007:06:23:07 +0000] [Job 17] --> This document is DSC-conforming!
D [02/Nov/2007:06:23:07 +0000] [Job 17] 
D [02/Nov/2007:06:23:07 +0000] [Job 17] -----------
D [02/Nov/2007:06:23:07 +0000] [Job 17] Found: %%BeginProlog
D [02/Nov/2007:06:23:07 +0000] [Job 17] Found: %%EndProlog
D [02/Nov/2007:06:23:07 +0000] [Job 17] 
D [02/Nov/2007:06:23:07 +0000] [Job 17] -----------
D [02/Nov/2007:06:23:07 +0000] [Job 17] Found: %%BeginSetup
D [02/Nov/2007:06:23:07 +0000] [Job 17] Found: %%BeginFeature: *PageSize Letter
D [02/Nov/2007:06:23:07 +0000] [Job 17] Option: PageSize=Letter --> Option will be set by PostScript interpreter
D [02/Nov/2007:06:23:07 +0000] [Job 17] Found: %%BeginFeature: *Resolution 600x600dpi
D [02/Nov/2007:06:23:07 +0000] [Job 17] Option: Resolution=600x600dpi --> Setting option
D [02/Nov/2007:06:23:07 +0000] [Job 17] Found: %% FoomaticRIPOptionSetting: Resolution=600x600dpi
D [02/Nov/2007:06:23:07 +0000] [Job 17] Option: Resolution=600x600dpi --> Setting option
D [02/Nov/2007:06:23:07 +0000] [Job 17] Found: %%EndSetup
D [02/Nov/2007:06:23:07 +0000] [Job 17] Inserting PostScript code for CUPS' page accounting
D [02/Nov/2007:06:23:07 +0000] [Job 17] 
D [02/Nov/2007:06:23:07 +0000] [Job 17] -----------
D [02/Nov/2007:06:23:07 +0000] [Job 17] New page:  1 1
D [02/Nov/2007:06:23:07 +0000] [Job 17] Inserting option code into "PageSetup" section.
D [02/Nov/2007:06:23:07 +0000] [Job 17] 
D [02/Nov/2007:06:23:07 +0000] [Job 17] Found: %%BeginPageSetup
D [02/Nov/2007:06:23:07 +0000] [Job 17] Found: %%EndPageSetup
D [02/Nov/2007:06:23:07 +0000] [Job 17] End of page header
D [02/Nov/2007:06:23:07 +0000] [Job 17] Embedded document, nesting level now: 1
D [02/Nov/2007:06:23:07 +0000] [Job 17] Stopping search for page header options
D [02/Nov/2007:06:23:07 +0000] [Job 17] Found: 
D [02/Nov/2007:06:23:07 +0000] [Job 17] --> Output goes directly to the renderer now.
D [02/Nov/2007:06:23:07 +0000] [Job 17] 
D [02/Nov/2007:06:23:07 +0000] [Job 17] 
D [02/Nov/2007:06:23:07 +0000] [Job 17] Starting renderer
D [02/Nov/2007:06:23:07 +0000] [Job 17] JCL: <job data> 
D [02/Nov/2007:06:23:07 +0000] [Job 17] 
D [02/Nov/2007:06:23:07 +0000] [Job 17] renderer PID kid4=10688
D [02/Nov/2007:06:23:07 +0000] [Job 17] renderer command: gs -q -dBATCH -dPARANOIDSAFER -dQUIET -dNOPAUSE -sDEVICE=lex7000  -r600x600 -sOutputFile=- -
D [02/Nov/2007:06:23:07 +0000] [Job 17] perl: warning: Setting locale failed.
D [02/Nov/2007:06:23:07 +0000] [Job 17] perl: warning: Please check that your locale settings:
D [02/Nov/2007:06:23:07 +0000] [Job 17] LANGUAGE = (unset),
D [02/Nov/2007:06:23:07 +0000] [Job 17] LC_ALL = (unset),
D [02/Nov/2007:06:23:07 +0000] [Job 17] LANG = "en_US"
D [02/Nov/2007:06:23:07 +0000] [Job 17] are supported and installed on your system.
D [02/Nov/2007:06:23:07 +0000] [Job 17] perl: warning: Falling back to the standard locale ("C").
D [02/Nov/2007:06:23:07 +0000] [Job 17] foomatic-gswrapper: gs '-sstdout=%stderr' '-dBATCH' '-dPARANOIDSAFER' '-dQUIET' '-dNOPAUSE' '-sDEVICE=lex7000' '-r600x600' '-sOutputFile=%stdout' '-'
D [02/Nov/2007:06:23:07 +0000] cupsdAcceptClient: 11 from localhost (Domain)
D [02/Nov/2007:06:23:07 +0000] cupsdReadClient: 11 POST / HTTP/1.1
D [02/Nov/2007:06:23:07 +0000] cupsdAuthorize: No authentication data provided.
D [02/Nov/2007:06:23:07 +0000] Get-Jobs ipp://localhost/jobs/
D [02/Nov/2007:06:23:07 +0000] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [02/Nov/2007:06:23:07 +0000] cupsdReadClient: 11 POST / HTTP/1.1
D [02/Nov/2007:06:23:07 +0000] cupsdAuthorize: No authentication data provided.
D [02/Nov/2007:06:23:07 +0000] CUPS-Get-Printers
D [02/Nov/2007:06:23:07 +0000] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [02/Nov/2007:06:23:07 +0000] cupsdCloseClient: 11
D [02/Nov/2007:06:23:08 +0000] [Job 17] Wrote 1 pages...
D [02/Nov/2007:06:23:08 +0000] PID 10678 (/usr/lib/cups/filter/pstops) exited with no errors.
D [02/Nov/2007:06:23:08 +0000] [Job 17] Found: %%EndFont
D [02/Nov/2007:06:23:08 +0000] [Job 17] --> Continue DSC parsing now.
D [02/Nov/2007:06:23:08 +0000] [Job 17] 
D [02/Nov/2007:06:23:08 +0000] [Job 17] Found: %%BeginResource: procset Altsys_header 4 0
D [02/Nov/2007:06:23:08 +0000] [Job 17] --> Continue DSC parsing now.
D [02/Nov/2007:06:23:08 +0000] [Job 17] 
D [02/Nov/2007:06:23:08 +0000] [Job 17] Found: %%EndResource
D [02/Nov/2007:06:23:08 +0000] [Job 17] --> Continue DSC parsing now.
D [02/Nov/2007:06:23:08 +0000] [Job 17] 
D [02/Nov/2007:06:23:08 +0000] [Job 17] Found: %%EndProlog
D [02/Nov/2007:06:23:08 +0000] [Job 17] --> Continue DSC parsing now.
D [02/Nov/2007:06:23:08 +0000] [Job 17] 
D [02/Nov/2007:06:23:08 +0000] [Job 17] Found: %%BeginSetup
D [02/Nov/2007:06:23:08 +0000] [Job 17] --> Continue DSC parsing now.
D [02/Nov/2007:06:23:08 +0000] [Job 17] 
D [02/Nov/2007:06:23:08 +0000] [Job 17] Found: %%IncludeResource: font Times-Roman
D [02/Nov/2007:06:23:08 +0000] [Job 17] --> Continue DSC parsing now.
D [02/Nov/2007:06:23:08 +0000] [Job 17] 
D [02/Nov/2007:06:23:08 +0000] [Job 17] Found: %%EndSetup
D [02/Nov/2007:06:23:08 +0000] [Job 17] --> Continue DSC parsing now.
D [02/Nov/2007:06:23:08 +0000] [Job 17] 
D [02/Nov/2007:06:23:08 +0000] [Job 17] Found: %%Trailer
D [02/Nov/2007:06:23:08 +0000] [Job 17] --> Continue DSC parsing now.
D [02/Nov/2007:06:23:08 +0000] [Job 17] 
D [02/Nov/2007:06:23:08 +0000] [Job 17] Found: %%EndDocument
D [02/Nov/2007:06:23:08 +0000] [Job 17] --> Continue DSC parsing now.
D [02/Nov/2007:06:23:08 +0000] [Job 17] 
D [02/Nov/2007:06:23:08 +0000] [Job 17] End of Embedded document, nesting level now: 0
D [02/Nov/2007:06:23:08 +0000] [Job 17] Found: %%Trailer
D [02/Nov/2007:06:23:08 +0000] [Job 17] --> Continue DSC parsing now.
D [02/Nov/2007:06:23:08 +0000] [Job 17] 
D [02/Nov/2007:06:23:08 +0000] [Job 17] Found: %%Pages: 1
D [02/Nov/2007:06:23:08 +0000] [Job 17] --> Continue DSC parsing now.
D [02/Nov/2007:06:23:08 +0000] [Job 17] 
D [02/Nov/2007:06:23:08 +0000] [Job 17] Found: %%BoundingBox: 18 36 594 756
D [02/Nov/2007:06:23:08 +0000] [Job 17] --> Continue DSC parsing now.
D [02/Nov/2007:06:23:08 +0000] [Job 17] 
D [02/Nov/2007:06:23:08 +0000] [Job 17] Found: %%EOF
D [02/Nov/2007:06:23:08 +0000] [Job 17] --> Continue DSC parsing now.
D [02/Nov/2007:06:23:08 +0000] [Job 17] 
D [02/Nov/2007:06:23:08 +0000] [Job 17] 
D [02/Nov/2007:06:23:08 +0000] [Job 17] Closing renderer
D [02/Nov/2007:06:23:08 +0000] Discarding unused job-progress event...

---

### Post by Maestro23 on 2007-11-02
Here's the entry for your printer at Open Printing.
[http://openprinting.org/show_printer.cgi?recnum=Lexmark-x7170](http://openprinting.org/show_printer.cgi?recnum=Lexmark-x7170)

Good luck.

---

