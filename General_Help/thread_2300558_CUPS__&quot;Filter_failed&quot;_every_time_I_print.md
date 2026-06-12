---
title: "CUPS : &quot;Filter failed&quot; every time I print only odd numbered pages"
date: 2015-10-26
forum: General Help
---

### Post by timothylegg on 2015-10-26
Hello,

This happened once before a while back.  I was without printing ability for nearly a week.  I don't remember how I fixed it.

I was given 15 PDF files by a publisher (instructor solutions manuals, to be specific, so I'm prohibited from posting online them to reproduce the condition)

I decide to be clever and double side the print job.  I forget that when I do this, I get a filter failed error and it knocks me offline until I tinker around to get it fixed.  I don't think I went so var as to clear the spool folder. I might have deleted and reinstalled the printer.

It works fine except for when I try to do a double sided print arrangement.  I print the even pages first just fine.  I printed one page as a test afterwards (just fine) but when I go to print the odds, it never happens because of this filter failed error.

These printed just fine.

GradSpace legg 218 [26/Oct/2015:14:20:38 -0400] total 34 - localhost tcu12_ism_10.pdf &#8212; ISMT12_C10_A - -
GradSpace legg 219 [26/Oct/2015:14:21:22 -0400] 1 1 - localhost tcu12_ism_10.pdf &#8212; ISMT12_C10_A - -

Job 220 is the one that failed.

Below lie the /var/log/cups/error_log.

```
E [26/Oct/2015:14:24:22 -0400] [Job 220] Job stopped due to filter errors; please consult the error_log file for details.
D [26/Oct/2015:14:24:22 -0400] [Job 220] The following messages were recorded from 14:24:22 to 14:24:22
D [26/Oct/2015:14:24:22 -0400] [Job 220] Adding start banner page "none".
D [26/Oct/2015:14:24:22 -0400] [Job 220] Adding end banner page "none".
D [26/Oct/2015:14:24:22 -0400] [Job 220] File of type application/pdf queued by "legg".
D [26/Oct/2015:14:24:22 -0400] [Job 220] hold_until=0
D [26/Oct/2015:14:24:22 -0400] [Job 220] Queued on "GradSpace" by "legg".
D [26/Oct/2015:14:24:22 -0400] [Job 220] time-at-processing=1445883862
D [26/Oct/2015:14:24:22 -0400] [Job 220] 3 filters for job:
D [26/Oct/2015:14:24:22 -0400] [Job 220] pdftopdf (application/pdf to application/vnd.cups-pdf, cost 66)
D [26/Oct/2015:14:24:22 -0400] [Job 220] gstoraster (application/vnd.cups-pdf to application/vnd.cups-raster, cost 99)
D [26/Oct/2015:14:24:22 -0400] [Job 220] hpcups (application/vnd.cups-raster to printer/GradSpace, cost 0)
D [26/Oct/2015:14:24:22 -0400] [Job 220] job-sheets=none,none
D [26/Oct/2015:14:24:22 -0400] [Job 220] argv[0]="GradSpace"
D [26/Oct/2015:14:24:22 -0400] [Job 220] argv[1]="220"
D [26/Oct/2015:14:24:22 -0400] [Job 220] argv[2]="legg"
D [26/Oct/2015:14:24:22 -0400] [Job 220] argv[3]="tcu12_ism_10.pdf &#8212; ISMT12_C10_A"
D [26/Oct/2015:14:24:22 -0400] [Job 220] argv[4]="1"
D [26/Oct/2015:14:24:22 -0400] [Job 220] argv[5]="InputSlot=Auto number-up=1 MediaType=Plain PageSize=Letter page-set=even OutputMode=Best Duplex=None job-uuid=urn:uuid:4b6d4485-24d8-3866-46fa-6bb4f8033e53 job-originating-host-name=localhost time-at-creation=1445883862 time-at-processing=1445883862"
D [26/Oct/2015:14:24:22 -0400] [Job 220] argv[6]="/var/spool/cups/d00220-001"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[8]="HOME=/var/spool/cups/tmp"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[10]="SERVER_ADMIN=root@Parallels"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[11]="SOFTWARE=CUPS/1.7.2"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[13]="USER=root"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[14]="CUPS_MAX_MESSAGE=2047"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[16]="CUPS_ENCRYPTION=IfRequested"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[17]="IPP_PORT=631"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[18]="CHARSET=utf-8"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[19]="LANG=en_US.UTF-8"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[20]="PPD=/etc/cups/ppd/GradSpace.ppd"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[21]="RIP_MAX_CACHE=128m"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[22]="CONTENT_TYPE=application/pdf"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[23]="DEVICE_URI=socket://xxx.xxx.121.25:9100"  //edited for online use on web
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[24]="PRINTER_INFO=Grad Student Space Printer"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[25]="PRINTER_LOCATION=Architecture 2nd Floor"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[26]="PRINTER=GradSpace"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[27]="PRINTER_STATE_REASONS=none"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[28]="CUPS_FILETYPE=document"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[29]="FINAL_CONTENT_TYPE=printer/GradSpace"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[30]="AUTH_I****"
D [26/Oct/2015:14:24:22 -0400] [Job 220] Started filter /usr/lib/cups/filter/pdftopdf (PID 3100)
D [26/Oct/2015:14:24:22 -0400] [Job 220] Started filter /usr/lib/cups/filter/gstoraster (PID 3101)
D [26/Oct/2015:14:24:22 -0400] [Job 220] Started filter /usr/lib/cups/filter/hpcups (PID 3102)
D [26/Oct/2015:14:24:22 -0400] [Job 220] Started backend /usr/lib/cups/backend/socket (PID 3103)
D [26/Oct/2015:14:24:22 -0400] [Job 220] PID 3100 (/usr/lib/cups/filter/pdftopdf) exited with no errors.
D [26/Oct/2015:14:24:22 -0400] [Job 220] STATE: +connecting-to-device
D [26/Oct/2015:14:24:22 -0400] [Job 220] Looking up "xx.xxx.121.25"...  //edited for online use on web
D [26/Oct/2015:14:24:22 -0400] [Job 220] Calling FindDeviceById(cups-GradSpace)
D [26/Oct/2015:14:24:22 -0400] [Job 220] Found device /org/freedesktop/ColorManager/devices/cups_GradSpace
D [26/Oct/2015:14:24:22 -0400] [Job 220] Calling org.freedesktop.ColorManager.Device.Get(ProfilingInhibitors)
D [26/Oct/2015:14:24:22 -0400] [Job 220] PPD uses qualifier 'Gray.Plain.'
D [26/Oct/2015:14:24:22 -0400] [Job 220] Calling FindDeviceById(cups-GradSpace)
D [26/Oct/2015:14:24:22 -0400] [Job 220] Found device /org/freedesktop/ColorManager/devices/cups_GradSpace
D [26/Oct/2015:14:24:22 -0400] [Job 220] Calling GetProfileForQualifiers(Gray.Plain....)
D [26/Oct/2015:14:24:22 -0400] [Job 220] Found profile /org/freedesktop/ColorManager/profiles/GradSpace_Gray__
D [26/Oct/2015:14:24:22 -0400] [Job 220] Calling org.freedesktop.ColorManager.Profile.Get(Filename)
D [26/Oct/2015:14:24:22 -0400] [Job 220] Use profile filename: ''
D [26/Oct/2015:14:24:22 -0400] [Job 220] Using ICC Profile ''
D [26/Oct/2015:14:24:22 -0400] [Job 220] Ghostscript command line: /usr/bin/gs -dQUIET -dPARANOIDSAFER -dNOPAUSE -dBATCH -dNOINTERPOLATE -sDEVICE=cups -sstdout=%stderr -sOutputFile=%stdout -sMediaType=Plain -sOutputType=0 -r600x600 -dMediaPosition=7 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -dcupsBitsPerColor=1 -dcupsColorOrder=0 -dcupsColorSpace=3 -dcupsRowCount=1 -dcupsRowStep=2 -dcupsInteger0=2 -scupsPageSizeName=Letter -I/usr/share/cups/fonts -c '<</.HWMargins[18.000000 14.000000 18.000000 14.000000] /Margins[0 0]>>setpagedevice' -f -_
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[8]="HOME=/var/spool/cups/tmp"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[10]="SERVER_ADMIN=root@Parallels"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[11]="SOFTWARE=CUPS/1.7.2"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[12]="USER=root"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[13]="CUPS_MAX_MESSAGE=2047"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[16]="IPP_PORT=631"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[17]="CHARSET=utf-8"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[18]="LANG=en_US.UTF-8"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[19]="PPD=/etc/cups/ppd/GradSpace.ppd"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[20]="RIP_MAX_CACHE=128m"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[21]="CONTENT_TYPE=application/pdf"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[22]="DEVICE_URI=socket://10.248.121.25:9100"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[23]="PRINTER_INFO=Grad Student Space Printer"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[24]="PRINTER_LOCATION=Architecture 2nd Floor"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[25]="PRINTER=GradSpace"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[26]="PRINTER_STATE_REASONS=none"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[27]="CUPS_FILETYPE=document"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[28]="FINAL_CONTENT_TYPE=printer/GradSpace"
D [26/Oct/2015:14:24:22 -0400] [Job 220] envp[29]="AUTH_INFO_REQUIRED=none"
D [26/Oct/2015:14:24:22 -0400] [Job 220] hrDeviceDesc="HP LaserJet P4014"
D [26/Oct/2015:14:24:22 -0400] [Job 220] prtMarkerColorantValue.1.1 = "black"
D [26/Oct/2015:14:24:22 -0400] [Job 220] ATTR: marker-colors=#000000,none
D [26/Oct/2015:14:24:22 -0400] [Job 220] ATTR: marker-names='"Black Cartridge HP CC364A"','"Maintenance Kit HP 110V-CB388A, 220V-CB389A"'
D [26/Oct/2015:14:24:22 -0400] [Job 220] ATTR: marker-types=toner-cartridge,fuser
D [26/Oct/2015:14:24:22 -0400] [Job 220] ATTR: marker-levels=91,43
D [26/Oct/2015:14:24:22 -0400] [Job 220] new_supply_state=0, change_state=ffff
D [26/Oct/2015:14:24:22 -0400] [Job 220] STATE: -developer-low-report
D [26/Oct/2015:14:24:22 -0400] [Job 220] STATE: -developer-empty-warning
D [26/Oct/2015:14:24:22 -0400] [Job 220] STATE: -marker-supply-low-report
D [26/Oct/2015:14:24:22 -0400] [Job 220] STATE: -marker-supply-empty-warning
D [26/Oct/2015:14:24:22 -0400] [Job 220] STATE: -opc-near-eol-report
D [26/Oct/2015:14:24:22 -0400] [Job 220] STATE: -opc-life-over-warning
D [26/Oct/2015:14:24:22 -0400] [Job 220] STATE: -toner-low-report
D [26/Oct/2015:14:24:22 -0400] [Job 220] STATE: -toner-empty-warning
D [26/Oct/2015:14:24:22 -0400] [Job 220] STATE: -waste-receptacle-almost-full-report
D [26/Oct/2015:14:24:22 -0400] [Job 220] STATE: -waste-receptacle-full-warning
D [26/Oct/2015:14:24:22 -0400] [Job 220] STATE: -cleaner-life-almost-over-report
D [26/Oct/2015:14:24:22 -0400] [Job 220] STATE: -cleaner-life-over-warning
D [26/Oct/2015:14:24:22 -0400] [Job 220] Start rendering...
D [26/Oct/2015:14:24:22 -0400] [Job 220] Set job-printer-state-message to "Start rendering...", current level=INFO
D [26/Oct/2015:14:24:22 -0400] [Job 220] Processing page 1...
D [26/Oct/2015:14:24:22 -0400] [Job 220] Set job-printer-state-message to "Processing page 1...", current level=INFO
D [26/Oct/2015:14:24:22 -0400] [Job 220] new_state=100, change_state=ffff
D [26/Oct/2015:14:24:22 -0400] [Job 220] STATE: -media-empty-warning
D [26/Oct/2015:14:24:22 -0400] [Job 220] STATE: -door-open-report
D [26/Oct/2015:14:24:22 -0400] [Job 220] STATE: -media-jam-warning
D [26/Oct/2015:14:24:22 -0400] [Job 220] STATE: -input-tray-missing-warning
D [26/Oct/2015:14:24:22 -0400] [Job 220] STATE: -output-tray-missing-warning
D [26/Oct/2015:14:24:22 -0400] [Job 220] STATE: -marker-supply-missing-warning
D [26/Oct/2015:14:24:22 -0400] [Job 220] STATE: -output-area-almost-full-report
D [26/Oct/2015:14:24:22 -0400] [Job 220] STATE: -output-area-full-warning
D [26/Oct/2015:14:24:22 -0400] [Job 220] **** Warning:  Invalid Page count.
D [26/Oct/2015:14:24:22 -0400] [Job 220] **** Warning:  Invalid Page count.
D [26/Oct/2015:14:24:22 -0400] [Job 220] No pages will be processed (FirstPage > LastPage).
D [26/Oct/2015:14:24:22 -0400] [Job 220] **** This file had errors that were repaired or ignored.
D [26/Oct/2015:14:24:22 -0400] [Job 220] **** The file was produced by: 
D [26/Oct/2015:14:24:22 -0400] [Job 220] **** >>>> cairo 1.13.1 ([http://cairographics.org](http://cairographics.org)) <<<<
D [26/Oct/2015:14:24:22 -0400] [Job 220] **** Please notify the author of the software that produced this
D [26/Oct/2015:14:24:22 -0400] [Job 220] **** file that it does not conform to Adobe's published PDF
D [26/Oct/2015:14:24:22 -0400] [Job 220] **** specification.
D [26/Oct/2015:14:24:22 -0400] [Job 220] Rendering completed
D [26/Oct/2015:14:24:22 -0400] [Job 220] Set job-printer-state-message to "Rendering completed", current level=INFO
D [26/Oct/2015:14:24:22 -0400] [Job 220] prnt/hpcups/HPCupsFilter.cpp 530: cupsRasterOpen failed, fd = 0
D [26/Oct/2015:14:24:22 -0400] [Job 220] PID 3101 (/usr/lib/cups/filter/gstoraster) exited with no errors.
D [26/Oct/2015:14:24:22 -0400] [Job 220] PID 3102 (/usr/lib/cups/filter/hpcups) stopped with status 1.
D [26/Oct/2015:14:24:22 -0400] [Job 220] Hint: Try setting the LogLevel to "debug" to find out more.
D [26/Oct/2015:14:24:22 -0400] [Job 220] backendWaitLoop(snmp_fd=5, addr=0x7f3a6cfbfc28, side_cb=0x7f3a6b0dd200)
D [26/Oct/2015:14:24:22 -0400] [Job 220] PID 3103 (/usr/lib/cups/backend/socket) exited with no errors.
D [26/Oct/2015:14:24:22 -0400] [Job 220] End of messages
D [26/Oct/2015:14:24:22 -0400] [Job 220] printer-state=3(idle)
D [26/Oct/2015:14:24:22 -0400] [Job 220] printer-state-message="Filter failed"
D [26/Oct/2015:14:24:22 -0400] [Job 220] printer-state-reasons=none
```

---

### Post by tgalati4 on 2015-10-26
Try printing the odd pages to  "Print to File", then examine the PDF file that is created.  There may be some restrictions on the files that prevent certain operations.  Use *qpdf* to examine the files and check the permissions.  Then try streamlining the files to get them to perform better.

Try your 2-sided method with some open-source PDF files (like an Ubuntu tutorial), and see if the filter/queue locks up. Generally deleting the printer and reinstalling will create a new spool.

---

### Post by Vladlenin5000 on 2015-10-26
```
D [26/Oct/2015:14:24:22 -0400] [Job 220] **** Warning:  Invalid Page count.
D [26/Oct/2015:14:24:22 -0400] [Job 220] **** Warning:  Invalid Page count.
D [26/Oct/2015:14:24:22 -0400] [Job 220] No pages will be processed (FirstPage > LastPage).
```

This seems to be the problem and it's the first time I'm seeing such odd error (pun intended). Googling didn't help. All I could find are mentions of PostgreSQL issues, printing to HylaFax  (a TIFF file !!!) or Ghostscript... A bad file seems to be the common denominator.

---

### Post by QIII on 2015-10-26
timothylegg:

Please use code tags for commands and their results in the terminal:

1. If you are using the "Reply to Thread" button - highlight text and use the # button in the text box header.  Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

Thanks!

---

