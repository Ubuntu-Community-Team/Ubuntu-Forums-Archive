---
title: "AVG  update"
date: 2008-01-19
forum: General Help
---

### Post by nikef on 2008-01-19
Hi all
i am trying to update avg
but it says i don't have permissions  :(
also it will not scan ,i have been searching the forum,but the threads are outdated and they are for fiesty 
can any1 help please

---

### Post by y-lee on 2008-01-19
I don't have AVG and I use Dapper, but ya probably need to run it as superuser to update. 

Btw how did you install AVG? I found this [guide online]("http://www.ubuntugeek.com/install-avg-antivirus-in-ubuntu-desktop.html") it may help. Esp the part:

```
sudo gedit /usr/share/applications/avgupdate.desktop

enter the following lines Save and exit the file

File:/usr/share/applications/avg.desktop
[Desktop Entry]
Name=AVG Updater
Comment=Antivirus
Exec=sudo /opt/grisoft/avg7/bin/avgupdate -o
Icon=/opt/grisoft/avggui/prog/pixmaps/avgupdateico.png
Terminal=true
Type=Application
Categories=Application;System;
```

Looking at that I would think **sudo /opt/grisoft/avg7/bin/avgupdate -o** would actually do the update. But remember I don't have AVG haven't tried it and I am new to linux. Just warning ya.

---

### Post by nikef on 2008-01-19
Thanks
the link has sorted my update out and it has now updated

but does any1 know how i can scan properly 

this is what is says after doing scan

---

### Post by y-lee on 2008-01-19
It is just a guess but those are all system files Ya probably can't open them because they are in use. maybe you could run AVG as superuser but I would not mess around with system files. If I wanted to scan my entire ubuntu partition system files and all  I would do it from outside ubuntu, from my windows partition because i still dual boot or from a Live CD or something. Again this is the blind leading the blind ...  I don't know.

---

### Post by nikef on 2008-01-20
II will scan in win xp,then that should scan my ubuntu files to
thanks for all your help :)

---

