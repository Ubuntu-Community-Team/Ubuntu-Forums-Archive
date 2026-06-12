---
title: "Canon BJC-2110 printer not cooperating"
date: 2006-11-29
forum: General Help
---

### Post by Elimist on 2006-11-29
I installed it yesterday. It's there when I try and print something. It's in the Print Job Manager.
But it says "processing" for forever on whatever it tries to print.

I've looked into it on the CUPS site and a couple other places, I can't remember where. Some place said it needs a ppd file, and there's nothing in the ppd folder.
How can I get that file?

Any other ideas for solving this?

---

### Post by lhtown on 2006-11-29
Here is a link that might help, in case you haven't seen it:
[http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-BJC-2110](http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-BJC-2110)

It sounds like you might have selected the wrong driver. You might check to make sure cupsys-driver-gutenprint is installed. You might have to enter it as a BJC-2000 instead of a BJC-2110 to get it to work.

It looks like the gimpprint driver will also work.

I don't have this printer, but from all indications, it should work reasonably well without too much fuss.

---

### Post by Elimist on 2006-11-30
How do I change the driver?

---

### Post by lhtown on 2006-11-30
In System > administration > printers you can delete the printer icons that don't work. (all of them if your printer isn't working) and click on the new printer icon and follow the prompts to reinstall it and select the driver you want as I recall.

---

