---
title: "Making a graphic icon for a program"
date: 2015-03-12
forum: General Help
---

### Post by michael-piziak on 2015-03-12
I downloaded an older version of Snes9x that works on Ubuntu 14.04 LTS.

How do I add a graphic icon to it, and then how do I put that graphic icon to the dock on the left.

---

### Post by michael-piziak on 2015-03-12
Update:  I now see an icon show up on the dock when I double click Snes9x (see attached screen shot).

However, when I lock that icon to the dock, it really doesn't get locked there on reboot and also it will not launch Snes9x if clicked.

---

### Post by CantankRus on 2015-03-13
You would need to create a **snes9x.desktop** file in **~/.local/share/applications** something like the following
which is the **/usr/share/applications/snes9x.desktop** installed by the deb file from the ppa below....
```
[Desktop Entry]
Name=Snes9x
Comment=Super NES Emulator
Type=Application
Categories=Game;Emulator;
MimeType=application/x-snes-rom;
[COLOR="#FF8C00"]Exec=[/COLOR]snes9x-gtk %F
[COLOR="#FF0000"]Icon=[/COLOR]snes9x
```

If you create your own **snes9x.desktop** file you would need to use a path to an icon in the line [COLOR="#FF0000"]Icon=[/COLOR]
If you are running snes9x-gtk from a folder you would have to edit the [COLOR="#FF8C00"]Exec=[/COLOR] line
to something like...
```
[COLOR="#FF8C00"]Exec=[/COLOR]**sh -c "cd ~/Desktop/snes9x-1.52 && ./snes9x-gtk"**
```
or
```
[COLOR="#FF8C00"]Exec=[/COLOR]**/home/[COLOR="#EE82EE"]glen[/COLOR]/Desktop/snes9x-1.52/snes9x-gtk**
```
[COLOR="#EE82EE"]Your username[/COLOR].
Whatever **command** you use test in terminal first.
eg I created this **~/.local/share/applications/snes9x.desktop** file that shows in a dash search for snes
and can be dragged and dropped to the launcher....
```
[Desktop Entry]
Name=Snes9x
Comment=Super NES Emulator
Type=Application
Categories=Game;Emulator;
MimeType=application/x-snes-rom;
Exec=sh -c "cd /home/[COLOR="#EE82EE"]glen[/COLOR]/Desktop/snes9x-1.52 && ./snes9x-gtk"
Icon=/home/[COLOR="#EE82EE"]glen[/COLOR]/Desktop/snes9x-1.52/data/snes9x.svg
GenericName[en_AU]=snes
``` 
[COLOR="#EE82EE"]Your username[/COLOR]

Any reason not to install using the deb from this ppa ... [https://launchpad.net/~bearoso/+archive/ubuntu/ppa/+packages](https://launchpad.net/~bearoso/+archive/ubuntu/ppa/+packages)
then its all done for you.
I know nothing about snes9x and don't know if it will actually work but using the deb file, it installs and opens.

---

