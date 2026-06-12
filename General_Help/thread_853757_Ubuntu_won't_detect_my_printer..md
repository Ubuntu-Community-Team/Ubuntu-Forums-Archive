---
title: "Ubuntu won't detect my printer."
date: 2008-07-08
forum: General Help
---

### Post by DocHolliday2006 on 2008-07-08
Though I don't recall making any changes, about a month ago my printer stopped being able to send print commands to my printer (Epson Stylus CX 6600). The print commands would que up but would not print.

I tried deleting the printer out of Printer Configuration under administration in system, but it could not be redetected. I tried the obvious things like checking the usb cable and restarting the printer.

I have Hardy Heron

Does anyone know how I can get my printer detected again? Any advice welcome.

BTW, I don't know if this will help, but it came out of the trouble shoot option on the printer page:

Page 1 (Choose printer):
{'cups_dests_available': [], 'cups_queue_listed': False}
Page 2 (Printer not listed):
{'cups_connection_failure': False}
Page 3 (Local or remote?):
{'printer_is_remote': False}


Thanks.

---

### Post by bgs100 on 2008-11-27
same problem here!  My System>Admin>Printer won't even come up!

---

### Post by Peter09 on 2008-11-27
Try in firefox,

[http://localhost:631](http://localhost:631)

This will start up the Cups application

---

