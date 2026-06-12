---
title: "HOWTO - Transmission Bittorrent client without compiling from source"
date: 2006-08-26
forum: General Help
---

### Post by amgeex on 2006-08-26
**NOTE:** The forum wouldn't let me post this in the HowTo section, so I posted it here and I kindly ask if it can be moved to the right section, thanks!

This are instructions to download and install the Transmission Bittorrent client on Ubuntu Dapper Drake (tested on 6.06.1).

**Download the Dapper packages from:**

[http://acorbeaux.free.fr/packages/](http://acorbeaux.free.fr/packages/)
[http://gir.deefa.com/debian/transmission/](http://gir.deefa.com/debian/transmission/)

The first link has the most recent version built based on snapshots from the transmission homepage.

The second link hosts several other packages, but it hosts the recommended one for dapper, which is transmission_0.6.1-1_i386.deb

**How to install:**

Just double click on the .deb file you downloaded and the package installer should start up, install the package and notify you that it has been successfully installed.

**How to start Transmission:**

Open up a terminal by going to Applications > Accesories > Terminal and type:
```
transmission-gtk
```
Additionaly, you could make a launcher in your desktop with the following properties: See attached image.

**How to set Transmission as your default Bittorrent client for Firefox:**

1. Navigate to your favorite bittorrent tracker.

2. Find a torrent you want to download and click it.

3. Firefox's download window should pop up with two options: Open with and Save to Disk. Make shure Open with is selected, now, click on the drop down list and select 'other'. Now on the left pane click 'Filesystem' and navigate to /usr/local/bin and select 'transmission-gtk', click open, and you're almost done. Now just tick the 'Do this automatically for files like this from now on.' option and click 'Ok'. Done!

Hope you find this helpfull! :D

---

