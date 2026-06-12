---
title: "Desktop shortcut to start exe with Wine"
date: 2013-01-25
forum: General Help
---

### Post by hornetster on 2013-01-25
Not sure if this is possible, but wondering if a desktop shortcut can be created, that when an *.EXE file is drag'n'dropped onto it, it will start with Wine...?
ie the >Property>Application info would be somrthing similar to:
Command = "usr/bin/wine %u" (which obviously DOESN"T work...
Thanks.

---

### Post by mcduck on 2013-01-25
"%u" is the variable for an URL. Try "%f" instead... ;)

edit:
> 
%f 	a single filename.
%F 	multiple filenames.
%u 	a single URL.
%U 	multiple URLs.
%d 	a single directory. Used in conjunction with %f to locate a file.
%D 	multiple directories. Used in conjunction with %F to locate files.
%n 	a single filename without a path.
%N 	multiple filenames without paths.
%k 	a URI or local filename of the location of the desktop file.
%v 	the name of the Device entry.


---

### Post by mc4man on 2013-01-25
Some wine apps will need a little more help to actually open with/on the file being dropped.
If that's the case then then adding a Z:%f to end of wine launch command will do that

a couple of examples
open & play in foobar2000
```
[Desktop Entry]
Name=foobar2000
Exec=wine "C:\\Program Files (x86)\\foobar2000\\foobar2000.exe" Z:%f
Type=Application
Path=/home/doug/.wine/dosdevices/c:/Program Files (x86)/foobar2000
Icon=3C17_foobar2000.0
```

append in foobar2000
```
[Desktop Entry]
Name=Append in Foobar
Exec=wine "C:\\Program Files (x86)\\foobar2000\\foobar2000.exe" /add Z:%f
Type=Application
Path=/home/doug/.wine/dosdevices/c:/Program Files (x86)/foobar2000
Icon=3C17_foobar2000.0
```

open in photoshop 7.0 
```
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Exec=wine "C:\\Program Files\\Adobe\\Photoshop 7.0\\Photoshop.exe" Z:%f 
Name=Open in Photoshop
NoDisplay=true
Path=/home/doug/.wine/dosdevices/c:/Program Files/Adobe/Photoshop 7.0
Icon=/home/doug/.local/share/icons/cc22_photoshop.0.png
```

(there are several variations of an Exec= for wine program launchers, the above work well when just using the default WINEPREFIX of /home/username/.wine
All launchers on the Desktop need to be marked as executable to show icon

---

