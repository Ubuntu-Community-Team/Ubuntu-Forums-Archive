---
title: "Lexmark X2650 print driver fails, possibly selinux"
date: 2013-02-07
forum: General Help
---

### Post by afrodeity on 2013-02-07
```

E [07/Feb/2013:07:46:45 +0200] Unknown directive SystemGroup on line 16 of /etc/cups/cupsd.conf.
E [07/Feb/2013:07:46:46 +0200] 2600-Series: File "/usr/local/lexmark/lxk08/bin/printdriver" has insecure permissions (0100775/uid=0/gid=2).
W [07/Feb/2013:07:46:46 +0200] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id '2600-Series-Gray..' already exists
W [07/Feb/2013:07:46:46 +0200] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id '2600-Series-RGB..' already exists
W [07/Feb/2013:07:46:46 +0200] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-2600-Series' already exists
E [07/Feb/2013:18:10:00 +0200] [CGI] File "/usr/lib/cups/backend/lxkusb" has insecure permissions (0100775/uid=0/gid=2).
E [07/Feb/2013:18:10:26 +0200] PID 32172 (/usr/local/lexmark/lxk08/bin/printdriver) crashed on signal 6.
E [07/Feb/2013:18:10:34 +0200] [Job 8] Job stopped due to filter errors; please consult the error_log file for details.
D [07/Feb/2013:18:10:34 +0200] [Job 8] The following messages were recorded from 18:10:21 to 18:10:33
D [07/Feb/2013:18:10:34 +0200] [Job 8] Adding start banner page "none".
D [07/Feb/2013:18:10:34 +0200] [Job 8] Adding end banner page "none".
D [07/Feb/2013:18:10:34 +0200] [Job 8] File of type application/vnd.cups-pdf-banner queued by "afrodeity".
D [07/Feb/2013:18:10:34 +0200] [Job 8] hold_until=0
D [07/Feb/2013:18:10:34 +0200] [Job 8] Queued on "2600-Series" by "afrodeity".
D [07/Feb/2013:18:10:34 +0200] [Job 8] job-sheets=none,none
D [07/Feb/2013:18:10:34 +0200] [Job 8] argv[0]="2600-Series"
D [07/Feb/2013:18:10:34 +0200] [Job 8] argv[1]="8"
D [07/Feb/2013:18:10:34 +0200] [Job 8] argv[2]="afrodeity"
D [07/Feb/2013:18:10:34 +0200] [Job 8] argv[3]="Test page"
D [07/Feb/2013:18:10:34 +0200] [Job 8] argv[4]="1"
D [07/Feb/2013:18:10:34 +0200] [Job 8] argv[5]="job-uuid=urn:uuid:41bec4e2-e282-31c3-79c5-7ddf5c713a64 job-originating-host-name=localhost time-at-creation=1360253421 time-at-processing=1360253421"
D [07/Feb/2013:18:10:34 +0200] [Job 8] argv[6]="/var/spool/cups/d00008-001"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[8]="HOME=/var/spool/cups/tmp"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[10]="SERVER_ADMIN=root@afrodeity-desktop"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[11]="SOFTWARE=CUPS/1.5.3"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[13]="USER=root"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[16]="IPP_PORT=631"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[17]="CHARSET=utf-8"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[18]="LANG=en_US.UTF-8"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[19]="PPD=/etc/cups/ppd/2600-Series.ppd"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[20]="RIP_MAX_CACHE=128m"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[21]="CONTENT_TYPE=application/vnd.cups-pdf-banner"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[22]="DEVICE_URI=usb://Lexmark/2600%20Series?serial=3001960HB000863&interface=1"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[23]="PRINTER_INFO=Lexmark 2600 Series"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[24]="PRINTER_LOCATION=afrodeity-desktop"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[25]="PRINTER=2600-Series"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[26]="PRINTER_STATE_REASONS=none"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[27]="CUPS_FILETYPE=document"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[28]="FINAL_CONTENT_TYPE=printer/2600-Series"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[29]="AUTH_I****"
D [07/Feb/2013:18:10:34 +0200] [Job 8] Started filter /usr/lib/cups/filter/bannertopdf (PID 32169)
D [07/Feb/2013:18:10:34 +0200] [Job 8] Started filter /usr/lib/cups/filter/pdftopdf (PID 32170)
D [07/Feb/2013:18:10:34 +0200] [Job 8] Started filter /usr/lib/cups/filter/gstoraster (PID 32171)
D [07/Feb/2013:18:10:34 +0200] [Job 8] Started filter /usr/local/lexmark/lxk08/bin/printdriver (PID 32172)
D [07/Feb/2013:18:10:34 +0200] [Job 8] Started backend /usr/lib/cups/backend/usb (PID 32173)
D [07/Feb/2013:18:10:34 +0200] [Job 8] Printing on printer with URI: usb://Lexmark/2600%20Series?serial=3001960HB000863&interface=1
D [07/Feb/2013:18:10:34 +0200] [Job 8] libusb_get_device_list=11
D [07/Feb/2013:18:10:34 +0200] [Job 8] STATE: +connecting-to-device
D [07/Feb/2013:18:10:34 +0200] [Job 8] STATE: -connecting-to-device
D [07/Feb/2013:18:10:34 +0200] [Job 8] Printer found with device ID: MFG:Lexmark;CMD:CPDNPA004;MODEL: 2600 Series;CLASS:Printer;DES:Lexmark 2600 Series; Device URI: usb://Lexmark/2600%20Series?serial=3001960HB000863&interface=1
D [07/Feb/2013:18:10:34 +0200] [Job 8] Device protocol: 2
D [07/Feb/2013:18:10:34 +0200] [Job 8] Sending data to printer.
D [07/Feb/2013:18:10:34 +0200] [Job 8] Set job-printer-state-message to "Sending data to printer.", current level=INFO
D [07/Feb/2013:18:10:34 +0200] [Job 8] Read 17 bytes of back-channel data...
D [07/Feb/2013:18:10:34 +0200] [Job 8] PPD uses qualifier 'Color.Plain.'
D [07/Feb/2013:18:10:34 +0200] [Job 8] Calling FindDeviceById(2600-Series)
D [07/Feb/2013:18:10:34 +0200] [Job 8] Failed to send: org.freedesktop.ColorManager.Failed:device id '2600-Series' does not exists
D [07/Feb/2013:18:10:34 +0200] [Job 8] Failed to get profile filename!
D [07/Feb/2013:18:10:34 +0200] [Job 8] no profiles specified in PPD
D [07/Feb/2013:18:10:34 +0200] [Job 8] Set job-printer-state-message to "no profiles specified in PPD", current level=INFO
D [07/Feb/2013:18:10:34 +0200] [Job 8] Ghostscript command line: /usr/bin/gs -dQUIET -dPARANOIDSAFER -dNOPAUSE -dBATCH -dNOINTERPOLATE -sDEVICE=cups -sstdout=%stderr -sOutputFile=%stdout -sOutputType=2 -r600x600 -dDEVICEWIDTHPOINTS=595 -dDEVICEHEIGHTPOINTS=841 -dcupsMediaType=1 -dcupsBitsPerColor=8 -dcupsColorOrder=0 -dcupsColorSpace=1 -dcupsCompression=8 -dcupsRowStep=1 -scupsPageSizeName=A4 -I/usr/share/cups/fonts -c -f -_
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[8]="HOME=/var/spool/cups/tmp"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[10]="SERVER_ADMIN=root@afrodeity-desktop"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[11]="SOFTWARE=CUPS/1.5.3"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[12]="USER=root"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[13]="CUPS_SERVER=/var/run/cups/cups.sock"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[14]="CUPS_ENCRYPTION=IfRequested"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[15]="IPP_PORT=631"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[16]="CHARSET=utf-8"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[17]="LANG=en_US.UTF-8"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[18]="PPD=/etc/cups/ppd/2600-Series.ppd"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[19]="RIP_MAX_CACHE=128m"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[20]="CONTENT_TYPE=application/vnd.cups-pdf-banner"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[21]="DEVICE_URI=usb://Lexmark/2600%20Series?serial=3001960HB000863&interface=1"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[22]="PRINTER_INFO=Lexmark 2600 Series"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[23]="PRINTER_LOCATION=afrodeity-desktop"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[24]="PRINTER=2600-Series"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[25]="PRINTER_STATE_REASONS=none"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[26]="CUPS_FILETYPE=document"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[27]="FINAL_CONTENT_TYPE=printer/2600-Series"
D [07/Feb/2013:18:10:34 +0200] [Job 8] envp[28]="AUTH_INFO_REQUIRED=none"
D [07/Feb/2013:18:10:34 +0200] [Job 8] Start rendering...
D [07/Feb/2013:18:10:34 +0200] [Job 8] Set job-printer-state-message to "Start rendering...", current level=INFO
D [07/Feb/2013:18:10:34 +0200] [Job 8] Processing page 1...
D [07/Feb/2013:18:10:34 +0200] [Job 8] Set job-printer-state-message to "Processing page 1...", current level=INFO
D [07/Feb/2013:18:10:34 +0200] [Job 8] Read 8 bytes of print data...
D [07/Feb/2013:18:10:34 +0200] [Job 8] Read 8 bytes of back-channel data...
D [07/Feb/2013:18:10:34 +0200] [Job 8] Wrote 8 bytes of print data...
D [07/Feb/2013:18:10:34 +0200] [Job 8] Read 15 bytes of print data...
D [07/Feb/2013:18:10:34 +0200] [Job 8] Wrote 15 bytes of print data...
D [07/Feb/2013:18:10:34 +0200] [Job 8] Read 15 bytes of back-channel data...
D [07/Feb/2013:18:10:34 +0200] [Job 8] Read 8 bytes of print data...
D [07/Feb/2013:18:10:34 +0200] [Job 8] Wrote 8 bytes of print data...
D [07/Feb/2013:18:10:34 +0200] [Job 8] Read 9 bytes of back-channel data...
D [07/Feb/2013:18:10:34 +0200] [Job 8] Read 8 bytes of print data...
D [07/Feb/2013:18:10:34 +0200] [Job 8] Wrote 8 bytes of print data...
D [07/Feb/2013:18:10:34 +0200] [Job 8] Read 8 bytes of back-channel data...
D [07/Feb/2013:18:10:34 +0200] [Job 8] Read 8 bytes of print data...
D [07/Feb/2013:18:10:34 +0200] [Job 8] Wrote 8 bytes of print data...
D [07/Feb/2013:18:10:34 +0200] [Job 8] Read 512 bytes of back-channel data...
D [07/Feb/2013:18:10:34 +0200] [Job 8] Read 37 bytes of back-channel data...
D [07/Feb/2013:18:10:34 +0200] [Job 8] 2600-Series: malloc.c:3064: __libc_realloc: Assertion `!newp || ((((mchunkptr)((char*)(newp) - 2*(sizeof(size_t)))))->size & 0x2) || ar_ptr == (((((mchunkptr)((char*)(newp) - 2*(sizeof(size_t)))))->size & 0x4) ? ((heap_info *)((unsigned long)(((mchunkptr)((char*)(newp) - 2*(sizeof(size_t))))) & ~((2 * (512 * 1024))-1)))->ar_ptr : &main_arena)' failed.
D [07/Feb/2013:18:10:34 +0200] [Job 8] Sent 47 bytes...
D [07/Feb/2013:18:10:34 +0200] [Job 8] Waiting for read thread to exit...
D [07/Feb/2013:18:10:34 +0200] [Job 8] Read thread still active, aborting the pending read...
D [07/Feb/2013:18:10:34 +0200] [Job 8] End of messages
D [07/Feb/2013:18:10:34 +0200] [Job 8] printer-state=3(idle)
D [07/Feb/2013:18:10:34 +0200] [Job 8] printer-state-message="/usr/local/lexmark/lxk08/bin/printdriver failed"
D [07/Feb/2013:18:10:34 +0200] [Job 8] printer-state-reasons=none
E [07/Feb/2013:18:14:54 +0200] PID 2146 (/usr/local/lexmark/lxk08/bin/printdriver) crashed on signal 11.
E [07/Feb/2013:18:15:02 +0200] [Job 9] Job stopped due to filter errors; please consult the error_log file for details.
D [07/Feb/2013:18:15:02 +0200] [Job 9] The following messages were recorded from 18:14:50 to 18:15:01
D [07/Feb/2013:18:15:02 +0200] [Job 9] Adding start banner page "none".
D [07/Feb/2013:18:15:02 +0200] [Job 9] Adding end banner page "none".
D [07/Feb/2013:18:15:02 +0200] [Job 9] File of type application/vnd.cups-pdf-banner queued by "afrodeity".
D [07/Feb/2013:18:15:02 +0200] [Job 9] hold_until=0
D [07/Feb/2013:18:15:02 +0200] [Job 9] Queued on "2600-Series" by "afrodeity".
D [07/Feb/2013:18:15:02 +0200] [Job 9] job-sheets=none,none
D [07/Feb/2013:18:15:02 +0200] [Job 9] argv[0]="2600-Series"
D [07/Feb/2013:18:15:02 +0200] [Job 9] argv[1]="9"
D [07/Feb/2013:18:15:02 +0200] [Job 9] argv[2]="afrodeity"
D [07/Feb/2013:18:15:02 +0200] [Job 9] argv[3]="Test page"
D [07/Feb/2013:18:15:02 +0200] [Job 9] argv[4]="1"
D [07/Feb/2013:18:15:02 +0200] [Job 9] argv[5]="job-uuid=urn:uuid:4d060ccd-9a40-3299-7655-a1aa95e5b3f3 job-originating-host-name=localhost time-at-creation=1360253690 time-at-processing=1360253690"
D [07/Feb/2013:18:15:02 +0200] [Job 9] argv[6]="/var/spool/cups/d00009-001"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[8]="HOME=/var/spool/cups/tmp"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[10]="SERVER_ADMIN=root@afrodeity-desktop"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[11]="SOFTWARE=CUPS/1.5.3"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[13]="USER=root"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[16]="IPP_PORT=631"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[17]="CHARSET=utf-8"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[18]="LANG=en_US.UTF-8"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[19]="PPD=/etc/cups/ppd/2600-Series.ppd"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[20]="RIP_MAX_CACHE=128m"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[21]="CONTENT_TYPE=application/vnd.cups-pdf-banner"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[22]="DEVICE_URI=usb://Lexmark/2600%20Series?serial=3001960HB000863&interface=1"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[23]="PRINTER_INFO=Lexmark 2600 Series"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[24]="PRINTER_LOCATION=afrodeity-desktop"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[25]="PRINTER=2600-Series"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[26]="PRINTER_STATE_REASONS=none"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[27]="CUPS_FILETYPE=document"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[28]="FINAL_CONTENT_TYPE=printer/2600-Series"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[29]="AUTH_I****"
D [07/Feb/2013:18:15:02 +0200] [Job 9] Started filter /usr/lib/cups/filter/bannertopdf (PID 2143)
D [07/Feb/2013:18:15:02 +0200] [Job 9] Started filter /usr/lib/cups/filter/pdftopdf (PID 2144)
D [07/Feb/2013:18:15:02 +0200] [Job 9] Started filter /usr/lib/cups/filter/gstoraster (PID 2145)
D [07/Feb/2013:18:15:02 +0200] [Job 9] Started filter /usr/local/lexmark/lxk08/bin/printdriver (PID 2146)
D [07/Feb/2013:18:15:02 +0200] [Job 9] Started backend /usr/lib/cups/backend/usb (PID 2147)
D [07/Feb/2013:18:15:02 +0200] [Job 9] Printing on printer with URI: usb://Lexmark/2600%20Series?serial=3001960HB000863&interface=1
D [07/Feb/2013:18:15:02 +0200] [Job 9] libusb_get_device_list=11
D [07/Feb/2013:18:15:02 +0200] [Job 9] STATE: +connecting-to-device
D [07/Feb/2013:18:15:02 +0200] [Job 9] STATE: -connecting-to-device
D [07/Feb/2013:18:15:02 +0200] [Job 9] Printer found with device ID: MFG:Lexmark;CMD:CPDNPA004;MODEL: 2600 Series;CLASS:Printer;DES:Lexmark 2600 Series; Device URI: usb://Lexmark/2600%20Series?serial=3001960HB000863&interface=1
D [07/Feb/2013:18:15:02 +0200] [Job 9] Device protocol: 2
D [07/Feb/2013:18:15:02 +0200] [Job 9] Sending data to printer.
D [07/Feb/2013:18:15:02 +0200] [Job 9] Set job-printer-state-message to "Sending data to printer.", current level=INFO
D [07/Feb/2013:18:15:02 +0200] [Job 9] PPD uses qualifier 'Color.Plain.'
D [07/Feb/2013:18:15:02 +0200] [Job 9] Calling FindDeviceById(2600-Series)
D [07/Feb/2013:18:15:02 +0200] [Job 9] Failed to send: org.freedesktop.ColorManager.Failed:device id '2600-Series' does not exists
D [07/Feb/2013:18:15:02 +0200] [Job 9] Failed to get profile filename!
D [07/Feb/2013:18:15:02 +0200] [Job 9] no profiles specified in PPD
D [07/Feb/2013:18:15:02 +0200] [Job 9] Set job-printer-state-message to "no profiles specified in PPD", current level=INFO
D [07/Feb/2013:18:15:02 +0200] [Job 9] Ghostscript command line: /usr/bin/gs -dQUIET -dPARANOIDSAFER -dNOPAUSE -dBATCH -dNOINTERPOLATE -sDEVICE=cups -sstdout=%stderr -sOutputFile=%stdout -sOutputType=2 -r600x600 -dDEVICEWIDTHPOINTS=595 -dDEVICEHEIGHTPOINTS=841 -dcupsMediaType=1 -dcupsBitsPerColor=8 -dcupsColorOrder=0 -dcupsColorSpace=1 -dcupsCompression=8 -dcupsRowStep=1 -scupsPageSizeName=A4 -I/usr/share/cups/fonts -c -f -_
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[8]="HOME=/var/spool/cups/tmp"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[10]="SERVER_ADMIN=root@afrodeity-desktop"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[11]="SOFTWARE=CUPS/1.5.3"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[12]="USER=root"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[13]="CUPS_SERVER=/var/run/cups/cups.sock"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[14]="CUPS_ENCRYPTION=IfRequested"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[15]="IPP_PORT=631"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[16]="CHARSET=utf-8"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[17]="LANG=en_US.UTF-8"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[18]="PPD=/etc/cups/ppd/2600-Series.ppd"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[19]="RIP_MAX_CACHE=128m"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[20]="CONTENT_TYPE=application/vnd.cups-pdf-banner"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[21]="DEVICE_URI=usb://Lexmark/2600%20Series?serial=3001960HB000863&interface=1"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[22]="PRINTER_INFO=Lexmark 2600 Series"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[23]="PRINTER_LOCATION=afrodeity-desktop"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[24]="PRINTER=2600-Series"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[25]="PRINTER_STATE_REASONS=none"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[26]="CUPS_FILETYPE=document"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[27]="FINAL_CONTENT_TYPE=printer/2600-Series"
D [07/Feb/2013:18:15:02 +0200] [Job 9] envp[28]="AUTH_INFO_REQUIRED=none"
D [07/Feb/2013:18:15:02 +0200] [Job 9] Start rendering...
D [07/Feb/2013:18:15:02 +0200] [Job 9] Set job-printer-state-message to "Start rendering...", current level=INFO
D [07/Feb/2013:18:15:02 +0200] [Job 9] Processing page 1...
D [07/Feb/2013:18:15:02 +0200] [Job 9] Set job-printer-state-message to "Processing page 1...", current level=INFO
D [07/Feb/2013:18:15:02 +0200] [Job 9] Read 8 bytes of print data...
D [07/Feb/2013:18:15:02 +0200] [Job 9] Wrote 8 bytes of print data...
D [07/Feb/2013:18:15:02 +0200] [Job 9] Read 8 bytes of back-channel data...
D [07/Feb/2013:18:15:02 +0200] [Job 9] Read 15 bytes of print data...
D [07/Feb/2013:18:15:02 +0200] [Job 9] Wrote 15 bytes of print data...
D [07/Feb/2013:18:15:02 +0200] [Job 9] Read 15 bytes of back-channel data...
D [07/Feb/2013:18:15:02 +0200] [Job 9] Read 8 bytes of print data...
D [07/Feb/2013:18:15:02 +0200] [Job 9] Wrote 8 bytes of print data...
D [07/Feb/2013:18:15:02 +0200] [Job 9] Read 9 bytes of back-channel data...
D [07/Feb/2013:18:15:02 +0200] [Job 9] Read 8 bytes of print data...
D [07/Feb/2013:18:15:02 +0200] [Job 9] Wrote 8 bytes of print data...
D [07/Feb/2013:18:15:02 +0200] [Job 9] Read 8 bytes of back-channel data...
D [07/Feb/2013:18:15:02 +0200] [Job 9] Read 8 bytes of print data...
D [07/Feb/2013:18:15:02 +0200] [Job 9] Wrote 8 bytes of print data...
D [07/Feb/2013:18:15:02 +0200] [Job 9] Read 512 bytes of back-channel data...
D [07/Feb/2013:18:15:02 +0200] [Job 9] Read 37 bytes of back-channel data...
D [07/Feb/2013:18:15:02 +0200] [Job 9] Sent 47 bytes...
D [07/Feb/2013:18:15:02 +0200] [Job 9] Waiting for read thread to exit...
D [07/Feb/2013:18:15:02 +0200] [Job 9] Read thread still active, aborting the pending read...
D [07/Feb/2013:18:15:02 +0200] [Job 9] End of messages
D [07/Feb/2013:18:15:02 +0200] [Job 9] printer-state=3(idle)
D [07/Feb/2013:18:15:02 +0200] [Job 9] printer-state-message="/usr/local/lexmark/lxk08/bin/printdriver failed"
D [07/Feb/2013:18:15:02 +0200] [Job 9] printer-state-reasons=none
E [07/Feb/2013:18:20:03 +0200] [Job 9] Stopping unresponsive job!

