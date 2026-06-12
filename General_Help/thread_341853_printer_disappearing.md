---
title: "printer disappearing"
date: 2007-01-19
forum: General Help
---

### Post by braincat on 2007-01-19
I have an edgy system with all updates applied, an HP Laserjet 1020 usb
printer that used to print.   After installing the system for the first time,
I have successfully added the printer, and it worked for a while until
one day I restarted the machine with the printer off.   After that, no
matter what I do, the printer doesn't print, and all jobs disappear into
a thin air.
I tried
* deleting and creating the printer again
* reinstalling cups
* enabled a "warning" loglevel in /etc/cupsd/cupsd.conf, and looked at 
/var/log/cups/error_log.  The log looks normal, as if cups did all the job
correctly.  I had exactly the same problem in dapper, and resigned to
running without a printer, until I installed edgy.
Thanks.

D [19/Jan/2007:07:52:12 -0600] [Job 20] Parameter Summary
D [19/Jan/2007:07:52:12 -0600] [Job 20] -----------------
D [19/Jan/2007:07:52:12 -0600] [Job 20] 
D [19/Jan/2007:07:52:12 -0600] [Job 20] Spooler: cups
D [19/Jan/2007:07:52:12 -0600] [Job 20] Printer: hp
D [19/Jan/2007:07:52:12 -0600] [Job 20] Shell: /bin/bash
D [19/Jan/2007:07:52:12 -0600] [Job 20] PPD file: /etc/cups/ppd/hp.ppd
D [19/Jan/2007:07:52:12 -0600] [Job 20] ATTR file: 
D [19/Jan/2007:07:52:12 -0600] [Job 20] Printer model: HP LaserJet 1020 Foomatic/foo2zjs (recommended)
D [19/Jan/2007:07:52:12 -0600] [Job 20] Job title: stdin
D [19/Jan/2007:07:52:12 -0600] [Job 20] File(s) to be printed: 
D [19/Jan/2007:07:52:12 -0600] [Job 20] <STDIN> 
D [19/Jan/2007:07:52:12 -0600] [Job 20] 
D [19/Jan/2007:07:52:12 -0600] [Job 20] GhostScript extra search path ('GS_LIB'): /usr/share/cups/fonts
D [19/Jan/2007:07:52:12 -0600] [Job 20] Pondering option 'job-uuid=urn:uuid:5fafd2d5-97aa-32eb-71e8-8570b2364ad0'
D [19/Jan/2007:07:52:12 -0600] [Job 20] Unknown option job-uuid=urn:uuid:5fafd2d5-97aa-32eb-71e8-8570b2364ad0.
D [19/Jan/2007:07:52:12 -0600] [Job 20] 
D [19/Jan/2007:07:52:12 -0600] [Job 20] ================================================
D [19/Jan/2007:07:52:12 -0600] [Job 20] 
D [19/Jan/2007:07:52:12 -0600] [Job 20] File: <STDIN>
D [19/Jan/2007:07:52:12 -0600] [Job 20] 
D [19/Jan/2007:07:52:12 -0600] [Job 20] ================================================
D [19/Jan/2007:07:52:12 -0600] [Job 20] 
D [19/Jan/2007:07:52:12 -0600] [Job 20] Reading PostScript input ...
D [19/Jan/2007:07:52:12 -0600] [Job 20] --> This document is DSC-conforming!
D [19/Jan/2007:07:52:12 -0600] [Job 20] 
D [19/Jan/2007:07:52:12 -0600] [Job 20] -----------
D [19/Jan/2007:07:52:12 -0600] [Job 20] Found: %%BeginProlog 
D [19/Jan/2007:07:52:12 -0600] PID 6420 (/usr/lib/cups/filter/texttops) exited with no errors.
D [19/Jan/2007:07:52:12 -0600] [Job 20] Before copy_setup - %%Page: 1 1
D [19/Jan/2007:07:52:12 -0600] [Job 20] Before page loop - %%Page: 1 1
D [19/Jan/2007:07:52:12 -0600] [Job 20] Copying page 1...
D [19/Jan/2007:07:52:12 -0600] [Job 20] pagew = 589.3, pagel = 769.3
D [19/Jan/2007:07:52:12 -0600] [Job 20] bboxw = 612, bboxl = 792
D [19/Jan/2007:07:52:12 -0600] [Job 20] PageLeft = 11.3, PageRight = 600.7
D [19/Jan/2007:07:52:12 -0600] [Job 20] PageTop = 780.7, PageBottom = 11.3
D [19/Jan/2007:07:52:12 -0600] [Job 20] PageWidth = 612.0, PageLength = 792.0
D [19/Jan/2007:07:52:12 -0600] [Job 20] Wrote 1 pages...
D [19/Jan/2007:07:52:12 -0600] PID 6421 (/usr/lib/cups/filter/pstops) exited with no errors.
D [19/Jan/2007:07:52:12 -0600] [Job 20] Found: %%EndProlog
D [19/Jan/2007:07:52:12 -0600] [Job 20]
D [19/Jan/2007:07:52:12 -0600] [Job 20] -----------
D [19/Jan/2007:07:52:12 -0600] [Job 20] Found: %%BeginSetup
D [19/Jan/2007:07:52:12 -0600] [Job 20] Found: %%BeginFeature: *Quality normal
D [19/Jan/2007:07:52:12 -0600] [Job 20] Option: Quality=normal --> Setting option
D [19/Jan/2007:07:52:12 -0600] [Job 20] Found: %% FoomaticRIPOptionSetting: Quality=normal
D [19/Jan/2007:07:52:12 -0600] [Job 20] Option: Quality=normal --> Setting option
D [19/Jan/2007:07:52:12 -0600] [Job 20] Found: %%BeginFeature: *Resolution 1200x600dpi
D [19/Jan/2007:07:52:12 -0600] [Job 20] Option: Resolution=1200x600dpi --> Setting option
D [19/Jan/2007:07:52:12 -0600] [Job 20] Found: %% FoomaticRIPOptionSetting: Resolution=1200x600dpi
D [19/Jan/2007:07:52:12 -0600] [Job 20] Option: Resolution=1200x600dpi --> Setting option
D [19/Jan/2007:07:52:12 -0600] [Job 20] Found: %%BeginFeature: *PageRegion Letter
D [19/Jan/2007:07:52:12 -0600] [Job 20] Option: PageRegion=Letter --> Option will be set by PostScript interpreter
D [19/Jan/2007:07:52:12 -0600] [Job 20] Found: %% FoomaticRIPOptionSetting: PageSize=Letter
D [19/Jan/2007:07:52:12 -0600] [Job 20] Option: PageSize=Letter --> Setting option
D [19/Jan/2007:07:52:12 -0600] [Job 20] Found: %%BeginFeature: *InputSlot Auto
D [19/Jan/2007:07:52:12 -0600] [Job 20] Option: InputSlot=Auto --> Setting option
D [19/Jan/2007:07:52:12 -0600] [Job 20] Found: %% FoomaticRIPOptionSetting: InputSlot=Auto
D [19/Jan/2007:07:52:12 -0600] [Job 20] Option: InputSlot=Auto --> Setting option
D [19/Jan/2007:07:52:12 -0600] [Job 20] Found: %%BeginFeature: *MediaType Standard
D [19/Jan/2007:07:52:12 -0600] [Job 20] Option: MediaType=Standard --> Setting option
D [19/Jan/2007:07:52:12 -0600] [Job 20] Found: %% FoomaticRIPOptionSetting: MediaType=Standard
D [19/Jan/2007:07:52:12 -0600] [Job 20] Option: MediaType=Standard --> Setting option
D [19/Jan/2007:07:52:12 -0600] [Job 20] Found: %%BeginFeature: *Nup 1up
D [19/Jan/2007:07:52:12 -0600] [Job 20] Option: Nup=1up --> Setting option
D [19/Jan/2007:07:52:12 -0600] [Job 20] Found: %% FoomaticRIPOptionSetting: Nup=1up
D [19/Jan/2007:07:52:12 -0600] [Job 20] Option: Nup=1up --> Setting option
D [19/Jan/2007:07:52:12 -0600] [Job 20] Found: %%BeginFeature: *NupOrient port
D [19/Jan/2007:07:52:12 -0600] [Job 20] Option: NupOrient=port --> Setting option
D [19/Jan/2007:07:52:12 -0600] [Job 20] Found: %% FoomaticRIPOptionSetting: NupOrient=port
D [19/Jan/2007:07:52:12 -0600] [Job 20] Option: NupOrient=port --> Setting option
D [19/Jan/2007:07:52:12 -0600] [Job 20] Found: %%BeginFeature: *Copies 1
D [19/Jan/2007:07:52:12 -0600] [Job 20] Option: Copies=1 --> Setting option
D [19/Jan/2007:07:52:12 -0600] [Job 20] Found: %% FoomaticRIPOptionSetting: Copies=1
D [19/Jan/2007:07:52:12 -0600] [Job 20] Option: Copies=1 --> Setting option
D [19/Jan/2007:07:52:12 -0600] [Job 20] Found: %%EndSetup
D [19/Jan/2007:07:52:12 -0600] [Job 20] Inserting PostScript code for CUPS' page accounting
D [19/Jan/2007:07:52:12 -0600] [Job 20]
D [19/Jan/2007:07:52:12 -0600] [Job 20] -----------
D [19/Jan/2007:07:52:12 -0600] [Job 20] New page:  1 1
D [19/Jan/2007:07:52:12 -0600] [Job 20] Inserting option code into "PageSetup" section.
D [19/Jan/2007:07:52:12 -0600] [Job 20]
D [19/Jan/2007:07:52:12 -0600] [Job 20] Found: %%BeginPageSetup
D [19/Jan/2007:07:52:12 -0600] [Job 20] Found: %%EndPageSetup
D [19/Jan/2007:07:52:12 -0600] [Job 20] End of page header
D [19/Jan/2007:07:52:12 -0600] [Job 20] Flushing FIFO.
D [19/Jan/2007:07:52:12 -0600] [Job 20]
D [19/Jan/2007:07:52:12 -0600] [Job 20] Starting renderer
D [19/Jan/2007:07:52:12 -0600] [Job 20] JCL: <job data>
D [19/Jan/2007:07:52:12 -0600] [Job 20]
D [19/Jan/2007:07:52:12 -0600] [Job 20] renderer PID kid4=6432
D [19/Jan/2007:07:52:12 -0600] [Job 20] renderer command: foo2zjs-wrapper   -P -z1 -L0  -r1200x600 -p1 -s7 -m1   -n1
D [19/Jan/2007:07:52:12 -0600] [Job 20]
D [19/Jan/2007:07:52:12 -0600] [Job 20] Closing renderer
D [19/Jan/2007:07:52:12 -0600] [Job 20] tail process done writing data to STDOUT
D [19/Jan/2007:07:52:12 -0600] [Job 20] KID4 finished
D [19/Jan/2007:07:52:12 -0600] [Job 20] KID3 exited with status 0
D [19/Jan/2007:07:52:12 -0600] [Job 20] KID4 exited with status 0
D [19/Jan/2007:07:52:12 -0600] [Job 20] Renderer exit stat: 0
D [19/Jan/2007:07:52:12 -0600] [Job 20] KID3 finished
D [19/Jan/2007:07:52:12 -0600] [Job 20] Renderer process finished
D [19/Jan/2007:07:52:12 -0600] [Job 20]
D [19/Jan/2007:07:52:12 -0600] [Job 20] Closing foomatic-rip.
D [19/Jan/2007:07:52:12 -0600] PID 6422 (/usr/lib/cups/filter/foomatic-rip) exited with no errors.
D [19/Jan/2007:07:52:54 -0600] cupsdAcceptClient: 6 from localhost (Domain)
D [19/Jan/2007:07:52:54 -0600] cupsdCloseClient: 8
D [19/Jan/2007:07:52:54 -0600] PID 6423 (/usr/lib/cups/backend/hp) exited with no errors.
D [19/Jan/2007:07:52:54 -0600] [Job 20] File 0 is complete.
D [19/Jan/2007:07:52:54 -0600] Discarding unused printer-state-changed event...

---

### Post by scrooge_74 on 2007-01-19
I had a similar problem, if I remember well I deleted every reference to the printer in all the files on /etc/cups, restarted cups and install the printer again

Then it seems to come back and is working again

---

### Post by braincat on 2007-01-19
Thanks for the hint.  I did that, then restarted into Windows
(I am dual-booting), printed a test page, restarted into linux
again, and the printer started working!  Not sure which
one of the two steps fixed the problem (maybe both?)

---

### Post by scrooge_74 on 2007-01-20
Is like magic don't you think? I recommend you read the info on Cupsys so you have a better understanding on how the magic works

[http://www.cups.org/doc-1.1/sam.html](http://www.cups.org/doc-1.1/sam.html)
[http://www.linuxprinting.org/](http://www.linuxprinting.org/)

---

