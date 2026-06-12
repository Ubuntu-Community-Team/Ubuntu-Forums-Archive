---
title: "Opening Terminal from Context Menu"
date: 2014-05-15
forum: General Help
---

### Post by TheCO2 on 2014-05-15
I have been using a Firefox addon, for a while, called "[Advanced URL Builder]("http://www.jamescookie.com/extensions/aub.html")." It allows me to highlight context and use that for my custom search or open unlinked URLs in a new tab (if Linkification doesn't catch it). I was wondering if there was a way I could configure it as a launcher or if anyone knows of a Firefox addon (or other way) to do that.

I was hoping to be able to open code, in context, straight to a Terminal window without having to go through the copy/paste.

---

### Post by grumblebum2 on 2014-05-15
Not entirely sure what you want to achieve here, but you may be able to use **xsel**.
By default xsel copies the primary or middle click buffer. To use with the secondary copy/paste buffer use **xsel --clipboard**

Here's an example how I use xsel to add highlighted text  to my Notes file.
```
echo $(xsel) >> /media/Data/Notes
```
The command adds highlighted text to my Notes file. (See the last  quicklist section below).

My edited gnote.desktop launcher placed in **~/.local/share/applications**...
```
[Desktop Entry]
Name=Gnote
Comment=Take notes, link ideas, and stay organized
GenericName=Note-taker
Exec=gnote %u
Icon=gnote
MimeType=x-scheme-handler/note;
StartupNotify=true
Terminal=false
Type=Application
Categories=GNOME;GTK;Utility;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gnote
X-GNOME-Bugzilla-Component=main
X-GNOME-Bugzilla-Version=3.6.1

Actions=new;scribbles;search;addtoNotes;

Name[en_AU]=gnote

[Desktop Action new]
Name=New Note
Exec=gnote --new-note
OnlyShowIn=Unity;

[Desktop Action scribbles]
Name=Scribbles
Exec=gnote --open-note Scribbles
OnlyShowIn=Unity;

[Desktop Action search]
Name=Search Selection
Exec=sh -c "gnote --search $(xsel)"
OnlyShowIn=Unity;

[Desktop Action addtoNotes]
Name=Add Selection to Notes
**Exec=sh -c "echo $(xsel) >> /media/Data/Notes"**
OnlyShowIn=Unity;
```

Any .desktop file copied from **/usr/share/applications** and place in **~/.local/share/applications** will override the original.

---

### Post by TheCO2 on 2014-05-15
Basically, what I want is to be able to highlight and be able to open a context menu and send the highlighted to Terminal, or something similar.  Kind of like the terminal Terminal middle click, but from Firefox.

I thought I understood what you were doing, but I think I am just confusing myself (or doing it wrong).  I installed gnote, tried editing **gnote.desktop** (with gedit) and saving it to  **~/.local/share/applications**, but it's not working.  
I wanted to see if I could get your trick to work.  If it did, I was going to try replacing all instances of gnote with gnome-terminal, if it was kind of what I was looking for.

FYI: I am on Mint and have only been using it for about 2 weeks.

---

### Post by grumblebum2 on 2014-05-16
> **TheCO2 said:**
> Basically, what I want is to be able to highlight and be able to open a context menu and send the highlighted to Terminal, or something similar.  Kind of like the terminal Terminal middle click, but from Firefox.

I thought I understood what you were doing, but I think I am just confusing myself (or doing it wrong).  I installed gnote, tried editing **gnote.desktop** (with gedit) and saving it to  **~/.local/share/applications**, but it's not working.  
I wanted to see if I could get your trick to work.  If it did, I was going to try replacing all instances of gnote with gnome-terminal, if it was kind of what I was looking for.

FYI: I am on Mint and have only been using it for about 2 weeks.

What I showed you was just an example of how I customized my gnote quicklists. 
You don't need gnote. You would use that method with the **/usr/share/applications/firefox.desktop** file.


The outcome isn't really much better than opening a terminal and middle click paste.
If you don't fully understand what I said I wouldn't worry about it.
I don't even know if the launcher application in Mint supports unity quicklists.

There is an extension [**_[COLOR="#B22222"]TerminalRun[/COLOR]_**]("https://addons.mozilla.org/en-US/firefox/addon/terminalrun/?src=ss") but it doesn't work with the latest firefox. 
I wouldn't use anyway  as I think it's dangerous to run commands in this way.

---

### Post by TheCO2 on 2014-05-16
It was worth a shot.  Thanks for your time. :)

---

### Post by grumblebum2 on 2014-05-16
> **TheCO2 said:**
> It was worth a shot.  Thanks for your time. :)
Ok no problem.
While I was looking into this I made a little script to open a terminal and paste in the middle click buffer.
Needs xsel and xdotool installed.
May be able to use it.
Again, if you don't understand how to use it, don't worry about it.

_xsel-terminal.sh_
```
#!/bin/bash

gnome-terminal --geometry 103x11+331+14 &
sleep 2
xdotool type "$(xsel)"
#xdotool key Return
exit 0 
```

---

