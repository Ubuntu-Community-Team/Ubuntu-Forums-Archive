---
title: "Ubuntu Hardy versus the Serial Port"
date: 2008-06-20
forum: General Help
---

### Post by mykrob on 2008-06-20
Hey-

Trying to get an application to run in Dosemu on Ubuntu Hardy. it worked fine in Ubuntu 6.06. I think my issue is the serial port. This application needs the serial port to work. Running "lshw" in terminal shows the serial as UNCLAIMED.

What does this mean?

anyway, I have configured my dosemu.conf to route COM1 to /dev/ttyS0. The error I get is "can't find IRQ line for serial port 1", which I can only assume is due to this serial error.

Help?

thanks,
-myk

---

