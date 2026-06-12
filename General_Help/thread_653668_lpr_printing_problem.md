---
title: "lpr printing problem"
date: 2007-12-30
forum: General Help
---

### Post by Eraser007 on 2007-12-30
Hi,

I've some problem printing documents with the lpr command.
Printing from FireFox, OpenOffice, gedit, ... is no problem at all but when I want to print a simple textfile with lpr nothing happens.

I use following commands: lpr test.txt and cat test.txt | lpr.
The terminal processes the command without any errors but the printer doesn't react.

When I execute lpq I see the document is on the queue:
C5450 is ready and printing
Rank   Owner      Job  Files                                 Total Size
active frederik   72   (standard input)                      31 bytes

The printer I'm using is an OKI C5450n

Does anyone have an idea what the problem can be?

Thanks

---

### Post by cmnorton on 2007-12-30
Your applications clearly have what is to them a "default" printer, but does CUPS know about a default printer? Print out your logs tail /var/log/messages and tail /var/log/syslog right after issuing the command, and see what's there.

---

### Post by Eraser007 on 2007-12-31
The default printer for CUPS is set to C5450 just like the Environment Variable PRINTER, which is used by the lpr command.
When I check the log files after I executed lpr test.txt or cat test.txt | lpr no new lines were added to the log.

---

