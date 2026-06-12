---
title: "Is my problem OS or Software?"
date: 2006-10-28
forum: General Help
---

### Post by Ken Milburn on 2006-10-28
I installed Ubuntu 6.06 successfully but still require a print driver.

I installed TurboPrint which supports the Canon i860 printer.  I got as far as the command:
   xtpconfig    and get GTK-WARNING  Cannot open display
That is as far as I could pursue this.
I tried a few other commands mentioned if similar posts, such as:
   xhost+  Unable to open display ""

I have posted on the TurboPrint forum with no reply.  

This got me thinking perhaps this is my Ubuntu os installation problem.

If so, what direction should I start digging in?

I have an Old Pentium mmx computer.

Thank you for your help.

---

### Post by deweese on 2006-10-28
Did you look to see if Ubuntu already has the driver for this printer?
I installed my printer.  The drivers were included in Ubuntu. Go to administration then to printing.

---

### Post by .t. on 2006-10-28
Run the command with "DISPLAY=:0 <command goes here>". That may help.

Plus, OS *is* software!

---

### Post by beerfan on 2006-10-28
See this thread.

[http://ubuntuforums.org/showthread.php?t=1108](http://ubuntuforums.org/showthread.php?t=1108)

It discusses your printer model.

---

### Post by Ken Milburn on 2006-10-29
> **deweese said:**
> Did you look to see if Ubuntu already has the driver for this printer?
I installed my printer.  The drivers were included in Ubuntu. Go to administration then to printing.

I went back to administration - printing.  I connected my usb cable directly to the printed and to the computer.
Ubuntu saw my Canon i860 printer.  The driver selection did not show any i8xx printers however the selection did highlight imageRunner-330s so I tried using it.
A test page from OpenOffice looked ok, but nothing happened when I tried to print.

---

### Post by Ken Milburn on 2006-10-29
Trying the suggestion by .t. I got:
DISPLAY=:0 xtpconfig
ERROR:
inifile::open: could not open input file:
/home/ken/.turboprint/turboprint.cfg
config_class: open_config_file: could not open file.

The other reply regarding turboPrint postings for my i860 printer will be examined one step at a time.

Thank you for all the responses.

---

