---
title: "“printing stopped” and “filter failed” - laser printer Dell 2150cdn - Ubuntu 18.04.2"
date: 2019-05-14
forum: General Help
---

### Post by janow on 2019-05-14
0

                     I know that other people had the same kind of problem but I couldn't find any solutions that worked for me.

  since an update of Ubuntu I can't print anymore... It keeps telling me "printing stopped" after a second and nothing happens.
  I tried to reinstall the driver folowing this method [https://www.rottenrei.be/blog//posts/2014-07-19-dell-2150cdn-color-under-ubuntu-14-04/](https://www.rottenrei.be/blog//posts/2014-07-19-dell-2150cdn-color-under-ubuntu-14-04/) but it still doesn't work. 


  Here is my /var/log/cups/error_log 

```
[14/May/2019:18:00:36 +0200] [Job 319] Job stopped due to filter errors; please consult the error_log file for details.
D [14/May/2019:18:00:36 +0200] [Job 319] The following messages were recorded from 18:00:36 to 18:00:36
D [14/May/2019:18:00:36 +0200] [Job 319] Applying default options...
D [14/May/2019:18:00:36 +0200] [Job 319] Adding start banner page "none".
D [14/May/2019:18:00:36 +0200] [Job 319] Adding end banner page "none".
D [14/May/2019:18:00:36 +0200] [Job 319] File of type application/pdf queued by "elodie".
D [14/May/2019:18:00:36 +0200] [Job 319] hold_until=0
D [14/May/2019:18:00:36 +0200] [Job 319] Queued on "2150cdn-Color-Printer-2" by "elodie".
D [14/May/2019:18:00:36 +0200] [Job 319] time-at-processing=1557849636
D [14/May/2019:18:00:36 +0200] [Job 319] 3 filters for job:
D [14/May/2019:18:00:36 +0200] [Job 319] pdftopdf (application/pdf to application/vnd.cups-pdf, cost 66)
D [14/May/2019:18:00:36 +0200] [Job 319] gstoraster (application/vnd.cups-pdf to application/vnd.cups-raster, cost 99)
D [14/May/2019:18:00:36 +0200] [Job 319] /usr/lib/cups/filter/Dell_2150_Color_Printer/DLM_MF (application/vnd.cups-raster to printer/2150cdn-Color-Printer-2, cost 0)
D [14/May/2019:18:00:36 +0200] [Job 319] job-sheets=none,none
D [14/May/2019:18:00:36 +0200] [Job 319] argv[0]="2150cdn-Color-Printer-2"
D [14/May/2019:18:00:36 +0200] [Job 319] argv[1]="319"
D [14/May/2019:18:00:36 +0200] [Job 319] argv[2]="elodie"
D [14/May/2019:18:00:36 +0200] [Job 319] argv[3]="Imprimer Nouveau document 1"
D [14/May/2019:18:00:36 +0200] [Job 319] argv[4]="1"
D [14/May/2019:18:00:36 +0200] [Job 319] argv[5]="DLColorDensityYellowMid=0 DLDocumentType=Normal DLColorDensityMagentaMid=0 DLColorMode=Color noDLSkip DLColorDensityMagentaHigh=0 Duplex=None DLColorDensityYellowHigh=0 number-up=1 PageSize=Custom.595.28x841.89 DLColorDensityBlackLow=0 DLScreen2=Auto noDLTurnPage InputSlot=AutoSelect DLColorDensityBlackHigh=0 DLColorDensityCyanLow=0 noDLTonerSaver DLColorDensityBlackMid=0 DLSubPaperSelection=Policy2 MediaType=Stationary DLColorDensityCyanMid=0 DLLetterHeadDuplexMode=DupAuto noDLTrapping noDLEdgeEnhance DLColorDensityCyanHigh=0 DLDigitalFilter=Off DLColorDensityYellowLow=0 DLColorDensityMagentaLow=0 job-uuid=urn:uuid:438c7d8e-2e44-305c-6408-52b474148453 job-originating-host-name=localhost date-time-at-creation= date-time-at-processing= time-at-creation=1557849636 time-at-processing=1557849636"
D [14/May/2019:18:00:36 +0200] [Job 319] argv[6]="/var/spool/cups/d00319-001"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[7]="CUPS_STATEDIR=/run/cups"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[8]="HOME=/var/spool/cups/tmp"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[10]="SERVER_ADMIN=root@elodie"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[11]="SOFTWARE=CUPS/2.2.7"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[13]="USER=root"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[14]="CUPS_MAX_MESSAGE=2047"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[16]="CUPS_ENCRYPTION=IfRequested"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[17]="IPP_PORT=631"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[18]="CHARSET=utf-8"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[19]="LANG=fr_FR.UTF-8"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[20]="PPD=/etc/cups/ppd/2150cdn-Color-Printer-2.ppd"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[21]="RIP_MAX_CACHE=128m"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[22]="CONTENT_TYPE=application/pdf"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[23]="DEVICE_URI=usb://Dell/2150cdn%20Color%20Printer?serial=VZG008554"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[24]="PRINTER_INFO=Dell 2150cdn Color Printer"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[25]="PRINTER_LOCATION="
D [14/May/2019:18:00:36 +0200] [Job 319] envp[26]="PRINTER=2150cdn-Color-Printer-2"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[27]="PRINTER_STATE_REASONS=none"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[28]="CUPS_FILETYPE=document"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[29]="FINAL_CONTENT_TYPE=application/vnd.cups-raster"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[30]="AUTH_I****"
D [14/May/2019:18:00:36 +0200] [Job 319] Started filter /usr/lib/cups/filter/pdftopdf (PID 9445)
D [14/May/2019:18:00:36 +0200] [Job 319] Started filter /usr/lib/cups/filter/gstoraster (PID 9446)
D [14/May/2019:18:00:36 +0200] [Job 319] Started filter /usr/lib/cups/filter/Dell_2150_Color_Printer/DLM_MF (PID 9447)
D [14/May/2019:18:00:36 +0200] [Job 319] Started backend /usr/lib/cups/backend/usb (PID 9449)
D [14/May/2019:18:00:36 +0200] [Job 319] pdftopdf: Last filter determined by the PPD: DLM_MF; FINAL_CONTENT_TYPE: application/vnd.cups-raster => pdftopdf will not log pages in page_log.
D [14/May/2019:18:00:36 +0200] [Job 319] OUTFORMAT=\"(null)\", so output format will be CUPS/PWG Raster
D [14/May/2019:18:00:36 +0200] [Job 319] PID 9445 (/usr/lib/cups/filter/pdftopdf) exited with no errors.
D [14/May/2019:18:00:36 +0200] [Job 319] Loading USB quirks from \"/usr/share/cups/usb\".
D [14/May/2019:18:00:36 +0200] [Job 319] Loaded 159 quirks.
D [14/May/2019:18:00:36 +0200] [Job 319] Printing on printer with URI: usb://Dell/2150cdn%20Color%20Printer?serial=VZG008554
D [14/May/2019:18:00:36 +0200] [Job 319] Color Manager: Calibration Mode/Off
D [14/May/2019:18:00:36 +0200] [Job 319] Calling FindDeviceById(cups-2150cdn-Color-Printer-2)
D [14/May/2019:18:00:36 +0200] [Job 319] Found device /org/freedesktop/ColorManager/devices/cups_2150cdn_Color_Printer_2
D [14/May/2019:18:00:36 +0200] [Job 319] Calling org.freedesktop.ColorManager.Device.Get(ProfilingInhibitors)
D [14/May/2019:18:00:36 +0200] [Job 319] !!!!! checkIfExecFilter : Condition ($DLSkip True eq) is false -> Filter DLM_SBP skipped. !!!!!
D [14/May/2019:18:00:36 +0200] [Job 319] Calling FindDeviceById(cups-2150cdn-Color-Printer-2)
D [14/May/2019:18:00:36 +0200] [Job 319] Found device /org/freedesktop/ColorManager/devices/cups_2150cdn_Color_Printer_2
D [14/May/2019:18:00:36 +0200] [Job 319] Calling GetProfileForQualifiers(CMYK.Stationary.600dpi...)
D [14/May/2019:18:00:36 +0200] [Job 319] Found profile /org/freedesktop/ColorManager/profiles/2150cdn_Color_Printer_2_CMYK__
D [14/May/2019:18:00:36 +0200] [Job 319] Calling org.freedesktop.ColorManager.Profile.Get(Filename)
D [14/May/2019:18:00:36 +0200] [Job 319] Use profile filename: \'\'
D [14/May/2019:18:00:36 +0200] [Job 319] Color Manager: ICC Profile: 
D [14/May/2019:18:00:36 +0200] [Job 319] Ghostscript using Any-Part-of-Pixel method to fill paths.
D [14/May/2019:18:00:36 +0200] [Job 319] Ghostscript command line: gs -dQUIET -dPARANOIDSAFER -dNOPAUSE -dBATCH -dNOINTERPOLATE -dNOMEDIAATTRS -dShowAcroForm -sstdout=%stderr -sOutputFile=%stdout -sDEVICE=cups -r600x600 -dDEVICEWIDTHPOINTS=595 -dDEVICEHEIGHTPOINTS=842 -dcupsBitsPerColor=8 -dcupsColorOrder=0 -dcupsColorSpace=1 -scupsPageSizeName=A4 -I/usr/share/cups/fonts -c \'<</.HWMargins[11.620000 11.620000 11.619995 11.619995] /Margins[0 0]>>setpagedevice\' -f -_
D [14/May/2019:18:00:36 +0200] [Job 319] envp[0]=\"CUPS_CACHEDIR=/var/cache/cups\"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[1]=\"CUPS_DATADIR=/usr/share/cups\"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[2]=\"CUPS_DOCROOT=/usr/share/cups/doc-root\"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[3]=\"CUPS_FONTPATH=/usr/share/cups/fonts\"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[4]=\"CUPS_REQUESTROOT=/var/spool/cups\"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[5]=\"CUPS_SERVERBIN=/usr/lib/cups\"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[6]=\"CUPS_SERVERROOT=/etc/cups\"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[7]=\"CUPS_STATEDIR=/run/cups\"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[8]=\"HOME=/var/spool/cups/tmp\"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[9]=\"PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin\"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[10]=\"SERVER_ADMIN=root@elodie\"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[11]=\"SOFTWARE=CUPS/2.2.7\"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[12]=\"USER=root\"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[13]=\"CUPS_MAX_MESSAGE=2047\"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[14]=\"CUPS_SERVER=/var/run/cups/cups.sock\"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[15]=\"CUPS_ENCRYPTION=IfRequested\"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[16]=\"IPP_PORT=631\"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[17]=\"CHARSET=utf-8\"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[18]=\"LANG=fr_FR.UTF-8\"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[19]=\"PPD=/etc/cups/ppd/2150cdn-Color-Printer-2.ppd\"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[20]=\"RIP_MAX_CACHE=128m\"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[21]=\"CONTENT_TYPE=application/pdf\"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[22]=\"DEVICE_URI=usb://Dell/2150cdn%20Color%20Printer?serial=VZG008554\"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[23]=\"PRINTER_INFO=Dell 2150cdn Color Printer\"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[24]=\"PRINTER_LOCATION=\"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[25]=\"PRINTER=2150cdn-Color-Printer-2\"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[26]=\"PRINTER_STATE_REASONS=none\"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[27]=\"CUPS_FILETYPE=document\"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[28]=\"FINAL_CONTENT_TYPE=application/vnd.cups-raster\"
D [14/May/2019:18:00:36 +0200] [Job 319] envp[29]=\"AUTH_INFO_REQUIRED=none\"
D [14/May/2019:18:00:36 +0200] [Job 319] !!!!! checkIfExecFilter : Condition ($Duplex DuplexNoTumble eq $DLTurnPage True eq or) is false -> Filter DLM_PR skipped. !!!!!
D [14/May/2019:18:00:36 +0200] [Job 319] libusb_get_device_list=15
D [14/May/2019:18:00:36 +0200] [Job 319] STATE: +connecting-to-device
D [14/May/2019:18:00:36 +0200] [Job 319] STATE: -connecting-to-device
D [14/May/2019:18:00:36 +0200] [Job 319] !!!!! checkIfExecFilter : Condition ($DLTrapping True eq $DLColorMode Color eq and) is false -> Filter DLM_TP skipped. !!!!!
D [14/May/2019:18:00:36 +0200] [Job 319] Printer found with device ID: MFG:Dell;CMD:PJL,PCLXL,PCL;MDL:2150cdn Color Printer;DES:Dell 2150cdn Color Printer;CLS:PRINTER;STS:AAAAugAAAAAAAAAAAAgAAxkDKAM8AwUGZANkA2QDQBoAAAAAsIIAAAAAAAAAAAAA4QAAEQAAAAAQ\r
D [14/May/2019:18:00:36 +0200] [Job 319] DA==; Device URI: usb://Dell/2150cdn%20Color%20Printer?serial=VZG008554
D [14/May/2019:18:00:36 +0200] [Job 319] Device protocol: 2
D [14/May/2019:18:00:36 +0200] [Job 319] Sending data to printer.
D [14/May/2019:18:00:36 +0200] [Job 319] Set job-printer-state-message to "Sending data to printer.", current level=INFO
D [14/May/2019:18:00:36 +0200] [Job 319] !!!!! checkIfExecFilter : Condition ($DLEdgeEnhance True eq) is false -> Filter DLM_EE skipped. !!!!!
D [14/May/2019:18:00:36 +0200] [Job 319] !!!!! checkIfExecFilter : Condition ($DLDigitalFilter Off ne) is false -> Filter DLM_DF skipped. !!!!!
D [14/May/2019:18:00:36 +0200] [Job 319] 2150cdn-Color-Printer-2: error while loading shared libraries: libcupsimage.so.2: cannot open shared object file: No such file or directory
D [14/May/2019:18:00:36 +0200] [Job 319] PID 9447 (/usr/lib/cups/filter/Dell_2150_Color_Printer/DLM_MF) stopped with status 1.
D [14/May/2019:18:00:36 +0200] [Job 319] Hint: Try setting the LogLevel to "debug" to find out more.
D [14/May/2019:18:00:36 +0200] [Job 319] Sent 0 bytes...
D [14/May/2019:18:00:36 +0200] [Job 319] Start rendering...
D [14/May/2019:18:00:36 +0200] [Job 319] Processing page 1...
D [14/May/2019:18:00:36 +0200] [Job 319] Error: /ioerror in --showpage--
D [14/May/2019:18:00:36 +0200] [Job 319] Operand stack:
D [14/May/2019:18:00:36 +0200] [Job 319] true   (/tmp/gs_c4kLp6)   --nostringval--   1   true
D [14/May/2019:18:00:36 +0200] [Job 319] Execution stack:
D [14/May/2019:18:00:36 +0200] [Job 319] %interp_exit   .runexec2   --nostringval--   showpage   --nostringval--   2   %stopped_push   --nostringval--   showpage   showpage   false   1   %stopped_push   2045   2   3   %oparray_pop   2044   2   3   %oparray_pop   2025   2   3   %oparray_pop   showpage   2026   4   3   %oparray_pop   showpage   showpage   2   1   1   showpage   %for_pos_int_continue   2029   4   7   %oparray_pop   showpage   showpage   1890   3   9   %oparray_pop   showpage   showpage
D [14/May/2019:18:00:36 +0200] [Job 319] Dictionary stack:
D [14/May/2019:18:00:36 +0200] [Job 319] --dict:968/1684(ro)(G)--   --dict:1/20(G)--   --dict:82/200(L)--   --dict:82/200(L)--   --dict:133/256(ro)(G)--   --dict:311/450(ro)(G)--   --dict:32/32(L)--   --dict:6/9(L)--   --dict:6/20(L)--
D [14/May/2019:18:00:36 +0200] [Job 319] Current allocation mode is local
D [14/May/2019:18:00:36 +0200] [Job 319] Last OS error: Broken pipe
D [14/May/2019:18:00:36 +0200] [Job 319] GPL Ghostscript 9.26: Unrecoverable error, exit code 1
D [14/May/2019:18:00:36 +0200] [Job 319] Rendering completed
D [14/May/2019:18:00:36 +0200] [Job 319] Waiting for read thread to exit...
D [14/May/2019:18:00:36 +0200] [Job 319] PID 9446 (/usr/lib/cups/filter/gstoraster) stopped with status 1.
D [14/May/2019:18:00:36 +0200] [Job 319] Hint: Try setting the LogLevel to "debug" to find out more.
D [14/May/2019:18:00:36 +0200] [Job 319] PID 9449 (/usr/lib/cups/backend/usb) exited with no errors.
D [14/May/2019:18:00:36 +0200] [Job 319] End of messages
D [14/May/2019:18:00:36 +0200] [Job 319] printer-state=3(idle)
D [14/May/2019:18:00:36 +0200] [Job 319] printer-state-message="Rendering completed"
D [14/May/2019:18:00:36 +0200] [Job 319] printer-state-reasons=none
E [14/May/2019:18:07:50 +0200] [cups-deviced] PID 9591 (gutenprint52+usb) stopped 
```

Thanks in advance for your help !

---

