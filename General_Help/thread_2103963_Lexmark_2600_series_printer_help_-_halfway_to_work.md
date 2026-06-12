---
title: "Lexmark 2600 series printer help - halfway to working."
date: 2013-01-11
forum: General Help
---

### Post by EchoVelocity on 2013-01-11
Hey.

I've been trying all evening to get a family members printer to work, and now I've ended up at a "filter failed" printer status. Here is the CUPS log from the troubleshooter:
[http://pastebin.com/M7Lyx7Yj](http://pastebin.com/M7Lyx7Yj)
```
D [11/Jan/2013:20:38:07 +0000] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [11/Jan/2013:20:38:07 +0000] [Client 16] POST / HTTP/1.1
D [11/Jan/2013:20:38:07 +0000] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [11/Jan/2013:20:38:07 +0000] [Client 16] No authentication data provided.
D [11/Jan/2013:20:38:07 +0000] [Client 16] 2.0 Get-Jobs 128
D [11/Jan/2013:20:38:07 +0000] Get-Jobs ipp://localhost/printers/
D [11/Jan/2013:20:38:07 +0000] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [11/Jan/2013:20:38:07 +0000] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [11/Jan/2013:20:38:07 +0000] [Client 16] POST / HTTP/1.1
D [11/Jan/2013:20:38:07 +0000] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [11/Jan/2013:20:38:07 +0000] [Client 16] No authentication data provided.
D [11/Jan/2013:20:38:07 +0000] [Client 16] 2.0 Get-Jobs 129
D [11/Jan/2013:20:38:07 +0000] Get-Jobs ipp://localhost/printers/
D [11/Jan/2013:20:38:07 +0000] [Job 1] Loading attributes...
D [11/Jan/2013:20:38:07 +0000] [Job 2] Loading attributes...
D [11/Jan/2013:20:38:07 +0000] [Job 3] Loading attributes...
D [11/Jan/2013:20:38:07 +0000] [Job 4] Loading attributes...
D [11/Jan/2013:20:38:07 +0000] [Job 5] Loading attributes...
D [11/Jan/2013:20:38:07 +0000] [Job 6] Loading attributes...
D [11/Jan/2013:20:38:07 +0000] [Job 7] Loading attributes...
D [11/Jan/2013:20:38:07 +0000] [Job 8] Loading attributes...
D [11/Jan/2013:20:38:07 +0000] [Job 9] Loading attributes...
D [11/Jan/2013:20:38:07 +0000] [Job 10] Loading attributes...
D [11/Jan/2013:20:38:07 +0000] [Job 11] Loading attributes...
D [11/Jan/2013:20:38:07 +0000] [Job 12] Loading attributes...
D [11/Jan/2013:20:38:07 +0000] [Job 13] Loading attributes...
D [11/Jan/2013:20:38:07 +0000] [Job 14] Loading attributes...
D [11/Jan/2013:20:38:07 +0000] [Job 15] Loading attributes...
D [11/Jan/2013:20:38:07 +0000] [Job 22] Loading attributes...
D [11/Jan/2013:20:38:07 +0000] [Job 22] Loading attributes...
D [11/Jan/2013:20:38:07 +0000] [Job 23] Loading attributes...
D [11/Jan/2013:20:38:07 +0000] [Job 23] Loading attributes...
D [11/Jan/2013:20:38:07 +0000] [Job 24] Loading attributes...
D [11/Jan/2013:20:38:07 +0000] [Job 24] Loading attributes...
D [11/Jan/2013:20:38:07 +0000] [Job 25] Loading attributes...
D [11/Jan/2013:20:38:07 +0000] [Job 28] Loading attributes...
D [11/Jan/2013:20:38:07 +0000] [Job 29] Loading attributes...
D [11/Jan/2013:20:38:07 +0000] [Job 30] Loading attributes...
D [11/Jan/2013:20:38:07 +0000] [Job 31] Loading attributes...
D [11/Jan/2013:20:38:07 +0000] [Job 32] Loading attributes...
D [11/Jan/2013:20:38:07 +0000] [Job 33] Loading attributes...
D [11/Jan/2013:20:38:07 +0000] [Job 34] Loading attributes...
D [11/Jan/2013:20:38:07 +0000] [Job 35] Loading attributes...
D [11/Jan/2013:20:38:07 +0000] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [11/Jan/2013:20:38:07 +0000] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [11/Jan/2013:20:38:07 +0000] [Client 16] POST / HTTP/1.1
D [11/Jan/2013:20:38:07 +0000] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [11/Jan/2013:20:38:07 +0000] [Client 16] No authentication data provided.
D [11/Jan/2013:20:38:07 +0000] [Client 16] 2.0 Create-Printer-Subscription 130
D [11/Jan/2013:20:38:07 +0000] Create-Printer-Subscription /
D [11/Jan/2013:20:38:07 +0000] cupsdCreateSubscription(con=0xb78dfda0(16), uri="/")
D [11/Jan/2013:20:38:07 +0000] pullmethod="ippget"
D [11/Jan/2013:20:38:07 +0000] notify-lease-duration=86400
D [11/Jan/2013:20:38:07 +0000] notify-time-interval=0
D [11/Jan/2013:20:38:07 +0000] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")
D [11/Jan/2013:20:38:07 +0000] Added subscription #101 for server.
D [11/Jan/2013:20:38:07 +0000] cupsdMarkDirty(-----S)
D [11/Jan/2013:20:38:07 +0000] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
D [11/Jan/2013:20:38:07 +0000] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost
D [11/Jan/2013:20:38:07 +0000] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [11/Jan/2013:20:38:08 +0000] [Client 16] POST / HTTP/1.1
D [11/Jan/2013:20:38:08 +0000] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [11/Jan/2013:20:38:08 +0000] [Client 16] No authentication data provided.
D [11/Jan/2013:20:38:08 +0000] [Client 16] 2.0 Get-Notifications 131
D [11/Jan/2013:20:38:08 +0000] Get-Notifications /
D [11/Jan/2013:20:38:08 +0000] cupsdIsAuthorized: requesting-user-name="pauline"
D [11/Jan/2013:20:38:08 +0000] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [11/Jan/2013:20:38:08 +0000] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [11/Jan/2013:20:38:15 +0000] [Client 18] Accepted from localhost (Domain)
D [11/Jan/2013:20:38:15 +0000] [Client 18] POST /printers/Lexmark-2600-Series HTTP/1.1
D [11/Jan/2013:20:38:15 +0000] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [11/Jan/2013:20:38:15 +0000] [Client 18] No authentication data provided.
D [11/Jan/2013:20:38:15 +0000] [Client 18] 2.0 Print-Job 132
D [11/Jan/2013:20:38:15 +0000] Print-Job ipp://localhost/printers/Lexmark-2600-Series
D [11/Jan/2013:20:38:15 +0000] [Job ???] Auto-typing file...
I [11/Jan/2013:20:38:15 +0000] [Job ???] Request file type is application/vnd.cups-pdf-banner.
D [11/Jan/2013:20:38:15 +0000] cupsdMarkDirty(----J-)
D [11/Jan/2013:20:38:15 +0000] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
D [11/Jan/2013:20:38:15 +0000] add_job: requesting-user-name="pauline"
D [11/Jan/2013:20:38:15 +0000] Adding default job-sheets values "none,none"...
I [11/Jan/2013:20:38:15 +0000] [Job 36] Adding start banner page "none".
D [11/Jan/2013:20:38:15 +0000] cupsdMarkDirty(-----S)
D [11/Jan/2013:20:38:15 +0000] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
D [11/Jan/2013:20:38:15 +0000] cupsdMarkDirty(----J-)
D [11/Jan/2013:20:38:15 +0000] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
I [11/Jan/2013:20:38:15 +0000] [Job 36] Adding end banner page "none".
I [11/Jan/2013:20:38:15 +0000] [Job 36] File of type application/vnd.cups-pdf-banner queued by "pauline".
D [11/Jan/2013:20:38:15 +0000] [Job 36] hold_until=0
I [11/Jan/2013:20:38:15 +0000] [Job 36] Queued on "Lexmark-2600-Series" by "pauline".
D [11/Jan/2013:20:38:15 +0000] [Job 36] time-at-processing=1357936695
D [11/Jan/2013:20:38:15 +0000] cupsdMarkDirty(----J-)
D [11/Jan/2013:20:38:15 +0000] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
D [11/Jan/2013:20:38:15 +0000] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
D [11/Jan/2013:20:38:15 +0000] cupsdMarkDirty(-----S)
D [11/Jan/2013:20:38:15 +0000] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
D [11/Jan/2013:20:38:15 +0000] [Job 36] job-sheets=none,none
D [11/Jan/2013:20:38:15 +0000] [Job 36] argv[0]="Lexmark-2600-Series"
D [11/Jan/2013:20:38:15 +0000] [Job 36] argv[1]="36"
D [11/Jan/2013:20:38:15 +0000] [Job 36] argv[2]="pauline"
D [11/Jan/2013:20:38:15 +0000] [Job 36] argv[3]="Test Page"
D [11/Jan/2013:20:38:15 +0000] [Job 36] argv[4]="1"
D [11/Jan/2013:20:38:15 +0000] [Job 36] argv[5]="job-uuid=urn:uuid:ca46a1a3-e7cb-3c7e-74fa-6319cb742042 job-originating-host-name=localhost time-at-creation=1357936695 time-at-processing=1357936695"
D [11/Jan/2013:20:38:15 +0000] [Job 36] argv[6]="/var/spool/cups/d00036-001"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[8]="HOME=/var/spool/cups/tmp"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[10]="SERVER_ADMIN=root@pauline-computer"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[11]="SOFTWARE=CUPS/1.6.1"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[13]="USER=root"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[14]="CUPS_MAX_MESSAGE=2047"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[16]="CUPS_ENCRYPTION=IfRequested"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[17]="IPP_PORT=631"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[18]="CHARSET=utf-8"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[19]="LANG=en_GB.UTF-8"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[20]="PPD=/etc/cups/ppd/Lexmark-2600-Series.ppd"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[21]="RIP_MAX_CACHE=128m"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[22]="CONTENT_TYPE=application/vnd.cups-pdf-banner"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[23]="DEVICE_URI=usb://Lexmark/2600%20Series?serial=3053730A5465971&interface=1"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[24]="PRINTER_INFO=Lexmark 2600 Series"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[25]="PRINTER_LOCATION=pauline-computer"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[26]="PRINTER=Lexmark-2600-Series"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[27]="PRINTER_STATE_REASONS=none"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[28]="CUPS_FILETYPE=document"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[29]="FINAL_CONTENT_TYPE=printer/Lexmark-2600-Series"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[30]="AUTH_I****"
I [11/Jan/2013:20:38:15 +0000] [Job 36] Started filter /usr/lib/cups/filter/bannertopdf (PID 6202)
I [11/Jan/2013:20:38:15 +0000] [Job 36] Started filter /usr/lib/cups/filter/pdftopdf (PID 6203)
I [11/Jan/2013:20:38:15 +0000] [Job 36] Started filter /usr/lib/cups/filter/gstoraster (PID 6204)
I [11/Jan/2013:20:38:15 +0000] [Job 36] Started filter /usr/local/lexmark/lxk08/bin/printdriver (PID 6205)
I [11/Jan/2013:20:38:15 +0000] [Job 36] Started backend /usr/lib/cups/backend/usb (PID 6206)
D [11/Jan/2013:20:38:15 +0000] cupsdMarkDirty(-----S)
D [11/Jan/2013:20:38:15 +0000] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Active clients and dirty files"
D [11/Jan/2013:20:38:15 +0000] Returning IPP successful-ok for Print-Job (ipp://localhost/printers/Lexmark-2600-Series) from localhost
D [11/Jan/2013:20:38:15 +0000] [Notifier] state=3
D [11/Jan/2013:20:38:15 +0000] [Notifier] state=3
D [11/Jan/2013:20:38:15 +0000] [Notifier] state=3
D [11/Jan/2013:20:38:15 +0000] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [11/Jan/2013:20:38:15 +0000] [Job 36] Printing on printer with URI: usb://Lexmark/2600%20Series?serial=3053730A5465971&interface=1
D [11/Jan/2013:20:38:15 +0000] [Job 36] libusb_get_device_list=7
D [11/Jan/2013:20:38:15 +0000] [Job 36] PID 6202 (/usr/lib/cups/filter/bannertopdf) exited with no errors.
D [11/Jan/2013:20:38:15 +0000] [Job 36] STATE: +connecting-to-device
D [11/Jan/2013:20:38:15 +0000] cupsdMarkDirty(----J-)
D [11/Jan/2013:20:38:15 +0000] cupsdSetBusyState: newbusy="Dirty files", busy="Printing jobs and dirty files"
D [11/Jan/2013:20:38:15 +0000] cupsdMarkDirty(-----S)
D [11/Jan/2013:20:38:15 +0000] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
D [11/Jan/2013:20:38:15 +0000] [Notifier] state=3
D [11/Jan/2013:20:38:15 +0000] [Job 36] PPD uses qualifier 'Color.Plain.'
D [11/Jan/2013:20:38:15 +0000] [Job 36] STATE: -connecting-to-device
D [11/Jan/2013:20:38:15 +0000] cupsdMarkDirty(----J-)
D [11/Jan/2013:20:38:15 +0000] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Dirty files"
D [11/Jan/2013:20:38:15 +0000] cupsdMarkDirty(-----S)
D [11/Jan/2013:20:38:15 +0000] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [11/Jan/2013:20:38:15 +0000] [Notifier] state=3
D [11/Jan/2013:20:38:15 +0000] [Job 36] Calling FindDeviceById(Lexmark-2600-Series)
D [11/Jan/2013:20:38:15 +0000] [Job 36] PID 6203 (/usr/lib/cups/filter/pdftopdf) exited with no errors.
D [11/Jan/2013:20:38:15 +0000] [Job 36] Failed to send: org.freedesktop.ColorManager.Failed:device id 'Lexmark-2600-Series' does not exists
D [11/Jan/2013:20:38:15 +0000] [Job 36] Failed to get profile filename!
I [11/Jan/2013:20:38:15 +0000] [Job 36] no profiles specified in PPD
D [11/Jan/2013:20:38:15 +0000] cupsdMarkDirty(----J-)
D [11/Jan/2013:20:38:15 +0000] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [11/Jan/2013:20:38:15 +0000] [Job 36] Set job-printer-state-message to "no profiles specified in PPD", current level=INFO
D [11/Jan/2013:20:38:15 +0000] [Job 36] Ghostscript command line: /usr/bin/gs -dQUIET -dPARANOIDSAFER -dNOPAUSE -dBATCH -dNOINTERPOLATE -sDEVICE=cups -sstdout=%stderr -sOutputFile=%stdout -sOutputType=2 -r600x600 -dDEVICEWIDTHPOINTS=595 -dDEVICEHEIGHTPOINTS=841 -dcupsMediaType=1 -dcupsBitsPerColor=8 -dcupsColorOrder=0 -dcupsColorSpace=1 -dcupsCompression=8 -dcupsRowStep=1 -scupsPageSizeName=A4 -I/usr/share/cups/fonts -c -f -_
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[8]="HOME=/var/spool/cups/tmp"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[10]="SERVER_ADMIN=root@pauline-computer"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[11]="SOFTWARE=CUPS/1.6.1"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[12]="USER=root"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[13]="CUPS_MAX_MESSAGE=2047"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[16]="IPP_PORT=631"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[17]="CHARSET=utf-8"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[18]="LANG=en_GB.UTF-8"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[19]="PPD=/etc/cups/ppd/Lexmark-2600-Series.ppd"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[20]="RIP_MAX_CACHE=128m"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[21]="CONTENT_TYPE=application/vnd.cups-pdf-banner"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[22]="DEVICE_URI=usb://Lexmark/2600%20Series?serial=3053730A5465971&interface=1"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[23]="PRINTER_INFO=Lexmark 2600 Series"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[24]="PRINTER_LOCATION=pauline-computer"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[25]="PRINTER=Lexmark-2600-Series"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[26]="PRINTER_STATE_REASONS=none"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[27]="CUPS_FILETYPE=document"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[28]="FINAL_CONTENT_TYPE=printer/Lexmark-2600-Series"
D [11/Jan/2013:20:38:15 +0000] [Job 36] envp[29]="AUTH_INFO_REQUIRED=none"
D [11/Jan/2013:20:38:15 +0000] cupsdMarkDirty(-----S)
D [11/Jan/2013:20:38:15 +0000] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [11/Jan/2013:20:38:15 +0000] cupsdMarkDirty(-----S)
D [11/Jan/2013:20:38:15 +0000] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [11/Jan/2013:20:38:15 +0000] [Job 36] Device protocol: 2
I [11/Jan/2013:20:38:15 +0000] [Job 36] Sending data to printer.
D [11/Jan/2013:20:38:15 +0000] cupsdMarkDirty(----J-)
D [11/Jan/2013:20:38:15 +0000] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [11/Jan/2013:20:38:15 +0000] [Job 36] Set job-printer-state-message to "Sending data to printer.", current level=INFO
D [11/Jan/2013:20:38:15 +0000] cupsdMarkDirty(-----S)
D [11/Jan/2013:20:38:15 +0000] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [11/Jan/2013:20:38:15 +0000] cupsdMarkDirty(-----S)
D [11/Jan/2013:20:38:15 +0000] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [11/Jan/2013:20:38:15 +0000] [Notifier] state=3
D [11/Jan/2013:20:38:15 +0000] [Notifier] state=3
D [11/Jan/2013:20:38:15 +0000] [Notifier] state=3
D [11/Jan/2013:20:38:15 +0000] [Notifier] state=3
D [11/Jan/2013:20:38:15 +0000] [Client 20] Accepted from localhost (Domain)
D [11/Jan/2013:20:38:15 +0000] [Client 20] POST / HTTP/1.1
D [11/Jan/2013:20:38:15 +0000] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [11/Jan/2013:20:38:15 +0000] [Client 20] No authentication data provided.
D [11/Jan/2013:20:38:15 +0000] [Client 20] 2.0 Get-Notifications 133
D [11/Jan/2013:20:38:15 +0000] Get-Notifications /
D [11/Jan/2013:20:38:15 +0000] cupsdIsAuthorized: requesting-user-name="pauline"
D [11/Jan/2013:20:38:15 +0000] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [11/Jan/2013:20:38:15 +0000] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [11/Jan/2013:20:38:15 +0000] [Client 21] Accepted from localhost (Domain)
D [11/Jan/2013:20:38:15 +0000] [Client 21] POST / HTTP/1.1
D [11/Jan/2013:20:38:15 +0000] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [11/Jan/2013:20:38:15 +0000] [Client 21] No authentication data provided.
D [11/Jan/2013:20:38:15 +0000] [Client 21] 2.0 Get-Printer-Attributes 134
D [11/Jan/2013:20:38:15 +0000] Get-Printer-Attributes ipp://localhost/printers/Lexmark-2600-Series
D [11/Jan/2013:20:38:15 +0000] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/Lexmark-2600-Series) from localhost
D [11/Jan/2013:20:38:15 +0000] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [11/Jan/2013:20:38:15 +0000] [Client 21] POST / HTTP/1.1
D [11/Jan/2013:20:38:15 +0000] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [11/Jan/2013:20:38:15 +0000] [Client 21] No authentication data provided.
D [11/Jan/2013:20:38:15 +0000] [Client 21] 2.0 Get-Printer-Attributes 135
D [11/Jan/2013:20:38:15 +0000] Get-Printer-Attributes ipp://localhost/printers/Lexmark-2600-Series
D [11/Jan/2013:20:38:15 +0000] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/Lexmark-2600-Series) from localhost
D [11/Jan/2013:20:38:15 +0000] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [11/Jan/2013:20:38:15 +0000] [Client 21] POST / HTTP/1.1
D [11/Jan/2013:20:38:15 +0000] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [11/Jan/2013:20:38:15 +0000] [Client 21] No authentication data provided.
D [11/Jan/2013:20:38:15 +0000] [Client 21] 2.0 Get-Printer-Attributes 136
D [11/Jan/2013:20:38:15 +0000] Get-Printer-Attributes ipp://localhost/printers/Lexmark-2600-Series
D [11/Jan/2013:20:38:15 +0000] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/Lexmark-2600-Series) from localhost
D [11/Jan/2013:20:38:15 +0000] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
I [11/Jan/2013:20:38:15 +0000] [Job 36] Start rendering...
D [11/Jan/2013:20:38:15 +0000] cupsdMarkDirty(----J-)
D [11/Jan/2013:20:38:15 +0000] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [11/Jan/2013:20:38:15 +0000] [Job 36] Set job-printer-state-message to "Start rendering...", current level=INFO
I [11/Jan/2013:20:38:15 +0000] [Job 36] Processing page 1...
D [11/Jan/2013:20:38:15 +0000] cupsdMarkDirty(----J-)
D [11/Jan/2013:20:38:15 +0000] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [11/Jan/2013:20:38:15 +0000] [Job 36] Set job-printer-state-message to "Processing page 1...", current level=INFO
D [11/Jan/2013:20:38:15 +0000] cupsdMarkDirty(-----S)
D [11/Jan/2013:20:38:15 +0000] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [11/Jan/2013:20:38:15 +0000] cupsdMarkDirty(-----S)
D [11/Jan/2013:20:38:15 +0000] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [11/Jan/2013:20:38:15 +0000] [Notifier] state=3
D [11/Jan/2013:20:38:15 +0000] [Notifier] state=3
D [11/Jan/2013:20:38:15 +0000] [Client 21] POST / HTTP/1.1
D [11/Jan/2013:20:38:15 +0000] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [11/Jan/2013:20:38:15 +0000] [Client 21] No authentication data provided.
D [11/Jan/2013:20:38:15 +0000] [Client 21] 2.0 Get-Printer-Attributes 137
D [11/Jan/2013:20:38:15 +0000] Get-Printer-Attributes ipp://localhost/printers/Lexmark-2600-Series
D [11/Jan/2013:20:38:15 +0000] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/Lexmark-2600-Series) from localhost
D [11/Jan/2013:20:38:15 +0000] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [11/Jan/2013:20:38:15 +0000] [Client 21] POST / HTTP/1.1
D [11/Jan/2013:20:38:15 +0000] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [11/Jan/2013:20:38:15 +0000] [Client 21] No authentication data provided.
D [11/Jan/2013:20:38:15 +0000] [Client 21] 2.0 Get-Printer-Attributes 138
D [11/Jan/2013:20:38:15 +0000] Get-Printer-Attributes ipp://localhost/printers/Lexmark-2600-Series
D [11/Jan/2013:20:38:15 +0000] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/Lexmark-2600-Series) from localhost
D [11/Jan/2013:20:38:15 +0000] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [11/Jan/2013:20:38:15 +0000] [Client 20] HTTP_WAITING Closing on EOF
D [11/Jan/2013:20:38:15 +0000] [Client 20] Closing connection.
D [11/Jan/2013:20:38:15 +0000] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [11/Jan/2013:20:38:15 +0000] [Client 16] POST / HTTP/1.1
D [11/Jan/2013:20:38:15 +0000] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [11/Jan/2013:20:38:15 +0000] [Client 16] No authentication data provided.
D [11/Jan/2013:20:38:15 +0000] [Client 16] 2.0 Get-Notifications 139
D [11/Jan/2013:20:38:15 +0000] Get-Notifications /
D [11/Jan/2013:20:38:15 +0000] cupsdIsAuthorized: requesting-user-name="pauline"
D [11/Jan/2013:20:38:15 +0000] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [11/Jan/2013:20:38:15 +0000] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [11/Jan/2013:20:38:15 +0000] [Client 20] Accepted from localhost (Domain)
D [11/Jan/2013:20:38:15 +0000] [Client 20] POST / HTTP/1.1
D [11/Jan/2013:20:38:15 +0000] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [11/Jan/2013:20:38:15 +0000] [Client 20] No authentication data provided.
D [11/Jan/2013:20:38:15 +0000] [Client 20] 2.0 CUPS-Get-Printers 140
D [11/Jan/2013:20:38:15 +0000] CUPS-Get-Printers
D [11/Jan/2013:20:38:15 +0000] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [11/Jan/2013:20:38:15 +0000] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [11/Jan/2013:20:38:15 +0000] [Client 20] POST / HTTP/1.1
D [11/Jan/2013:20:38:15 +0000] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [11/Jan/2013:20:38:15 +0000] [Client 20] No authentication data provided.
D [11/Jan/2013:20:38:15 +0000] [Client 20] 2.0 CUPS-Get-Classes 141
D [11/Jan/2013:20:38:15 +0000] CUPS-Get-Classes
D [11/Jan/2013:20:38:15 +0000] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [11/Jan/2013:20:38:15 +0000] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [11/Jan/2013:20:38:15 +0000] [Client 20] POST / HTTP/1.1
D [11/Jan/2013:20:38:15 +0000] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [11/Jan/2013:20:38:15 +0000] [Client 20] No authentication data provided.
D [11/Jan/2013:20:38:15 +0000] [Client 20] 2.0 CUPS-Get-Default 142
D [11/Jan/2013:20:38:15 +0000] CUPS-Get-Default
D [11/Jan/2013:20:38:15 +0000] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [11/Jan/2013:20:38:15 +0000] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [11/Jan/2013:20:38:16 +0000] [Client 22] Accepted from localhost (Domain)
D [11/Jan/2013:20:38:16 +0000] [Client 22] POST / HTTP/1.1
D [11/Jan/2013:20:38:16 +0000] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [11/Jan/2013:20:38:16 +0000] [Client 22] No authentication data provided.
D [11/Jan/2013:20:38:16 +0000] [Client 22] 2.0 Get-Notifications 143
D [11/Jan/2013:20:38:16 +0000] Get-Notifications /
D [11/Jan/2013:20:38:16 +0000] cupsdIsAuthorized: requesting-user-name="pauline"
D [11/Jan/2013:20:38:16 +0000] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [11/Jan/2013:20:38:16 +0000] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [11/Jan/2013:20:38:16 +0000] [Client 21] POST / HTTP/1.1
D [11/Jan/2013:20:38:16 +0000] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [11/Jan/2013:20:38:16 +0000] [Client 21] No authentication data provided.
D [11/Jan/2013:20:38:16 +0000] [Client 21] 2.0 Get-Printer-Attributes 144
D [11/Jan/2013:20:38:16 +0000] Get-Printer-Attributes ipp://localhost/printers/Lexmark-2600-Series
D [11/Jan/2013:20:38:16 +0000] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/Lexmark-2600-Series) from localhost
D [11/Jan/2013:20:38:16 +0000] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [11/Jan/2013:20:38:16 +0000] [Client 22] HTTP_WAITING Closing on EOF
D [11/Jan/2013:20:38:16 +0000] [Client 22] Closing connection.
D [11/Jan/2013:20:38:16 +0000] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [11/Jan/2013:20:38:16 +0000] [Client 20] POST / HTTP/1.1
D [11/Jan/2013:20:38:16 +0000] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [11/Jan/2013:20:38:16 +0000] [Client 20] No authentication data provided.
D [11/Jan/2013:20:38:16 +0000] [Client 20] 2.0 CUPS-Get-Printers 145
D [11/Jan/2013:20:38:16 +0000] CUPS-Get-Printers
D [11/Jan/2013:20:38:16 +0000] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [11/Jan/2013:20:38:16 +0000] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [11/Jan/2013:20:38:16 +0000] [Client 20] POST / HTTP/1.1
D [11/Jan/2013:20:38:16 +0000] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [11/Jan/2013:20:38:16 +0000] [Client 20] No authentication data provided.
D [11/Jan/2013:20:38:16 +0000] [Client 20] 2.0 CUPS-Get-Classes 146
D [11/Jan/2013:20:38:16 +0000] CUPS-Get-Classes
D [11/Jan/2013:20:38:16 +0000] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [11/Jan/2013:20:38:16 +0000] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [11/Jan/2013:20:38:16 +0000] [Client 20] POST / HTTP/1.1
D [11/Jan/2013:20:38:16 +0000] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [11/Jan/2013:20:38:16 +0000] [Client 20] No authentication data provided.
D [11/Jan/2013:20:38:16 +0000] [Client 20] 2.0 CUPS-Get-Default 147
D [11/Jan/2013:20:38:16 +0000] CUPS-Get-Default
D [11/Jan/2013:20:38:16 +0000] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [11/Jan/2013:20:38:16 +0000] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [11/Jan/2013:20:38:18 +0000] [Job 36] Read 8 bytes of print data...
D [11/Jan/2013:20:38:18 +0000] [Job 36] Read 8 bytes of back-channel data...
D [11/Jan/2013:20:38:18 +0000] [Job 36] Wrote 8 bytes of print data...
D [11/Jan/2013:20:38:18 +0000] [Client 22] Accepted from localhost (Domain)
D [11/Jan/2013:20:38:18 +0000] [Client 22] POST / HTTP/1.1
D [11/Jan/2013:20:38:18 +0000] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [11/Jan/2013:20:38:18 +0000] [Client 22] No authentication data provided.
D [11/Jan/2013:20:38:18 +0000] [Client 22] 2.0 CUPS-Get-Printers 1
D [11/Jan/2013:20:38:18 +0000] CUPS-Get-Printers
D [11/Jan/2013:20:38:18 +0000] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [11/Jan/2013:20:38:18 +0000] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [11/Jan/2013:20:38:18 +0000] [Client 22] HTTP_WAITING Closing on EOF
D [11/Jan/2013:20:38:18 +0000] [Client 22] Closing connection.
D [11/Jan/2013:20:38:18 +0000] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [11/Jan/2013:20:38:18 +0000] [Job 36] Read 15 bytes of print data...
D [11/Jan/2013:20:38:18 +0000] [Job 36] Wrote 15 bytes of print data...
D [11/Jan/2013:20:38:18 +0000] [Job 36] Read 15 bytes of back-channel data...
D [11/Jan/2013:20:38:18 +0000] [Job 36] Read 8 bytes of print data...
D [11/Jan/2013:20:38:18 +0000] [Job 36] Wrote 8 bytes of print data...
D [11/Jan/2013:20:38:18 +0000] [Job 36] Read 9 bytes of back-channel data...
D [11/Jan/2013:20:38:18 +0000] [Job 36] Read 8 bytes of print data...
D [11/Jan/2013:20:38:18 +0000] [Job 36] Wrote 8 bytes of print data...
D [11/Jan/2013:20:38:18 +0000] [Job 36] Read 8 bytes of back-channel data...
D [11/Jan/2013:20:38:19 +0000] [Job 36] Read 8 bytes of print data...
D [11/Jan/2013:20:38:19 +0000] [Job 36] Wrote 8 bytes of print data...
D [11/Jan/2013:20:38:19 +0000] [Job 36] Read 512 bytes of back-channel data...
D [11/Jan/2013:20:38:19 +0000] [Job 36] Read 37 bytes of back-channel data...
D [11/Jan/2013:20:38:19 +0000] [Job 36] PID 6205 (/usr/local/lexmark/lxk08/bin/printdriver) crashed on signal 11.
D [11/Jan/2013:20:38:19 +0000] [Job 36] Sent 47 bytes...
D [11/Jan/2013:20:38:19 +0000] [Job 36] Waiting for read thread to exit...
D [11/Jan/2013:20:38:19 +0000] [Job 36] PID 6204 (/usr/lib/cups/filter/gstoraster) stopped with status 13.
D [11/Jan/2013:20:38:26 +0000] [Job 36] Read thread still active, aborting the pending read...
D [11/Jan/2013:20:38:27 +0000] [Job 36] PID 6206 (/usr/lib/cups/backend/usb) exited with no errors.
D [11/Jan/2013:20:38:27 +0000] cupsdMarkDirty(-----S)
D [11/Jan/2013:20:38:27 +0000] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
E [11/Jan/2013:20:38:27 +0000] [Job 36] Job stopped due to filter errors; please consult the error_log file for details.
D [11/Jan/2013:20:38:27 +0000] cupsdMarkDirty(----J-)
D [11/Jan/2013:20:38:27 +0000] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [11/Jan/2013:20:38:27 +0000] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [11/Jan/2013:20:38:27 +0000] cupsdMarkDirty(-----S)
D [11/Jan/2013:20:38:27 +0000] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [11/Jan/2013:20:38:27 +0000] [Job 36] The following messages were recorded from 20:38:15 to 20:38:15
D [11/Jan/2013:20:38:27 +0000] [Job 36] Printer found with device ID: MFG:Lexmark;CMD:CPDNPA004;MODEL: 2600 Series;CLASS:Printer;DES:Lexmark 2600 Series; Device URI: usb://Lexmark/2600%20Series?serial=3053730A5465971&interface=1
D [11/Jan/2013:20:38:27 +0000] [Job 36] End of messages
D [11/Jan/2013:20:38:27 +0000] [Job 36] printer-state=3(idle)
D [11/Jan/2013:20:38:27 +0000] [Job 36] printer-state-message="Filter failed"
D [11/Jan/2013:20:38:27 +0000] [Job 36] printer-state-reasons=none
D [11/Jan/2013:20:38:27 +0000] [Notifier] state=3
D [11/Jan/2013:20:38:27 +0000] [Notifier] state=3
D [11/Jan/2013:20:38:27 +0000] [Client 19] Accepted from localhost (Domain)
D [11/Jan/2013:20:38:27 +0000] [Client 19] POST / HTTP/1.1
D [11/Jan/2013:20:38:27 +0000] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Printing jobs and dirty files"
D [11/Jan/2013:20:38:27 +0000] [Client 19] No authentication data provided.
D [11/Jan/2013:20:38:27 +0000] [Client 19] 2.0 Get-Notifications 148
D [11/Jan/2013:20:38:27 +0000] Get-Notifications /
D [11/Jan/2013:20:38:27 +0000] cupsdIsAuthorized: requesting-user-name="pauline"
D [11/Jan/2013:20:38:27 +0000] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [11/Jan/2013:20:38:27 +0000] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [11/Jan/2013:20:38:27 +0000] [Client 21] POST / HTTP/1.1
D [11/Jan/2013:20:38:27 +0000] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [11/Jan/2013:20:38:27 +0000] [Client 21] No authentication data provided.
D [11/Jan/2013:20:38:27 +0000] [Client 21] 2.0 Get-Printer-Attributes 149
D [11/Jan/2013:20:38:27 +0000] Get-Printer-Attributes ipp://localhost/printers/Lexmark-2600-Series
D [11/Jan/2013:20:38:27 +0000] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/Lexmark-2600-Series) from localhost
D [11/Jan/2013:20:38:27 +0000] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [11/Jan/2013:20:38:27 +0000] [Client 19] HTTP_WAITING Closing on EOF
D [11/Jan/2013:20:38:27 +0000] [Client 19] Closing connection.
D [11/Jan/2013:20:38:27 +0000] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
D [11/Jan/2013:20:38:27 +0000] [Client 16] POST / HTTP/1.1
D [11/Jan/2013:20:38:27 +0000] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [11/Jan/2013:20:38:27 +0000] [Client 16] No authentication data provided.
D [11/Jan/2013:20:38:27 +0000] [Client 16] 2.0 Get-Notifications 150
D [11/Jan/2013:20:38:27 +0000] Get-Notifications /
D [11/Jan/2013:20:38:27 +0000] cupsdIsAuthorized: requesting-user-name="pauline"
D [11/Jan/2013:20:38:27 +0000] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [11/Jan/2013:20:38:27 +0000] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [11/Jan/2013:20:38:27 +0000] [Client 20] POST / HTTP/1.1
D [11/Jan/2013:20:38:27 +0000] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [11/Jan/2013:20:38:27 +0000] [Client 20] No authentication data provided.
D [11/Jan/2013:20:38:27 +0000] [Client 20] 2.0 CUPS-Get-Printers 151
D [11/Jan/2013:20:38:27 +0000] CUPS-Get-Printers
D [11/Jan/2013:20:38:27 +0000] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [11/Jan/2013:20:38:27 +0000] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [11/Jan/2013:20:38:27 +0000] [Client 20] POST / HTTP/1.1
D [11/Jan/2013:20:38:27 +0000] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [11/Jan/2013:20:38:27 +0000] [Client 20] No authentication data provided.
D [11/Jan/2013:20:38:27 +0000] [Client 20] 2.0 CUPS-Get-Classes 152
D [11/Jan/2013:20:38:27 +0000] CUPS-Get-Classes
D [11/Jan/2013:20:38:27 +0000] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [11/Jan/2013:20:38:27 +0000] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [11/Jan/2013:20:38:27 +0000] [Client 20] POST / HTTP/1.1
D [11/Jan/2013:20:38:27 +0000] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [11/Jan/2013:20:38:27 +0000] [Client 20] No authentication data provided.
D [11/Jan/2013:20:38:27 +0000] [Client 20] 2.0 CUPS-Get-Default 153
D [11/Jan/2013:20:38:27 +0000] CUPS-Get-Default
D [11/Jan/2013:20:38:27 +0000] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [11/Jan/2013:20:38:27 +0000] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [11/Jan/2013:20:38:28 +0000] [Job 36] Unloading...
D [11/Jan/2013:20:38:30 +0000] [Client 16] POST / HTTP/1.1
D [11/Jan/2013:20:38:30 +0000] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [11/Jan/2013:20:38:30 +0000] [Client 16] No authentication data provided.
D [11/Jan/2013:20:38:30 +0000] [Client 16] 2.0 Get-Job-Attributes 154
D [11/Jan/2013:20:38:30 +0000] Get-Job-Attributes ipp://localhost/jobs/36
D [11/Jan/2013:20:38:30 +0000] [Job 36] Loading attributes...
D [11/Jan/2013:20:38:30 +0000] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/36) from localhost
D [11/Jan/2013:20:38:30 +0000] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [11/Jan/2013:20:38:30 +0000] [Client 16] POST / HTTP/1.1
D [11/Jan/2013:20:38:30 +0000] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [11/Jan/2013:20:38:30 +0000] [Client 16] No authentication data provided.
D [11/Jan/2013:20:38:30 +0000] [Client 16] 2.0 Cancel-Subscription 155
D [11/Jan/2013:20:38:30 +0000] Cancel-Subscription /
D [11/Jan/2013:20:38:30 +0000] cupsdIsAuthorized: requesting-user-name="pauline"
D [11/Jan/2013:20:38:30 +0000] cupsdMarkDirty(-----S)
D [11/Jan/2013:20:38:30 +0000] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
D [11/Jan/2013:20:38:30 +0000] Returning IPP successful-ok for Cancel-Subscription (/) from localhost
D [11/Jan/2013:20:38:30 +0000] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [11/Jan/2013:20:38:30 +0000] [Client 16] GET /admin/conf/cupsd.conf HTTP/1.1
D [11/Jan/2013:20:38:30 +0000] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [11/Jan/2013:20:38:30 +0000] [Client 16] No authentication data provided.
D [11/Jan/2013:20:38:30 +0000] cupsdIsAuthorized: username=""
D [11/Jan/2013:20:38:30 +0000] [Client 16] WWW-Authenticate: Basic realm="CUPS", trc="y"
D [11/Jan/2013:20:38:30 +0000] [Client 16] Closing connection.
D [11/Jan/2013:20:38:30 +0000] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [11/Jan/2013:20:38:30 +0000] [Client 16] Accepted from localhost (Domain)
D [11/Jan/2013:20:38:30 +0000] [Client 16] GET /admin/conf/cupsd.conf HTTP/1.1
D [11/Jan/2013:20:38:30 +0000] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [11/Jan/2013:20:38:30 +0000] [Client 16] Authorized as pauline using PeerCred
D [11/Jan/2013:20:38:30 +0000] cupsdIsAuthorized: username="pauline"
D [11/Jan/2013:20:38:30 +0000] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [11/Jan/2013:20:38:30 +0000] [Client 19] Accepted from localhost (Domain)
D [11/Jan/2013:20:38:30 +0000] [Client 19] POST / HTTP/1.1
D [11/Jan/2013:20:38:30 +0000] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [11/Jan/2013:20:38:30 +0000] [Client 19] No authentication data provided.
D [11/Jan/2013:20:38:30 +0000] [Client 19] 2.0 CUPS-Get-Printers 1
D [11/Jan/2013:20:38:30 +0000] CUPS-Get-Printers
D [11/Jan/2013:20:38:30 +0000] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [11/Jan/2013:20:38:30 +0000] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [11/Jan/2013:20:38:30 +0000] [Client 16] GET /admin/conf/cupsd.conf HTTP/1.1
D [11/Jan/2013:20:38:30 +0000] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [11/Jan/2013:20:38:30 +0000] [Client 16] Authorized as pauline using PeerCred
D [11/Jan/2013:20:38:30 +0000] cupsdIsAuthorized: username="pauline"
D [11/Jan/2013:20:38:30 +0000] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [11/Jan/2013:20:38:30 +0000] [Client 16] GET /admin/conf/cupsd.conf HTTP/1.1
D [11/Jan/2013:20:38:30 +0000] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [11/Jan/2013:20:38:30 +0000] [Client 16] Authorized as pauline using PeerCred
D [11/Jan/2013:20:38:30 +0000] cupsdIsAuthorized: username="pauline"
D [11/Jan/2013:20:38:30 +0000] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [11/Jan/2013:20:38:30 +0000] [Client 16] PUT /admin/conf/cupsd.conf HTTP/1.1
D [11/Jan/2013:20:38:30 +0000] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [11/Jan/2013:20:38:30 +0000] [Client 16] Authorized as pauline using PeerCred
D [11/Jan/2013:20:38:30 +0000] cupsdIsAuthorized: username="pauline"
I [11/Jan/2013:20:38:30 +0000] Installing config file "/etc/cups/cupsd.conf"...
D [11/Jan/2013:20:38:31 +0000] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [11/Jan/2013:20:38:31 +0000] [Client 19] HTTP_WAITING Closing on EOF
D [11/Jan/2013:20:38:31 +0000] [Client 19] Closing connection.
D [11/Jan/2013:20:38:31 +0000] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
D [11/Jan/2013:20:38:31 +0000] [Client 18] Closing connection.
D [11/Jan/2013:20:38:31 +0000] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
D [11/Jan/2013:20:38:31 +0000] [Client 21] Closing connection.
D [11/Jan/2013:20:38:31 +0000] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
D [11/Jan/2013:20:38:31 +0000] [Client 20] Closing connection.
D [11/Jan/2013:20:38:31 +0000] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
D [11/Jan/2013:20:38:31 +0000] [Client 16] Closing connection.
D [11/Jan/2013:20:38:31 +0000] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
I [11/Jan/2013:20:38:31 +0000] Generating printcap /var/run/cups/printcap...
I [11/Jan/2013:20:38:31 +0000] Saving job.cache...
I [11/Jan/2013:20:38:31 +0000] Saving subscriptions.conf...
D [11/Jan/2013:20:38:31 +0000] cupsdSetBusyState: newbusy="Not busy", busy="Dirty files"
E [11/Jan/2013:20:38:31 +0000] Unknown directive SystemGroup on line 4 of /etc/cups/cupsd.conf.
E [11/Jan/2013:20:38:31 +0000] Unknown directive JobPrivateAccess on line 85 of /etc/cups/cupsd.conf.
E [11/Jan/2013:20:38:31 +0000] Unknown directive JobPrivateValues on line 86 of /etc/cups/cupsd.conf.
E [11/Jan/2013:20:38:31 +0000] Unknown directive SubscriptionPrivateAccess on line 87 of /etc/cups/cupsd.conf.
E [11/Jan/2013:20:38:31 +0000] Unknown directive SubscriptionPrivateValues on line 88 of /etc/cups/cupsd.conf.
W [11/Jan/2013:20:38:31 +0000] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'Lexmark-2600-Series-Gray..' already exists
W [11/Jan/2013:20:38:31 +0000] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'Lexmark-2600-Series-RGB..' already exists
W [11/Jan/2013:20:38:31 +0000] CreateDevice failed: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Lexmark-2600-Series' already exists
W [11/Jan/2013:20:38:31 +0000] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'Lexmark_2600_Series-Gray..' already exists
W [11/Jan/2013:20:38:31 +0000] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'Lexmark_2600_Series-RGB..' already exists
W [11/Jan/2013:20:38:31 +0000] CreateDevice failed: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Lexmark_2600_Series' already exists
```

What can I do?

---

