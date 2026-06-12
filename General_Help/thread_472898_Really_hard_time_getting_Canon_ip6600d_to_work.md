---
title: "Really hard time getting Canon ip6600d to work"
date: 2007-06-13
forum: General Help
---

### Post by norobots on 2007-06-13
I'm wondering if someone can help me. I've already google searched, browsed every forum, went to the linux printer database, etc, and I cannot get my printer to print. I'm pretty sure I have the driver installed (says ip660d ver.2.6.0), Ubuntu says the printer is there and "Ready" but when I try to print a test page or say a pdf file, nothing happens.

Yes I am new to linux/Ubuntu but I REALLY don't want to have to install windows, I'm enjoying how nice Ubuntu works.. except for my printer. If someone can walk me through this me and my wife would be very happy people. Thanks.

---

### Post by 67GTA on 2007-06-13
[http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP6600D](http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP6600D) did you install both of the packages at the bottom of the link?

Did you try setup the printer with cups again after installing the driver?

---

### Post by norobots on 2007-06-22
I got it to print a test page beautifully, but it will not print from firefox, gimp, etc... anyone get this printer to work with Feisty?

---

### Post by stchman on 2007-06-22
> **norobots said:**
> I got it to print a test page beautifully, but it will not print from firefox, gimp, etc... anyone get this printer to work with Feisty?

Did you make your printer the deafult printer?

---

### Post by norobots on 2007-06-22
Well it's the only printer, and in the Printers window it has the green check on it with a green Ready.

---

### Post by 67GTA on 2007-06-22
Do you get an error message when you try to print?

---

### Post by norobots on 2007-06-22
No error message, In the print jobs window it has the job listed and it says "Stopped: job-stopped " when I try to resume nothing happens.

I just noticed this, wasn't there when I printed a test page originally but is in the Properties window now--

Ready: /usr/lib/cups/filter/pstocanonij failed

It will still print a test page though, but nothing else.

---

### Post by 67GTA on 2007-06-22
I remember someone saying they changed their paper size from A4 to Letter and it would print(not sure why). Cannon's aren't the most Linux friendly printers. It may be better to go buy a HP.

---

### Post by 67GTA on 2007-06-22
I found it.
[http://ubuntuforums.org/showthread.php?t=319564](http://ubuntuforums.org/showthread.php?t=319564)
Again, not sure what this will help, but might try it. Have you restarted your computer since you installed everything?

---

### Post by norobots on 2007-06-22
Yeah it has been restarted lots of times. 

It was already on Letter, I switched it to A4 and tried, nothing, switched back to Letter, nothing.

Thanks for the help btw :)

---

### Post by 67GTA on 2007-06-22
I done a google search on this and saw lots of the same for the Cannon printers in linux. I was lucky enough to already have an HP. Sorry I couldn't help more.

---

### Post by pickarooney on 2007-06-22
This printer can be a real pain, even under Windows with the proprietary Canon drivers. Even when it prints test pages, some programs have difficulties accessing or using the printer driver. This is the case with the two flagship programs of the company I work for. Not to be defeatist, but if at all possible, in your situation I'd try swapping it for another model.

---

