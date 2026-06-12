---
title: "x doesn't start, lock file created"
date: 2007-12-05
forum: General Help
---

### Post by pickarooney on 2007-12-05
Bit of an annoying problem since I upgraded to Gutsy - on bootup I get a black screen and have to drop to a console. If I startx I get an error message saying X is already started and a /tmp lock file created. If I delete this lock file I can start X... so why doesn't it start properly on startup?

---

### Post by pointone on 2007-12-06
When it drops you to a console, do you see any error messages? What happens if you press Ctrl+Alt+F7? (Press Ctrl+Alt+F1 to return to the console if this doesn't work.)

---

### Post by pickarooney on 2007-12-06
It doesn't drop me to a console; I have to ctrl-alt-F1 after 5 minutes of blank, black screen. No error message of note on the console screen and ctrl-alt-F7 sends me back to a blank screen.

---

### Post by geraldm on 2007-12-06
When X fails to start there is an error log, usually in home directory ~/.xsession-errors.

Gerald

---

### Post by pickarooney on 2007-12-12
```
startkde: Done.
Xsession: X session started for pickarooney at Wed Dec 12 21:31:00 CET 2007
startkde: Starting up...
startkde: kpersonalizer not found! Please install to properly configure your user.
kbuildsycoca running...
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/firefox/plugins/libjavaplugin.so: undefined symbol: NP_GetValue
nspluginscan: WARNING: Plugin doesn't implement NP_GetValue
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/firefox/plugins/libjavaplugin.so: undefined symbol: NP_GetMIMEDescription
Ignored duplicate item: KDE Groupware Wizard
Ignored duplicate item: Kontact
Ignored duplicate item: KArm
Ignored duplicate item: KDE Groupware Wizard
Ignored duplicate item: KNotes
Ignored duplicate item: Strigi
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/mozilla/plugins/libjavaplugin.so: undefined symbol: NP_GetValue
nspluginscan: WARNING: Plugin doesn't implement NP_GetValue
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/mozilla/plugins/libjavaplugin.so: undefined symbol: NP_GetMIMEDescription
Ignored duplicate item: Un bébé au naturel | Provence - Lubéron
Could not find 'guidance-power-manager.py' executable.
konsole: WARNING: Unable to use /usr/share/apps/konsole/mc.desktop
konsole: WARNING: Unable to use /usr/share/apps/konsole/sumc.desktop
kdecore (KProcess): WARNING: _attachPty() 11
kdecore (KProcess): WARNING: _attachPty() 13
kbuildsycoca running...
Reusing existing ksycoca
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x80df4c8 ): KAccel object already contains an action name "file_quit"
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x80df4c8 ): KAccel object already contains an action name "file_quit"
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x2603ad2

```

That's the latest output to .xsession-errors. Nothing seems to jump out. Also, nothing was written to it today until after I deleted the lock file and started X manually.

---

### Post by pickarooney on 2007-12-13
could it be that kdm is misconfigured and tries to display on a non-existent external monitor? I remember pressing a key that looks two tv screens ob the laptop keyboard not long ago, without knowing what it was for...

---

### Post by pickarooney on 2007-12-17
Anyone got any more suggestions?

---

### Post by pickarooney on 2008-04-30
Anyone?
I reformatted to fix this back in December. Now I've upgraded to Hardy and have the same problem again. I'd like to avoid reformatting.

---

### Post by pickarooney on 2008-04-30
Anyone?
I reformatted to fix this back in December. Now I've upgraded to Hardy and have the same problem again. I'd like to avoid reformatting.

---

### Post by pickarooney on 2008-06-06
just bumping this for one last cry for help before reformatting. I've spent a month looking and posting on 5 forums and nobody's come up with a solution. I would have fixed it in half an hour if I'd just formatted again from the get-go, but I want to know how to sort this out next time I upgrade and it screws up again.

---

