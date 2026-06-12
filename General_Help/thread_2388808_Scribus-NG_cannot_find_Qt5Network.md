---
title: "Scribus-NG cannot find Qt5Network"
date: 2018-04-07
forum: General Help
---

### Post by Timokl on 2018-04-07
Hi, 

After updgrading to Ubuntu 17.10, I had to re-install Scribus. On Ubuntu 17.04 I used the development version 1.5.3 from this PPS ([https://launchpad.net/~scribus/+archive/ubuntu/ppa](https://launchpad.net/~scribus/+archive/ubuntu/ppa)) without a problem.

On 17.10, I added the PPA and installed it through apt-get:

```
sudo apt-get install scribus-ng
```

Then I started the newly-installed Scribus, but come to this error message:

```
timo@grosshirn:~$ scribus-ng
scribus-ng: error while loading shared libraries: libQt5Network.so.5: cannot open shared object file: No such file or directory
```

The mentioned QT module is installed, though.

```
timo@grosshirn:~$ sudo apt-get install libqt5network5
[sudo] Passwort für timo: 
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
**libqt5network5 ist schon die neueste Version (5.9.1+dfsg-10ubuntu1).**
0 aktualisiert, 0 neu installiert, 0 zu entfernen und 11 nicht aktualisiert.
```

I can run the stable release version 1.4.6 without problems.

As a workaround, I tried to run the AppImage version, which works fine at first, but the drop-down menu shows no entries.

How can I make Scribus find the needed QT5Network Module?

Timo

---

### Post by yvandasilva on 2018-09-29
I just had the same problem.
I don't know why, but it seems libQt5 packages and some other packages had some issues, maybe it is a scribus-ng dependency issue. I don't have time to investigate.


Here is what you can do to solve your problem with Scribus-ng (basically, it's a simple reinstall)


On Ubuntu 18.04


sudo apt-get remove --purge scribus-ng scribus-trunk scribus
(Autoremove is optional)
sudo apt-get clean && sudo apt-get autoclean && sudo apt-get autoremove
sudo apt-get install --reinstall scribus-ng libqt5dbus5 libxcb-xinerama0 $(apt-cache depends scribus-ng | \
     grep -Po 'Depends:\s+\K[^ ]+$' | tr '\n' ' ')

---

### Post by yvandasilva on 2018-09-29
Just in case you might also require :
export QT_QPA_PLATFORM_PLUGIN_PATH=/usr/lib/x86_64-linux-gnu/qt5/plugins

This depends on your ENV. which I don't know.

If you have any QT plugin problems you can also do :
export QT_DEBUG_PLUGINS=1
And start your app from a terminal so you see what's going on.

Best regards,

---

