---
title: "system-config-printer hangs"
date: 2007-10-30
forum: General Help
---

### Post by elamericano on 2007-10-30
This app hangs. The window does not redraw. Eventually it does give an error: There was a problem connecting to the CUPS server. When you close that, the printer configuration closes.

The first time it ran I did not enter my username and password, when I went back and added that, I had already moved, and the printer was no longer on my network. I restarted the cupsys and rebooted, but it's messed up. I tried to delete the printers.conf for that printer, but it doesn't help.

If I can delete a conf file that will get recreated, maybe that's the best way to unstick this. Otherwise, what would I reinstall to get back to the default configuration?

This is with Ubuntu 7.10, BTW.

---

### Post by elamericano on 2007-11-06
I applied an update today for cupsys and 6 or so related packages. This has gotten rid of the hang, are far as I can tell. The only remaining problem is that one remote printer show up and if I click that it immediately says, "can't connect to cups server" and it exits as soon as I click OK. We have lots of printers on our LAN, I don't know why only that one shows and why it has to exit if I click it. If I browse for printers it shows them all.

So, I've added the three printers I want, and I unchecked "show me network printers", so hopefully that's the end of it.

Does someone know, I've added some printers now, but they show up under "local"? I think of them as remote, because they're on the LAN or shared from another computer. If that's not remote, then what is?

---

### Post by fuzzyworbles on 2008-01-17
I had the same exact problem. One day I could configure printers, and the next day I couldn't. I'm not sure what I did to break it, but following these instructions fixed it: [https://bugs.launchpad.net/ubuntu/+source/gnome-cups-manager/+bug/164204]("https://bugs.launchpad.net/ubuntu/+source/gnome-cups-manager/+bug/164204")

---

