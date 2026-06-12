---
title: "emulator won't run from application menu"
date: 2014-05-30
forum: General Help
---

### Post by nLpPyXR on 2014-05-30
after using ```
gksudo pcmanfm
``` to create a punes32.desktop file in /usr/share/applications ```
[Desktop Entry]
Exec=/home/my_name/punes32.exe
Icon=
Type=Application
Terminal=false
Name=puNES
GenericName=puNES
StartupNotify=false
Categories=Game
``` and verifying puNES got added to my games sub-menu, I tried running it and nothing happened. It's not the emulator as it works perfectly fine by just double-clicking the icon in my home folder.

What am I missing or doing wrong?

---

### Post by deadflowr on 2014-05-30
Is it a windows program?
(the .exe usually means so.)

Then try adding wine to the start of the command.
```
wine /path/to/file
```
see if that does anything.

---

### Post by nLpPyXR on 2014-05-30
it's not a windows program. The problem was that I was including the .exe extension when there isn't one.

Apparently, Linux and (L)Ubuntu are so avanced that executables need no extension to actually run because everything works fine now that I changed the path to just Exec=/home/my_name/punes32

Anyway, thread solved.

---

### Post by deadflowr on 2014-05-30
Well that's a lol.
But yeah, linux files run typically based on type of file versus a need to have an extension for it.
Case in point I have several pictures which don't have any extensions. Yet clicking on them always opens the image viewer and not something like a text editor.

Some programs might need the files to have extensions, though.

---

