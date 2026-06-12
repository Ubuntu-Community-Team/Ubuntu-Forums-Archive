---
title: "Set media player as default"
date: 2014-12-26
forum: General Help
---

### Post by Otto-C on 2014-12-26
Xubuntu 14.04.1 up to date.

How to set media player as default.
Options are Parole, rhythembox, VLC or any.
The fresh install has gmusicbrowser as default.

tia
otto

---

### Post by Holger_Gehrke on 2014-12-26
You can change the default action for a file-type in Thunar by right clicking and selecting 'properties'. In the dialog is a field "open with".  Select a program from the list.

OR

Edit the file '~/.local/share/applications/mimeapps.list'.

---

### Post by egeezer on 2014-12-26
I think you can find it in the Session and Startup section of the Settings Manager and mark it in the Application Autostart panel.

---

### Post by Otto-C on 2014-12-26
Re thread # 2 mimeapps.list is empty.

Re thread # 3 not mentioned  in the Application Autostart panel. 

Again using Xubuntu 14.04.1

tia
otto

---

### Post by flaymond on 2014-12-26
1. Go to the program you want.
2. Right click - Go to open with...
3. Select the music player you want, and check/tick the "***Set selected*** ***application as default action for this file type ***".
4. It worked if you just wanna run similar file extension like mp4, ogv, mp3 etc.

---

### Post by Holger_Gehrke on 2014-12-27
> **Otto-C said:**
> Re thread # 2 mimeapps.list is empty.

Sorry, that file contains associations made using the first way I described (using the properties dialog). If you've never created or changed a file type association it is of course empty.

The format of the file is a simple ini-style. It has two sections "[Added Associations]" (those show up as choices for "Open with") and "[Default Applications]". In each section are associations of the form "<mimetype>=<desktop file>".

An example:
```

[Added Associations]

[Default Applications]
video/x-msvideo=vlc.dektop
video/x-flv=vlc.desktop
video/mp4=vlc.desktop

```

You can use "mimetype <file>" in the shell to find out the type of a file.

---

### Post by brainwash on 2014-12-27
Settings Manager > MIME Type Editor

[http://docs.xfce.org/xfce/xfce4-settings/mime](http://docs.xfce.org/xfce/xfce4-settings/mime)

---

### Post by Otto-C on 2014-12-27
Guys, Thanks for all the thoughts and how to's.  I think its my machine.

Going to  put this project on hold for now.

---

