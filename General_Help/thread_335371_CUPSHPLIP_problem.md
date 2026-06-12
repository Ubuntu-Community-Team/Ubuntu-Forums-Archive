---
title: "CUPS/HPLIP problem"
date: 2007-01-10
forum: General Help
---

### Post by Hador on 2007-01-10
Hi everyone, I've been using (X)Ubuntu edgy for a while, and just recently bought a HP DeskJet F380 printer. I had managed to set it up and good, though HPLIP and the printer suddenly stopped working. At first I tried removing the ubuntu packages and installing the self-installing/compiling version from HPLIP's homepage, but that didn't work either. Debugging showed that the daemons included with the suite (hpiod/hpssd) weren't able to attach to the CUPS' socket. Therefore my best guess would be that it's CUPS (cupsys, rather) causing the trouble.
Question is: is anyone else experiencing the same issue or has any suggestion on how to solve it?

Note: I'm using a pretty much out-of-the-box installation of Ubuntu, with a manually compiled 2.6.19.1 kernel. I've managed to get the printer working again with CUPS, download the ppd  file from linuxprinting.org, but still I would love to get the HPLIP suite back up and running (scanning doesnt work without that as well)!

Thanks in advance.

---

### Post by 11hjpphty76lkjj on 2007-01-12
What happens if you run:

/etc/init.d/hplip restart

also run tail -f /var/log/messages and post any errors.

Aaron

---

