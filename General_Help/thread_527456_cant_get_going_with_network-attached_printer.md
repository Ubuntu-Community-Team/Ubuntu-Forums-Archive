---
title: "cant get going with network-attached printer"
date: 2007-08-16
forum: General Help
---

### Post by wb0gaz on 2007-08-16
Xubuntu 7.04 system attached by LAN to HP Color laserjet 3700. The printer is on a fixed IP address, and I can ping that address from Xubuntu 7.04 system. I set a printer up (with system-config-printer) with device URI as socket://ip:9100 where ip is the address of the printer. Make and model are set properly. The printer state is enabled, accepting jobs, and shared. The printer state shows forever as "processing". In the printer tray there are three jobs (the first three things I tried to print); these all show status "Pending". I can't cancel any of them, getting CUPS server error "there was an error during the CUPS operation - client error not possible". These jobs stay in the queue across a reboot. I've tried restarting /etc/init.d/cupsys to no avail. I can telnet to the printer (on it's IP address and port 9100) and cause keyboard stuff to get printed.

With this, anyone able to help me get started? It's the last obstruction to me using Linux/Openoffice in regular production at my job (I leave the windoze box at home.)

Thanks much,

Dave

---

### Post by wb0gaz on 2007-08-17
Operator error - I had entered the IP address of the printer wrong - once changed, everything came to life normally.

Dave

---

