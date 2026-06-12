---
title: "Printer"
date: 2005-10-13
forum: General Help
---

### Post by fiby on 2005-10-13
i have  dell photo printer 720, A.K.A. Lexmark z615.  I did everything thing the same as when nit worked with HOARY.  However, this time, the printer manager detects a deell photo printer 720, but it doesn't work.  If Ii click the chose from other port, usb #1 is labeled (dell photo printer).  However, doesn't work still.  And if I set it to the USB #1 port the port will change to canon parallel port #1.  My setting don't stick?

Any ideas?

---

### Post by rplantz on 2005-10-13
I had to delete my printers (I have two). Then I turned them on and rebooted the system. Then when I added them, they were both detected. They both work just fine.

By the way, one of the printers is an Epson CX-6400 (all-in-one). I used the same procedure to get the scanning part to work. I turned it on and rebooted. That allowed me to use sane-find-scanner to get the vendor and product numbers. I then added them to /etc/sane.d/epson.conf. Scanned a photo, then printed it from the file that was created. All worked just fine.

Bob

---

### Post by fiby on 2005-10-14
I have no clue, but the computer gods liked me and when I fired her  up  today the printer worked...  I am a linux newbie so I'll take it:)

---

