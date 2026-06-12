---
title: "Ubuntu 18.04.1 LTS CUPS / Samba Printer Stops Working After Awhile"
date: 2019-01-17
forum: General Help
---

### Post by mdbratch on 2019-01-17
I have an Ubuntu 18.04.1 LTS system which is a server on my private network and I have a couple of Windows clients. The server has two printers attached which are older HP printers (Laserjet 6L and Laserjet 1018). I set up the printers to use on the network with Windows clients via samba. In my Samba config, I just have
```
load printers = yes
cups options = raw
```.

I can see the printers fine from Windows clients and print. However, every couple of days printing to both of these printers stops working. I've tried restarting the CUPS service to get them going again but it doesn't work. The only solution I've found is to reboot the Ubuntu server, then the jobs I had sent will start printing immediately after the reboot completes.

Anyone know what might cause this?

---

