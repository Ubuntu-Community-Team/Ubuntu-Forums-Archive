---
title: "Word LibreOffice stopped working concerning Writer"
date: 2019-03-01
forum: General Help
---

### Post by Timmoore001 on 2019-03-01
I've used LibreOffice for many years, but its suppenly will not open .odt files....

I've no idea what could be wrong...

Its 'Recent' files are now a lot !    Maybe I've exceeded space available maybe.

I have to email the file (having found it in my copy of all 'Data@ files to Linux Lite to gey old files om the screen and print them !!!

I'm using normally Ubuntu 18.04   sometimes 16.04.

I've no idea of how to fix this glitch...

Any thoughts very very welcome,

A stressed 

Tim

---

### Post by ajgreeny on 2019-03-01
> **Timmoore001 said:**
> I've used LibreOffice for many years, but its suppenly will not open .odt files....

I've no idea what could be wrong...

Its 'Recent' files are now a lot !    Maybe I've exceeded space available maybe.

[COLOR="#FF0000"]I have to email the file (having found it in my copy of all 'Data@ files to Linux Lite to gey old files om the screen and print them !!![/COLOR]

I'm using normally Ubuntu 18.04   sometimes 16.04.

I've no idea of how to fix this glitch...

Any thoughts very very welcome,

A stressed 

Tim
What exactly does the red coloured sentence in your post mean?
Do you have to copy the file from an archive somewhere to another system still using LO?

It may be worth fully closing LO then renaming the config folder for LO in your problem machine with command ```
mv .config/libreoffice .config/libreoffice-backup
``` Now try opening the problem files again; perhaps your configuration is corrupt in some way, and this will create a new config for all of LO.

---

### Post by Timmoore001 on 2019-03-01
Many thanks for responding.  Sorry for all the typos.

This :-   [COLOR=#FF0000] have to email the file (having found it in my  copy of all 'Data@ files to Linux Lite to gey old files om the screen  and print them !!![/COLOR] 

should be:-

have to email the file (having found it in my  copy of all 'Data@ files, the file I wanted to read.   I then sent it to myself as an attachment.   Linux Lite on a different computer read it just fine and solved the problem as I could print it out.   But the problem on my main computer was not fixed so far....   a real pain as I do most of my written work on it !

I'm going to remove LibreOffice and reinstall it as an attempt as a fix.   If that doesn't work I may well move over to Linux Lite or a Ubuntu 18.04 Gnome version.

Again many thanks for responding....

: )))

Tim

---

### Post by ajgreeny on 2019-03-01
So did you try renaming the LO config folder as I suggested in post #2?

---

### Post by kc1di on 2019-03-01
A simple reinstall will most likely will not work as it will not erase the config folder that ajgreeny has asked to rename.  Please do what he said first.

---

