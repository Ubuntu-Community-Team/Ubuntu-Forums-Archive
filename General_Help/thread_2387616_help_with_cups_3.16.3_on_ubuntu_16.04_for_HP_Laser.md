---
title: "help with cups 3.16.3 on ubuntu 16.04 for HP_LaserJet_Professional_P1102w"
date: 2018-03-21
forum: General Help
---

### Post by Hodor on 2018-03-21
I'm trying to set up a print server so that hopefully my daughters (who love macs) can print some stuff, currently they have to go on a windows computer for that, it's a hassle.
After running hp-setup to install drivers for above printer (attached via usb, custom built 64 bit), and installing above printer via web interface to CUPS, get an error message on attempting test print:
[COLOR=#000000][FONT=&amp]stopped [/FONT][/COLOR][I]"Filter failed".
Some output from the error_log
[/I]```
D [21/Mar/2018:22:28:21 +1100] [Job 17] envp[0]=\"CUPS_CACHEDIR=/var/cache/cups\"
D [21/Mar/2018:22:28:21 +1100] [Job 17] envp[1]=\"CUPS_DATADIR=/usr/share/cups\"
D [21/Mar/2018:22:28:21 +1100] [Job 17] envp[2]=\"CUPS_DOCROOT=/usr/share/cups/doc-root\"
D [21/Mar/2018:22:28:21 +1100] [Job 17] envp[3]=\"CUPS_FONTPATH=/usr/share/cups/fonts\"
D [21/Mar/2018:22:28:21 +1100] [Job 17] envp[4]=\"CUPS_REQUESTROOT=/var/spool/cups\"
D [21/Mar/2018:22:28:21 +1100] [Job 17] envp[5]=\"CUPS_SERVERBIN=/usr/lib/cups\"
D [21/Mar/2018:22:28:21 +1100] [Job 17] envp[6]=\"CUPS_SERVERROOT=/etc/cups\"
D [21/Mar/2018:22:28:21 +1100] [Job 17] envp[7]=\"CUPS_STATEDIR=/var/run/cups\"
D [21/Mar/2018:22:28:21 +1100] [Job 17] envp[8]=\"HOME=/var/spool/cups/tmp\"
D [21/Mar/2018:22:28:21 +1100] [Job 17] envp[9]=\"PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin\"
D [21/Mar/2018:22:28:21 +1100] [Job 17] envp[10]=\"SERVER_ADMIN=root@x-desktop\"
D [21/Mar/2018:22:28:21 +1100] [Job 17] envp[11]=\"SOFTWARE=CUPS/2.1.3\"
D [21/Mar/2018:22:28:21 +1100] [Job 17] envp[12]=\"USER=root\"
D [21/Mar/2018:22:28:21 +1100] [Job 17] envp[13]=\"CUPS_MAX_MESSAGE=2047\"
D [21/Mar/2018:22:28:21 +1100] [Job 17] envp[14]=\"CUPS_SERVER=/var/run/cups/cups.sock\"
D [21/Mar/2018:22:28:21 +1100] [Job 17] envp[15]=\"CUPS_ENCRYPTION=IfRequested\"
D [21/Mar/2018:22:28:21 +1100] [Job 17] envp[16]=\"IPP_PORT=631\"
D [21/Mar/2018:22:28:21 +1100] [Job 17] envp[17]=\"CHARSET=utf-8\"
D [21/Mar/2018:22:28:21 +1100] [Job 17] envp[18]=\"LANG=en_GB.UTF-8\"
D [21/Mar/2018:22:28:21 +1100] [Job 17] envp[19]=\"PPD=/etc/cups/ppd/HP_LaserJet_Professional_P1102w.ppd\"
D [21/Mar/2018:22:28:21 +1100] [Job 17] envp[20]=\"RIP_MAX_CACHE=128m\"
D [21/Mar/2018:22:28:21 +1100] [Job 17] envp[21]=\"CONTENT_TYPE=application/vnd.cups-pdf-banner\"
D [21/Mar/2018:22:28:21 +1100] [Job 17] envp[22]=\"DEVICE_URI=usb://HP/LaserJet%20Professional%20P1102w?serial=000000000Q932P7EPR1a\"
D [21/Mar/2018:22:28:21 +1100] [Job 17] envp[23]=\"PRINTER_INFO=HP LaserJet Professional P1102w\"
D [21/Mar/2018:22:28:21 +1100] [Job 17] envp[24]=\"PRINTER_LOCATION=\"
D [21/Mar/2018:22:28:21 +1100] [Job 17] envp[25]=\"PRINTER=HP_LaserJet_Professional_P1102w\"
D [21/Mar/2018:22:28:21 +1100] [Job 17] envp[26]=\"PRINTER_STATE_REASONS=hplip.plugin-error\"
D [21/Mar/2018:22:28:21 +1100] [Job 17] envp[27]=\"CUPS_FILETYPE=document\"
D [21/Mar/2018:22:28:21 +1100] [Job 17] envp[28]=\"FINAL_CONTENT_TYPE=application/vnd.cups-raster\"
D [21/Mar/2018:22:28:21 +1100] [Job 17] envp[29]=\"AUTH_INFO_REQUIRED=none\"
D [21/Mar/2018:22:28:21 +1100] [Job 17] Start rendering...
D [21/Mar/2018:22:28:21 +1100] [Job 17] Set job-printer-state-message to "Start rendering...", current level=INFO
D [21/Mar/2018:22:28:21 +1100] [Job 17] Processing page 1...
D [21/Mar/2018:22:28:21 +1100] [Job 17] Set job-printer-state-message to "Processing page 1...", current level=INFO
D [21/Mar/2018:22:28:21 +1100] [Job 17] Read 91 bytes of print data...
D [21/Mar/2018:22:28:21 +1100] [Job 17] Wrote 91 bytes of print data...
D [21/Mar/2018:22:28:21 +1100] [Job 17] Error: This module is designed to work with HP Printers only
D [21/Mar/2018:22:28:21 +1100] [Job 17] STATE: +hplip.plugin-error
D [21/Mar/2018:22:28:21 +1100] [Job 17] prnt/hpcups/HPCupsFilter.cpp 486: m_Job initialization failed with error = 48
D [21/Mar/2018:22:28:21 +1100] [Job 17] Read 16 bytes of print data...
D [21/Mar/2018:22:28:21 +1100] [Job 17] Wrote 16 bytes of print data...
D [21/Mar/2018:22:28:21 +1100] [Job 17] Sent 107 bytes...
D [21/Mar/2018:22:28:21 +1100] [Job 17] PID 3787 (/usr/lib/cups/filter/hpcups) stopped with status 1.
D [21/Mar/2018:22:28:21 +1100] [Job 17] Hint: Try setting the LogLevel to "debug" to find out more.
D [21/Mar/2018:22:28:21 +1100] [Job 17] Processing page 2...
D [21/Mar/2018:22:28:21 +1100] [Job 17] Rendering completed
D [21/Mar/2018:22:28:21 +1100] [Job 17] PID 3786 (/usr/lib/cups/filter/gstoraster) exited with no errors.
D [21/Mar/2018:22:28:21 +1100] [Job 17] Waiting for read thread to exit...
D [21/Mar/2018:22:28:21 +1100] [Job 17] Read thread still active, aborting the pending read...
D [21/Mar/2018:22:28:21 +1100] [Job 17] PID 3788 (/usr/lib/cups/backend/usb) exited with no errors.
D [21/Mar/2018:22:28:21 +1100] [Job 17] End of messages
D [21/Mar/2018:22:28:21 +1100] [Job 17] printer-state=3(idle)
D [21/Mar/2018:22:28:21 +1100] [Job 17] printer-state-message="Rendering completed"
D [21/Mar/2018:22:28:21 +1100] [Job 17] printer-state-reasons=hplip.plugin-error

```[I]
Thanks for any help.[/I]

---

### Post by ajgreeny on 2018-03-21
The HPLIP page for that printer says a plugin is **Required** in order to work
> 8 ("**Required**") A downloadable driver plug-in is required for printing support. ("Optional") A downloadable driver plug-in is optional for printing support and may increase the speed, quality, or other aspect of printed output. ("No" or "None") A driver plug-in is not required nor available. Driver plug-ins are released under a proprietary (non-open) license and are not part of the HPLIP tarball release. For more information, please refer to this [KB article]("https://developers.hp.com/hp-linux-imaging-and-printing/binary_plugin.html")
Best of luck; I hope this helps.

---

### Post by Hodor on 2018-03-21
Thanks.  I downloaded hp-lip, ran the installer and CUPS can now print to this printer from Ubuntu. Hooray!

---

