---
title: "Installing Canon Canon imageRUNNER ADVANCE C5030 on Ubuntu 13.04"
date: 2013-08-08
forum: General Help
---

### Post by rgara on 2013-08-08
I have this printer running fine on Ubuntu 11.10. However, no luck on 32 bit 13.04 and I'm at a dead end.

Installed Canon 32 bit deb drivers from [http://software.canon-europe.com/products/0010762.asp](http://software.canon-europe.com/products/0010762.asp) (cndrvcups-common_2.70-1_i386.deb  cndrvcups-ufr2-uk_2.70-1_i386.deb). Installed common first. 

Used the printer app to create a printer. All seemed to work fine - printer was identified and created with no errors. But printing the test page fails. I know the print attempt is getting to the printer, because I see my request in the printer job queue (its an error). Cupps error logs show:

```
E [07/Aug/2013:17:24:32 -0400] [cups-driverd] Bad driver information file "/usr/share/cups/drv/cupsfilters.drv"!
W [07/Aug/2013:17:33:33 -0400] [CGI] Missing Product in /usr/share/cups/model/CNCUPSIRADV4051ZK.ppd!
E [07/Aug/2013:17:33:33 -0400] [cups-driverd] Bad driver information file "/usr/share/cups/drv/cupsfilters.drv"!
W [07/Aug/2013:17:33:33 -0400] [CGI] Missing Product in /usr/share/ppd/CNCUPSIRADV4051ZK.ppd!
W [07/Aug/2013:17:34:09 -0400] AddProfile failed: org.freedesktop.DBus.Error.UnknownMethod:No such interface `org.freedesktop.ColorManager' on object at path /org/freedesktop/ColorManager/devices/cups_Canon_iR_ADV_C5030_5035
W [07/Aug/2013:17:34:09 -0400] AddProfile failed: org.freedesktop.DBus.Error.UnknownMethod:No such interface `org.freedesktop.ColorManager' on object at path /org/freedesktop/ColorManager/devices/cups_Canon_iR_ADV_C5030_5035
E [07/Aug/2013:17:34:17 -0400] [Job 1] src = libcanon_pdlwrapper.c, line = 1018, err = -1¥nError Response:ReqNo=8, SeqNo=16926,opvpErrorNo=-2
E [07/Aug/2013:17:34:17 -0400] [Job 1] src = libcanon_pdlwrapper.c, line = 703, err = -1¥nError Response:ReqNo=8, SeqNo=16945,opvpErrorNo=-2
E [07/Aug/2013:17:34:17 -0400] [Job 1] src = libcanon_pdlwrapper.c, line = 1078, err = -1¥nINFO: Waiting for printer to finish.
```

I'm guessing these drivers are simply incompatabile with Ubuntu 13?

---

### Post by gordintoronto on 2013-08-08
Can you remove the stuff from the deb file? The correct way to install is using Printers.

---

### Post by rgara on 2013-08-12
I can, but on a clean install, Ubuntu doesn't recognize the printer. I tried generic (recommended), but that errors out:

```
E [12/Aug/2013:13:01:00 -0400] [cups-driverd] Bad driver information file "/usr/share/cups/drv/cupsfilters.drv"!
E [12/Aug/2013:13:33:05 -0400] [cups-driverd] Bad driver information file "/usr/share/cups/drv/cupsfilters.drv"!
W [12/Aug/2013:13:33:37 -0400] AddProfile failed: org.freedesktop.DBus.Error.UnknownMethod:No such interface `org.freedesktop.ColorManager' on object at path /org/freedesktop/ColorManager/devices/cups_Generic_text_only
E [12/Aug/2013:13:33:40 -0400] Returning IPP client-error-document-format-not-supported for Print-Job (ipp://localhost/printers/Generic-text-only) from localhost
```

This printer isn't in the database, and choosing the search option reslts with "No Matches found".

Everything I've read suggests I need to install Cannon's UFRII drivers ... which worked in 11. just wondering if I did something dumb, or if there is a work around.

---

### Post by rgara on 2013-08-13
I think I'm close. I found this blurb in the README:


> If you are using Ubuntu 12.04/12.10 32-bit and attempt to print with a Color 
  iR or Color LBP series printer using this driver, you may not be able to 
  print. This is because the JPEG library used by this driver is not installed 
  when you do a standard installation in Ubuntu 12.04/12.10.
  You can solve this problem by performing an additional package installation.
  Execute the following command:
    # apt-get install libjpeg62

After installing that, I no longer get errors in the cups error log. Sadly, printing still fails. The printer itself reports a generic error saying the print job was interupted?

> #099
Cause 1 - Copying/printing was interrupted.
Remedy - Try copying/printing again.

I'm fairly confident Ubuntu is connecting to the printer OK to get status because it is reporting low toner .. which is true. It has the colors with low toner correct. 

The only entry I get in the log file is when I try to cancel the print job:

```

W [13/Aug/2013:11:55:16 -0400] [Job 3] The printer did not respond.
```

Not much to go on ....

---

### Post by newbie-user on 2013-08-13
Have you tried the drivers from Codehost? [http://canon.codehost.com](http://canon.codehost.com)

We use codehost drivers for our iR5075 and iR-ADV C5045 copiers. Once you download the driver, make it executable, then run it using:
```
sudo codehost-config
```

---

### Post by rgara on 2013-08-14
Interesting. I've not heard of these guys before. Unfortunately, this product didn't work either. I uninstalled the Canon UFR drivers. Downloaded and installed Codehost app. The app recognized the printer just fine. However, an attempt to print a test page resulted with the same generic error code on the printer. Cups log does show errors this time:

```

D [14/Aug/2013:16:35:18 -0400] [Job 7] time-at-processing=1376512518
D [14/Aug/2013:16:35:18 -0400] cupsdMarkDirty(---J-)
D [14/Aug/2013:16:35:18 -0400] cupsdSetBusyState: newbusy="Dirty files", busy="Printing jobs and dirty files"
D [14/Aug/2013:16:35:18 -0400] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
D [14/Aug/2013:16:35:18 -0400] cupsdMarkDirty(----S)
D [14/Aug/2013:16:35:18 -0400] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
D [14/Aug/2013:16:35:18 -0400] [Job 7] job-sheets=none,none
D [14/Aug/2013:16:35:18 -0400] [Job 7] argv[0]="Canon-iR-ADV-C5030"
D [14/Aug/2013:16:35:18 -0400] [Job 7] argv[1]="7"
D [14/Aug/2013:16:35:18 -0400] [Job 7] argv[2]="rich"
D [14/Aug/2013:16:35:18 -0400] [Job 7] argv[3]="test-tmpl.ps"
D [14/Aug/2013:16:35:18 -0400] [Job 7] argv[4]="1"
D [14/Aug/2013:16:35:18 -0400] [Job 7] argv[5]="CNFinisher=None noCNPuncher noCNEnableTrustPrint Resolution=600 CNMonitorProfile=sRGBv3.0(Canon) CNMatchingMethod=Photographic CNTonerSaving=Auto MediaType=A
uto InputSlot=Auto CNInterleafSheet=None CNInterleafMediaType=PlainPaper1 CNInterleafPrint=None OutputBin=Auto Duplex=None BindEdge=Left Booklet=None CNOutputPartition=None Collate StapleLocation=TopLeft C
NSaddleStitch=None CNPunch=None CNMultiPunch=Off CNColorMode=Auto CNCopySetNumbering=None noCNShiftStartPrintPosition noCNCreep CNDisplacementCorrection=Device noCNTrustPrint CNAdvancedSmoothing=None CNCol
orHalftone=None CNHalftone=None CNLineControl=None CNJobExecMode=print CNSharpness=None PageSize=A4 job-uuid=urn:uuid:442c9c33-ca28-33f4-7de1-abd039e0ef5d job-originating-host-name=localhost time-at-creation=1376512350 time-at-processing=1376512518"
D [14/Aug/2013:16:35:18 -0400] [Job 7] argv[6]="/var/spool/cups/d00007-001"
D [14/Aug/2013:16:35:18 -0400] [Job 7] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [14/Aug/2013:16:35:18 -0400] [Job 7] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [14/Aug/2013:16:35:18 -0400] [Job 7] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [14/Aug/2013:16:35:18 -0400] [Job 7] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [14/Aug/2013:16:35:18 -0400] [Job 7] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [14/Aug/2013:16:35:18 -0400] [Job 7] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [14/Aug/2013:16:35:18 -0400] [Job 7] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [14/Aug/2013:16:35:18 -0400] [Job 7] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [14/Aug/2013:16:35:18 -0400] [Job 7] envp[8]="HOME=/var/spool/cups/tmp"
D [14/Aug/2013:16:35:18 -0400] [Job 7] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [14/Aug/2013:16:35:18 -0400] [Job 7] envp[10]="SERVER_ADMIN=root@rich-MXG061"
D [14/Aug/2013:16:35:18 -0400] [Job 7] envp[11]="SOFTWARE=CUPS/1.6.2"
D [14/Aug/2013:16:35:18 -0400] [Job 7] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [14/Aug/2013:16:35:18 -0400] [Job 7] envp[13]="USER=root"
D [14/Aug/2013:16:35:18 -0400] [Job 7] envp[14]="CUPS_MAX_MESSAGE=2047"
D [14/Aug/2013:16:35:18 -0400] [Job 7] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"
D [14/Aug/2013:16:35:18 -0400] [Job 7] envp[16]="CUPS_ENCRYPTION=IfRequested"
D [14/Aug/2013:16:35:18 -0400] [Job 7] envp[17]="IPP_PORT=631"
D [14/Aug/2013:16:35:18 -0400] [Job 7] envp[18]="CHARSET=utf-8"
D [14/Aug/2013:16:35:18 -0400] [Job 7] envp[19]="LANG=C"
D [14/Aug/2013:16:35:18 -0400] [Job 7] envp[20]="PPD=/etc/cups/ppd/Canon-iR-ADV-C5030.ppd"
D [14/Aug/2013:16:35:18 -0400] [Job 7] envp[21]="RIP_MAX_CACHE=128m"
D [14/Aug/2013:16:35:18 -0400] [Job 7] envp[22]="CONTENT_TYPE=application/postscript"
D [14/Aug/2013:16:35:18 -0400] [Job 7] envp[23]="DEVICE_URI=lpd://10.10.2.7:9100/Canon-iR-ADV-C5030"
D [14/Aug/2013:16:35:18 -0400] [Job 7] envp[24]="PRINTER_INFO=Canon-iR-ADV-C5030"
D [14/Aug/2013:16:35:18 -0400] [Job 7] envp[25]="PRINTER_LOCATION="
D [14/Aug/2013:16:35:18 -0400] [Job 7] envp[26]="PRINTER=Canon-iR-ADV-C5030"
D [14/Aug/2013:16:35:18 -0400] [Job 7] envp[27]="PRINTER_STATE_REASONS=toner-low-report"
D [14/Aug/2013:16:35:18 -0400] [Job 7] envp[28]="CUPS_FILETYPE=document"
D [14/Aug/2013:16:35:18 -0400] [Job 7] envp[29]="FINAL_CONTENT_TYPE=printer/Canon-iR-ADV-C5030"
D [14/Aug/2013:16:35:18 -0400] [Job 7] envp[30]="AUTH_I****"
I [14/Aug/2013:16:35:18 -0400] [Job 7] Started filter /usr/lib/cups/filter/pstopdf (PID 3342)
I [14/Aug/2013:16:35:18 -0400] [Job 7] Started filter /usr/lib/cups/filter/pdftopdf (PID 3344)
I [14/Aug/2013:16:35:18 -0400] [Job 7] Started filter /usr/lib/cups/filter/pdftops (PID 3345)
E [14/Aug/2013:16:35:18 -0400] Canon-iR-ADV-C5030: File "/usr/lib/cups/filter/pstoufr2cpca" not available: No such file or directory
D [14/Aug/2013:16:35:18 -0400] cupsdMarkDirty(P----)
D [14/Aug/2013:16:35:18 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Dirty files"
D [14/Aug/2013:16:35:18 -0400] cupsdMarkDirty(----S)
D [14/Aug/2013:16:35:18 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
E [14/Aug/2013:16:35:18 -0400] [Job 7] Unable to start filter "pstoufr2cpca" - Success.
D [14/Aug/2013:16:35:18 -0400] cupsdMarkDirty(----S)
D [14/Aug/2013:16:35:18 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
E [14/Aug/2013:16:35:18 -0400] [Job 7] Stopping job because the scheduler could not execute a filter.


```

---

### Post by rgara on 2013-08-15
I noticed I had some Ubuntu updates pending. I installed them, reinstalled the Canon drivers, and now printing works ?!?!? 

Dunno if I was just being completely ignorant before, or if there was something in those recent updates that fixed printing. For what its worth, I did a completely clean install and went through the process again. Printing still worked.

 Current state of my install is:

```
bit_Driver/Debian$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=13.04
DISTRIB_CODENAME=raring
DISTRIB_DESCRIPTION="Ubuntu 13.04"

rich@rich-MXG061:~/Downloads/Linux_UFRII_PrinterDriver_V270_uk_EN/32-bit_Driver/Debian$ uname -a
Linux rich-MXG061 3.8.0-27-generic #40-Ubuntu SMP Tue Jul 9 00:19:35 UTC 2013 i686 i686 i686 GNU/Linux
```

Then I downloaded the linux drivers from here:

> [http://support-asia.canon-asia.com/?personal](http://support-asia.canon-asia.com/?personal)

I'm not sure if I really need libjpeg, but I installed anyway. cndrvcups is dependent on libglade, so installed that too:
```

sudo  apt-get install libjpeg62
sudo apt-get install libglade2-0
sudo dpkg -i cndrvcups-common_2.70-1_i386.deb
sudo dpkg -i cndrvcups-ufr2-uk_2.70-1_i386.deb
```

Then added the printer through the printers program. Only thing I don't understand is that cups error log still shows errors:

```
W [15/Aug/2013:15:06:51 -0400] [CGI] Missing Product in /usr/share/cups/model/CNCUPSIRADV4051ZK.ppd!
E [15/Aug/2013:15:06:51 -0400] [cups-driverd] Bad driver information file "/usr/share/cups/drv/cupsfilters.drv"!
W [15/Aug/2013:15:06:51 -0400] [CGI] Missing Product in /usr/share/ppd/CNCUPSIRADV4051ZK.ppd!
W [15/Aug/2013:15:07:18 -0400] AddProfile failed: org.freedesktop.DBus.Error.UnknownMethod:No such interface `org.freedesktop.ColorManager' on object at path /org/freedesktop/ColorManager/devices/cups_Canon_iR_ADV_C5030_5035
W [15/Aug/2013:15:07:18 -0400] AddProfile failed: org.freedesktop.DBus.Error.UnknownMethod:No such interface `org.freedesktop.ColorManager' on object at path /org/freedesktop/ColorManager/devices/cups_Canon_iR_ADV_C5030_5035
```

but printing seems to work. So guess I'm good. Thanks for the suggestions along the way.

---

