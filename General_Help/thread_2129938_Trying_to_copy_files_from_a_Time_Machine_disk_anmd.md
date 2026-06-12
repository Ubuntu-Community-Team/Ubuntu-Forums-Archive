---
title: "Trying to copy files from a Time Machine disk anmd I found this..."
date: 2013-03-27
forum: General Help
---

### Post by Silverflyer on 2013-03-27
Someone wrote this to help, I am not sure how to use it.  Can anyone here help me out?  I am a Linux noob.


[https://gist.github.com/vjt/5183305/download#](https://gist.github.com/vjt/5183305/download#)

---

### Post by jonobr on 2013-03-27
Id like to help you, but I would rather not download files to my computer, what are you trying to do

---

### Post by schragge on 2013-03-27
@**jonobr**
No need to download, the code is browsable online:
[https://gist.github.com/vjt/5183305](https://gist.github.com/vjt/5183305)

@**Silverflyer**
It's a bash script. Download, unpack, set execute permission:
```
chmod +x copy-from-time-machine.sh
```
Run from command line with
```
./copy-from-time-machine.sh [COLOR=blue]source[/COLOR] [COLOR=blue]destination[/COLOR]
```

---

### Post by Silverflyer on 2013-03-27
> **schragge said:**
> @**jonobr**
No need to download, the code is browsable online:
[https://gist.github.com/vjt/5183305](https://gist.github.com/vjt/5183305)

@**Silverflyer**
It's a bash script. Download, unpack, set execute permission:
```
chmod +x copy-from-time-machine.sh
```
Run from command line with
```
./copy-from-time-machine.sh [COLOR=blue]source[/COLOR] [COLOR=blue]destination[/COLOR]
```

Alright, I hate to bother but you need to be clear, exactly how do I do that?  It is extracted in my downloads folder right now.

What I am trying to do is copy my music folder from itunes to my linux computer.  Sadly, the Time Machine backup drive is all I have to do that with.  I will never use Time Machine again.

edit: according to this it is already set to be executable:  [IMG]http://img594.imageshack.us/img594/9669/screenshotfrom201303271.png[/IMG]

---

### Post by Frogs Hair on 2013-03-27
I used time machine back on 9.10 to move a backup to a new installation and it was not recognized with the same user name and password . It may have been my fault, but I don't know and have not tried it since. I had mainly gedit documents and gedit on the new installation didn't recognize most of the documents. Deja Dup became default not long after that.

---

### Post by schragge on 2013-03-28
@**Silverflyer**
Sorry for being not clear. Yes, you are right, the script already has appropriate permissions. It is supposed to be launched from terminal. You can open a terminal window by pressing **Ctrl**+**Alt**+**t. **See [uhelp]community/UsingTheTerminal[/uhelp], [uhelp]community/GnomeTerminal[/uhelp], [GNOME Terminal Manual]("https://help.gnome.org/users/gnome-terminal/3.6/gnome-terminal-get-started.html.en").

When in terminal, start the script with the following command:
```
~/Downloads/copy-from-time-machine.sh [COLOR=blue]/path/to/time/machine/backup/drive[/COLOR] [COLOR=blue]path/to/local/music/folder[/COLOR]
``` Replace the [COLOR=blue]blue[/COLOR] parts accordingly. Your TimeMachine drive is probably mounted somewhere under */media/*, your music folder is probably *~/Music*.

---

