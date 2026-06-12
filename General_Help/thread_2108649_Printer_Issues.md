---
title: "Printer Issues"
date: 2013-01-25
forum: General Help
---

### Post by neuman1812 on 2013-01-25
Running Ubuntu 12.04
Printer is a Lexmark s310  Networked wireless

I can print fine to it for a few pages...then for whatever reason it stops communicating.  The only way to get it to work I've found is to either restart the cups  or to delete and readd the printer.   

This is the last few lines of my access_log

```
ocalhost - - [25/Jan/2013:06:51:03 -0500] "POST /printers/S310-Series HTTP/1.1" 200 271 Create-Job successful-ok
localhost - - [25/Jan/2013:06:51:03 -0500] "POST /printers/S310-Series HTTP/1.1" 200 29294 Send-Document successful-ok
localhost - - [25/Jan/2013:06:51:03 -0500] "POST /printers/S310-Series HTTP/1.1" 200 292 Create-Job successful-ok
localhost - - [25/Jan/2013:06:51:03 -0500] "POST /printers/S310-Series HTTP/1.1" 200 29294 Send-Document successful-ok
localhost - - [25/Jan/2013:06:51:37 -0500] "POST /printers/S310-Series HTTP/1.1" 200 271 Create-Job successful-ok
localhost - - [25/Jan/2013:06:51:37 -0500] "POST /printers/S310-Series HTTP/1.1" 200 28677 Send-Document successful-ok
localhost - midnight [25/Jan/2013:06:55:32 -0500] "POST / HTTP/1.1" 200 186 Renew-Subscription successful-ok
localhost - - [25/Jan/2013:07:06:11 -0500] "POST /printers/S310-Series HTTP/1.1" 200 270 Create-Job successful-ok
localhost - - [25/Jan/2013:07:06:11 -0500] "POST /printers/S310-Series HTTP/1.1" 200 28691 Send-Document successful-ok
localhost - - [25/Jan/2013:07:06:32 -0500] "POST / HTTP/1.1" 200 187 Renew-Subscription client-error-not-found
localhost - - [25/Jan/2013:07:06:32 -0500] "POST / HTTP/1.1" 200 348 Create-Printer-Subscription successful-ok
localhost - - [25/Jan/2013:07:06:33 -0500] "POST /admin/ HTTP/1.1" 401 127 CUPS-Delete-Printer successful-ok
localhost - root [25/Jan/2013:07:06:33 -0500] "POST /admin/ HTTP/1.1" 200 127 CUPS-Delete-Printer successful-ok
localhost - root [25/Jan/2013:07:06:35 -0500] "POST / HTTP/1.1" 200 2957 CUPS-Get-Devices -
localhost - - [25/Jan/2013:07:06:52 -0500] "POST / HTTP/1.1" 200 4876553 CUPS-Get-PPDs -
localhost - root [25/Jan/2013:07:06:57 -0500] "POST /admin/ HTTP/1.1" 200 322 CUPS-Add-Modify-Printer successful-ok
localhost - root [25/Jan/2013:07:06:57 -0500] "POST /admin/ HTTP/1.1" 200 127 CUPS-Accept-Jobs successful-ok
localhost - root [25/Jan/2013:07:06:57 -0500] "POST /admin/ HTTP/1.1" 200 127 Resume-Printer successful-ok
localhost - - [25/Jan/2013:07:07:02 -0500] "POST / HTTP/1.1" 200 156 Cancel-Subscription successful-ok
localhost - - [25/Jan/2013:07:07:02 -0500] "POST / HTTP/1.1" 200 156 Cancel-Subscription client-error-not-found
localhost - - [25/Jan/2013:07:07:10 -0500] "POST /printers/S310-Series HTTP/1.1" 200 270 Create-Job successful-ok
localhost - - [25/Jan/2013:07:07:10 -0500] "POST /printers/S310-Series HTTP/1.1" 200 28691 Send-Document successful-ok
localhost - - [25/Jan/2013:07:07:10 -0500] "POST /printers/S310-Series HTTP/1.1" 200 291 Create-Job successful-ok
localhost - - [25/Jan/2013:07:07:10 -0500] "POST /printers/S310-Series HTTP/1.1" 200 28691 Send-Document successful-ok

```

---

### Post by neuman1812 on 2013-02-26
Anyone have thoughts?  Still having this issue,.

---

