---
title: "Printer not printing but is recognised"
date: 2006-12-13
forum: General Help
---

### Post by Robbyx on 2006-12-13
My printer is a lexmark X73. I only use the printer facility not the scanner.

When I send a test page to the printer on USB2 I do not get any print out. 

I have also set up the printer using cupsys on [http://localhost:631](http://localhost:631) but it made no difference.

I would like help to trace why the printer will not printout under 6.10. I have not tried earlier versions of Ub.


My cups error log shows: (I have edited out the repeat lines, of which there are many)

Robin

```
 [12/Dec/2006:22:15:10 +0000] CUPS-Add-Modify-Printer: Unauthorized
E [12/Dec/2006:22:15:20 +0000] cupsdAuthorize: Local authentication certificate not found!
E [12/Dec/2006:22:15:21 +0000] [Job 10] /ioerror in --.outputpage--
E [12/Dec/2006:22:15:21 +0000] PID 6271 (/usr/lib/cups/filter/foomatic-rip) stopped with status 1!

E [12/Dec/2006:22:18:29 +0000] CUPS-Delete-Printer: Unauthorized
E [12/Dec/2006:22:24:19 +0000] Creating missing directory "/var/run/cups/certs"
E [12/Dec/2006:22:29:08 +0000] [Job 11] /ioerror in --.outputpage--
E [12/Dec/2006:22:29:08 +0000] PID 5205 (/usr/lib/cups/filter/foomatic-rip) stopped with status 1!
E [13/Dec/2006:09:04:03 +0000] Creating missing directory "/var/run/cups/certs"
```

---

### Post by Sef on 2006-12-14
Read [LinuxPrinting]("http://linuxprinting.org/show_printer.cgi?recnum=Lexmark-X73").

---

### Post by Robbyx on 2006-12-14
That reference is hard!

Were you pointing me to the Cups quick start?

I went to that page and tried to follow the advice but the systems are not the same. I could not find cups in ubuntu. Where is the program not the directory?

It seems to me that foomatic-rip is already installed in standard Ub and I assume foomatic-gswrapper is also there but I am not sure.

Assuming they are present I think I do not need to follow the steps before 4 as they seem to be there to load foomatic, which is present in Ub. If so I still have a problem because the advice suggest that:

Configure CUPS.

The simplest way is to walk through the Add Printer wizard in the CUPS web interface at [http://localhost:631/admin](http://localhost:631/admin). KDE users may instead use the KDE Printing Manager's "Add Printer" wizard. 

I had already done that earlier and it did not work. 

How do I go from here?

Robin

---

### Post by Robbyx on 2006-12-15
I have it working. Here is my guidance:

[http://forums.freestandards.org/read.php?29,297](http://forums.freestandards.org/read.php?29,297)

Robin

---

