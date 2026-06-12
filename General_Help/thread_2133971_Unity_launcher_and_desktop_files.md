---
title: "Unity launcher and desktop files"
date: 2013-04-09
forum: General Help
---

### Post by Zestypanda on 2013-04-09
Hello, I'm scratching my head trying to figure out how to make/edit a right click option for a program that is pinned in the unity launcher. I have libre office (awesome by the way) and I'm trying to figure out how I can add an option to the main launcher that when right clicked lists " create new speadsheet" "create new presentation" etc basically circumventing having to left click on it and wait for the main thing to synch and without cluttering up my launcher with each individual launcher for impress, writer, calc etc.

---

### Post by kuifje09 on 2013-04-09
I think I do not understand what you want. But if you open LibreOffice, it starts with a chooser to let you choose for any type it knows of. Why the need for an extra set of "buttons" ? Or do I miss your goal?
But Maby its is special releted to Unity. I only work in classic mode without efects.

---

### Post by Zestypanda on 2013-04-09
No, this is NOT related to fallback mode or 2d, this pertains to a feature that is only available on unity launcher 3d, when you right click a program it shows quick menu options.

---

### Post by mc4man on 2013-04-09
Pretty simple with several variations, will give one here & you can take from there.

Assuming you have the libreoffice start center icon in the launcher so to put back with some quicklists - 
First remove it from the launcher (r. click > unlock

Then open a terminal, copy & paste this command
```

mkdir -p ~/.local/share/applications && gedit ~/.local/share/applications/libreoffice.desktop
```

copy & paste this into gedit, save, close gedit
```
[Desktop Entry]
Version=1.0
Terminal=false
Icon=libreoffice-startcenter
Type=Application
Categories=Office;X-Red-Hat-Base;X-SuSE-Core-Office;X-MandrivaLinux-Office-Other;
Exec=libreoffice %U
MimeType=application/vnd.openofficeorg.extension;
Name=LibreOffice
GenericName=Office
Actions=Docu;Pres;Draw;Spread;

[Desktop Action Docu]
Name=New Document
Name[en]=New Document
Exec=libreoffice --writer %U
TargetEnvironment=Unity

[Desktop Action Pres]
Name=New Presentation
Name[en]=New Presentation
Exec=libreoffice --impress %U
TargetEnvironment=Unity

[Desktop Action Draw]
Name=New Drawing
Name[en]=New Drawing
Exec=libreoffice --draw %U
TargetEnvironment=Unity

[Desktop Action Spread]
Name=New Spreadsheet
Name[en]=New Spreadsheet
Exec=libreoffice --calc %U
TargetEnvironment=Unity
```

Then back in the terminal
```
nautilus ~/.local/share/applications/
```
You'll see libreoffice.desktop inside, grab with cursor & drag on to the unity launcher

The order of the quicklist items is determined by the order of the actions on this line
Actions=Docu;Pres;Draw;Spread;
So if desired switch them, ex, - 
Actions=Pres;Docu;Spread;Draw;

This .desktop (launcher icon) will still open the start-center when l. clicked on, a  variation of above would be to have it open your most used LO app & quicklists for the others
(if wanting that instead post which app

---

### Post by Zestypanda on 2013-04-10
Aww thanks guys ^_^ I will test this later, I have tests tomorrow so I should probably get to bed some time before 1am :P Though, this seems to be what I was looking for.

---

### Post by Zestypanda on 2013-04-10
Yay that did the trick ^_^

---

### Post by Zestypanda on 2013-04-12
On another note I seem to have messed up my home folder .-. So I re created the folders (pictures, videos, documents, downloads) but when I select "change desktop wallpaper" and do "pictures folder" the newly created folder in my home directory which has pics, they pics do not show up under is list. Furthermore, is there a way I can add a search icon to the unity top bar similar to the finder icon in OSX? Aha! It's indicators, that's what I mean, yeah how do I get a search shortcut indicator for my files? Like the search function in nautilus.

---

### Post by Zestypanda on 2013-04-12
Um...seems like unity is broken now, and when I try to reinstall it it says unsupported hardware when I know it worked just fine 4 hours ago

---

