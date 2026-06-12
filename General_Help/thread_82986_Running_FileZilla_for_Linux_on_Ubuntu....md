---
title: "Running FileZilla for Linux on Ubuntu..."
date: 2005-10-27
forum: General Help
---

### Post by Confuse on 2005-10-27
This is the output I get when I try to run the CVS build of filezilla for linux

damian@pompey:~/filezilla3/bin$ ./filezilla
./filezilla: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.6' not found (required by ./filezilla)


I'm running the latest up to date breezy. Anyone know what to do?

---

### Post by KnottyMan on 2005-10-27
sudo apt-get install libstdc++ will probably do the trick

---

### Post by Confuse on 2005-10-27
Its already installed...Any other ideas?

---

### Post by aysiu on 2005-10-28
Okay. I downloaded the source from the Filezilla main page, and there's no ./configure-ing on this one. The best way to do Filezilla is to install it using Wine. 

[Enable extra repositories](http://www.psychocats.net/sources.html). Then, type this in a terminal ```
sudo apt-get update
sudo apt-get install wine
``` Download the setup.exe file from the Filezilla site and install it by double-clicking it--Wine should be used to install it. Install it to your home directory (/home/Confuse/Filezilla). It'll put a shortcut on your desktop (mine had a command something like ```
wine "z:\home\aysiu\Filezilla\Filezilla.exe"
``` Yours will probably be something similar. Double-click that shortcut, and you're good to go.

To make Filezilla available to all users, I did a ```
gksudo nautilus
``` and copy and pasted the entire Filezilla directory to /usr/local/bin/Filezilla and updated the shortcut with the appropriate new command ```
wine "z:\usr\local\bin\Filezilla\Filezilla.exe"
```

---

