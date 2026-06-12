---
title: "How to start an app after installing it from repository using apt install."
date: 2019-01-12
forum: General Help
---

### Post by GwibberFooey on 2019-01-12
I ran the command ```
sudo apt install rtklib-qt
``` and the installation appears to have gone smoothly. Now how can I start the application?
My operating system is Ubuntu-Mate 18.04 for x86-64.

---

### Post by him610 on 2019-01-12
Not familiar with rtk-lib, but if you have *rtklib* installed you could try from the command line
```
rtklib --help
```
You may find more detailed information by downloading and installing *rtklib-doc*

I think you may have a better luck by visiting this website for GNSS: Global Navigation Satellite Systems. It seems that rtklib-qt are the GUI tool parts of GNSS.
[https://gnss-sdr.org/quick-start-guide/]("https://gnss-sdr.org/quick-start-guide/")

---

### Post by again? on 2019-01-13
To show files installed by rtklib-qt, run...
```
dpkg -L rtklib-qt
```

which amongst other files will show the /usr/bin executables...
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] dpkg -L rtklib-qt**
/.
/usr
/usr/bin
[COLOR="#FF0000"]/usr/bin/rtkconv_qt
/usr/bin/rtkget_qt
/usr/bin/rtklaunch_qt
/usr/bin/rtknavi_qt
/usr/bin/rtkplot_qt
/usr/bin/rtkpost_qt
/usr/bin/srctblbrows_qt
/usr/bin/strsvr_qt[/COLOR]
/usr/share
/usr/share/doc
/usr/share/doc/rtklib-qt
/usr/share/doc/rtklib-qt/changelog.Debian.gz
/usr/share/doc/rtklib-qt/copyright
```
[ATTACH=CONFIG]282189[/ATTACH]


[COLOR="#FF0000"]**Edit**[/COLOR]: Having a closer look it appears to have a tray icon activated by /usr/bin/rtklaunch_qt.
Help shows a --tray option which I thought would just start the tray icon but it shows a dialog where you have to click the box bottom right first,
But at any rate, launching from the tray popup doesn't work for me in xfce or gnome.
[ATTACH=CONFIG]282191[/ATTACH]

Best bet would be to make your own launcher.

---

