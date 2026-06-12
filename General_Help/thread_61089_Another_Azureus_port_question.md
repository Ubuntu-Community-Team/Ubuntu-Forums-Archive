---
title: "Another Azureus port question"
date: 2005-08-30
forum: General Help
---

### Post by Copter on 2005-08-30
hi!

ive just installed Azureus. unfortunatly my 6881 port is closed. how can i _open_ it. it seems to be open when running Azureus under Windows. my internet connection looks like that

my computer's ip : 10.0.0.25
gateway (my server's ip) : 10.0.0.1
mask : 255.255.255.0
external ip : 217.97.7x.xxx

i think its more like ubuntu rather than server related.

btw [www.portforwardning.com](www.portforwardning.com) takes my nowhere

thanks!

copter :]

---

### Post by arnieboy on 2005-08-30
[QUOTE=Copter]hi!

ive just installed Azureus. unfortunatly my 6881 port is closed. how can i _open_ it. it seems to be open when running Azureus under Windows. my internet connection looks like that

my computer's ip : 10.0.0.25
gateway (my server's ip) : 10.0.0.1
mask : 255.255.255.0
external ip : 217.97.7x.xxx

i think its more like ubuntu rather than server related.

btw [www.portforwardning.com](www.portforwardning.com) takes my nowhere

thanks!

copter :][/QUOTE]
the right way to do it is to configure iptables to open up ports 6881-6889 for you. The easiest way to do that is as follows:
```
sudo apt-get install firestarter
```
when firestarter gets installed, run it from system tools.
go to the "policy" tab and click on "add rule". there u will find a nice drop down menu which will let u open up the port which bittorrent uses (6881-6889). save that rule and close. also go to preferences--> and make sure when u hit the close button on firestarter main window it gets docked into system tray.
U should be interested in this howto which explains how to make firestarter run automatically on boot up:
[http://www.ubuntuforums.org/showthread.php?t=26483](http://www.ubuntuforums.org/showthread.php?t=26483)
That should get u all set.

---

