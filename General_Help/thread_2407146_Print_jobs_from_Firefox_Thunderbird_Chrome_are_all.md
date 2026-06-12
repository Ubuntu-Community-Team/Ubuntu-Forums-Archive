---
title: "Print jobs from Firefox Thunderbird Chrome are all cancelled at printer"
date: 2018-11-30
forum: General Help
---

### Post by bert.ram.aerts on 2018-11-30
I have both Ubuntu 18.10 and Windows 10 on a Dell 7577 laptop.
My printer is Epson EcoTank ET-2750.
I use the printer via its Wifi connection.
Printer is configured.
Printing works fine on Windows 10.

In Ubuntu I can print the printer test page.
I can print from Mathematica, LibreOffice and Okular.
But I can NOT print from Firefox, Thunderbird and Google Chrome.

```
bert@Dell7577Linux:/var/log/cups$ cat error_log
E [30/Nov/2018:11:07:36 +0100] [Job 25] Unable to add document to print job.
E [30/Nov/2018:11:07:42 +0100] [Job 25] Print job canceled at printer.

bert@Dell7577Linux:/usr/lib/cups/backend$ /usr/lib/cups/backend/snmp
network lpd://192.168.1.14:515/PASSTHRU "EPSON ET-2750 Series" "EPSON ET-2750 Series" "MFG:EPSON;CMD:ESCPL2,BDC,D4,D4PX,ESCPR1,END4,GENEP;MDL:ET-2750 Series;CLS:PRINTER;DES:EPSON ET-2750 Series;CID:EpsonRGB;FID:FXN,DPA,WFA,ETN,AFN,DAN,WRA;RID:40;DDS:022500;ELG:1162;SN:583444533030393655;" ""
```

What could cause this?

---

### Post by STPitcher on 2018-12-31
I have this same problem.  I can print from LibreOffice but can't print from Thunderbird.  Haven't tried others.

I've just recently done a clean install of Ubuntu 18.10.

Printer is Epson XP-830.

Error is Job Canceled at Printer.

---

### Post by clementc on 2018-12-31
Hi [**bert.ram.aerts**]("https://ubuntuforums.org/member.php?u=2112967") and [**STPitcher**]("https://ubuntuforums.org/member.php?u=608815"),

** Edit **

It seems that [**bert.ram.aerts**]("https://ubuntuforums.org/member.php?u=2112967") is already using the LPD protocol, in this case, can you please try switching to the ipp(s) protocol(s)?

If this still doesn't work, "AppSocket/HP JetDirect" might be your savior.

** End of Edit **

I believe that your issue might be due to an incompatibility between your printers, CUPS and the ipp protocol.

Can you please try navigating to [http://localhost:631/](http://localhost:631/) then click "Adding Printers and Classes", enter your username and password, click "Add Printer", select "LPD/LPR Host or Printer" and continue the installation process until the end, then try printing again using the LPD protocol.

Please report back once you have done this.

---

### Post by STPitcher on 2019-01-01
My first attempt at using LDP.  I used the "driverless" option.  It printed from Thunderbird, but that and the test page both came out, garbage.  I.E.  binary displayed as ASCII.  Or some such.  Maybe I'll try a non-driverless option.

---

### Post by clementc on 2019-01-01
Hi [**[COLOR=#000000]STPitcher[/COLOR]**]("https://ubuntuforums.org/member.php?u=608815"),

Can you please try using IPP and see if this works? Other recommended option is AppSocket.

However, driverless is not recommended in your case as you already noticed.

---

### Post by STPitcher on 2019-01-01
AppSocket works!!
IPP the job just sat there, pending.  Never printed until I modified the printer to AppSocket.

Thanks so much!!

- stp

---

### Post by clementc on 2019-01-01
Hi [**[COLOR=#000000]STPitcher[/COLOR]**]("https://ubuntuforums.org/member.php?u=608815"),

I am glad to hear that your issue is now resolved.

Happy printing!

---