```

I've tried fixing permissions:

```

sudo service cups stop

chmod 755 /usr/lib/cups/backend/lxkusb

chmod 755 /usr/local/lexmark/lxk08/bin/printdriver

cups service restart

```

but printer driver crashes with error 11

I found this [link]("http://forums.fedoraforum.org/archive/index.php/t-257176.html") but there issues with context as in [here]("ww.linuxquestions.org/questions/linux-general-1/chcon-cant-apply-partial-context-to-unlabeled-file-371977/")

So trouble running this

```

chcon -t texrel_shlib_t /usr/lexinkjet/lxk08/lib/libprinterdictionary.so
chcon -t texrel_shlib_t /usr/lexinkjet/lxk08/lib/libuiocli.so
chcon -t texrel_shlib_t /usr/lexinkjet/lxk08/lib/libnpa407.so
chcon -t texrel_shlib_t /usr/lexinkjet/lxk08/lib/libhdctransport.so

```

chcon: can't apply partial context to unlabeled file...

Any idea what the correct command would be?

This [posting ]("http://askubuntu.com/questions/120968/how-do-i-get-a-lexmark-x2600-printer-working")is useful, tried but still failed:


```
sudo modprobe usblp
sudo chown -Rh root:root /usr/local/lexmark
sudo chown -Rh root:root /usr/lib/cups
/etc/init.d/cups restart

```
gedit /etc/apparmor.d/usr.sbin.cupsd

Find:

# FIXME: no policy ATM for hplip and Brother drivers
/usr/bin/hpijs Ux,
/usr/Brother/** Ux,

Copy and Past after this:

/usr/local/lexmark/lxk08/bin/printdriver Ux,
/usr/lib/cups/backend/lxkusb Ux,
/usr/local/lexmark/lxk08/bin/lxkusb Ux,

Save the file

/etc/init.d/apparmor restart

No use, still stumped.

---

