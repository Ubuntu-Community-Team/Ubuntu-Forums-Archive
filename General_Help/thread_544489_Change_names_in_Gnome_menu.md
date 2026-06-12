---
title: "Change names in Gnome menu"
date: 2007-09-06
forum: General Help
---

### Post by Hallvor on 2007-09-06
Hi,

I noticed that there is a misspelling in the Norwegian Gnome menu (Applications->Accessories). I find this annoying. Is there any way for me to alter the name of Accessories in Norwegian? The translation is "Tillegsverkty", but the correct spelling should be "Tilleggsverkty"...

So, is it possible to change it?

---

### Post by aJayRoo on 2007-09-06
Yes it should be possible. You should use the menu editor (System -> Preferences -> Main Menu), sorry I only know the English for that! When it loads up, look in the right hand section , there you can right click on Accessories and choose properties. The properties dialog box has a field for changing the name.

Some points to note: I see you are a Dapper user, in this case the menu editor may be in a different place or have a different name. I think you should be able to find it but if not try typing:
```
alacarte
``` into a terminal or the Alt-F2 run dialog.
Also the application (alacarte) has a tendency to show its dialog boxes behind the main screen which is annoying when you are looking for the dialog that you think should have opened!

Hope that helps!

---

### Post by Hallvor on 2007-09-06
Actually, alacarte was the first I tried, but there was no option to rename the menu items. So after searching the web a little I found out that the items were located in .directory files.

So I opened up the terminal and wrote
```

locate .directory
```

I then located the files in /usr/share/desktop-directories

Then I used the terminal to open Nautilus in root-mode:
```

sudo nautilus
```

After opening /usr/share/desktop-directories I saw the misspelt file name (with menu icon) and renamed the file correctly with a right click -> rename file.

Problem solved! :)

---

### Post by aJayRoo on 2007-09-06
Ah right, when I saw that it was possible to change the name of a menu in alacarte I automatically assumed that it would work! I now realise it does not! I'm glad you got it sorted any way.

---

