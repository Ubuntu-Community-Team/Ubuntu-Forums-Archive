---
title: "FTP   for    KDE"
date: 2006-11-03
forum: General Help
---

### Post by rfruth on 2006-11-03
I switched from  GNOME to KDE  last night,  im impressed with it :KS - what  FTP  client do  KDE users use, Konqueror ?

---

### Post by bionnaki on 2006-11-03
if you ever want to look for an application, open the terminal and run "apt-cache search x" - x being a search query. so, apt-cache search ftp kde resules in:

apt-cache search kde ftp
kdebase-kio-plugins - core I/O slaves for KDE
klinkstatus - web link validity checker for KDE
gambas-gb-net-curl - The Gambas advanced networking component
kasablanca - fast and free ftp client for KDE
kcmpureftpd - KControl module for easily setting up pure-ftpd
kdirstat - graphical disk usage display with cleanup facilities
kftpgrabber - KDE FTP client
konserve - KDE system tray application that performs periodic backups
krusader - twin-panel (commander-style) file manager for KDE (and other desktops)
potracegui - KDE frontend for potrace


try kftpgrabber.
sudo aptitude install kftpgrabber

---

### Post by Jucato on 2006-11-03
Konqueror works well, too. You can even split the view for easier drag and drop. Right-click on the status bar for the split view options.

---

### Post by dresnu on 2006-11-03
I prefer kasablanca. It has a very simple and intuitive UI and I found it more stable than kftpgrabber which crashed on me a couple of times.

---

