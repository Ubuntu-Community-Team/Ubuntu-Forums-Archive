---
title: "Gedit command in terminal crashes"
date: 2008-05-27
forum: General Help
---

### Post by VickiAnn on 2008-05-27
I have been trying to sort out a few problems with my hardy install of Ubuntu.
It was all working wonderfully, and then I installed some recommended updates a few days ago which seemed to delete the driver for my USB wireless adaptor so I had to reinstall that and then I switched to wifi-radar and disbaled networking on the Network-Manager.

In the fix for the driver/wireless I had to change the /etc/network/interfaces/ file from what it was to:

> auto rausb0
iface rausb0 inet dhcp

Last time I did this to fix the connection it caused an error starting up the Gnome-settings-daemon, which has happened again this time.
I've forgotten how I fixed it so I'm trying some of the suggestions online for this.

I have now noticed though, that terminal is not asking for a sudo password today, and also that the gedit command is not running - well it tries - it takes about five minutes to attempt to load it and then crashes before it actually loads the file in the opened gedit window and I've just waited 15 minutes and no luck. It just crashes so I can't edit files through terminal.

Has anyone got any ideas as to what is going on with my installation?
I'm running Hardy Heron - my RAM definitely isn't the problem as this was working fine a few days ago.

I doubt anyone has been able to hack and mess up my system as I don't run any FTP programs or anything ...

---

