---
title: "Problem running script with hot key"
date: 2018-06-20
forum: General Help
---

### Post by brombo on 2018-06-20
I am running ubuntu 16.04.  I have a script I wish to run with a hot key.  The script is playrecord.sh -

```
#!/bin/sh
# This shell script is PUBLIC DOMAIN. You may do whatever you want with it.

TOGGLE=$HOME/.playrecord

if [ ! -e $TOGGLE ]; then
    touch $TOGGLE
    ecasound -i alsahw,0,0 -o alsahw,0,1 >/dev/null &
    vestax.py &
else
    rm $TOGGLE
    pkill vestax.py
    pkill ecasound
fi
```

The script routes line in to my speakers so I can play my old records "ecasound -i alsahw,0,0 -o alsahw,0,1 >/dev/null &"  and displays a picture of a record player while executing "vestax.py &."  It is set to toggle the programs on and off.  The script is executable and if I run it from a terminal it works. It is in my path so that playrecord.sh is all you need to type.  If I associate "playrecord.sh" with a hotkey (F12) the picture of the record player is displayed the first time I press F12 and it disappears the second time I press F12 but ecasound does not appear to be executed.  It was when I typed playrecord.sh from the command line.  The only thing I noticed when executing the script from the command line is that after executing the cursor is no longer focussed in the terminal and I have to refocus it before executing playrecord.sh the second time.  The program  vestax.py is -

```
#!/usr/bin/python

import Tkinter as tk
from PIL import ImageTk, Image

#This creates the main window of an application
window = tk.Tk()
window.title("Play Vinyl")
window.geometry("730x431")
window.configure(background='grey')

path = "/home/brombo/PlayVinyl/vestax.jpg"

#Creates a Tkinter-compatible photo image, which can be used everywhere Tkinter expects an image object.
img = ImageTk.PhotoImage(Image.open(path))

#The Label widget is a standard Tkinter widget used to display a text or image on the screen.
panel = tk.Label(window, image = img)

#The Pack geometry manager packs widgets in rows or columns.
panel.pack(side = "bottom", fill = "both", expand = "yes")

#Start the GUI
window.mainloop()
```


If I comment out vestax.py in the script the hotkey still does not work.  Any suggestions would be appreciated.

---

### Post by nlee2 on 2018-06-20
try setting TERM at the beginning of playrecord.sh

```
#!/bin/sh
# This shell script is PUBLIC DOMAIN. You may do whatever you want with it.
TERM=xterm
TOGGLE=$HOME/.playrecord

if [ ! -e $TOGGLE ]; then
    touch $TOGGLE
    ecasound -i alsahw,0,0 -o alsahw,0,1 >/dev/null &
    vestax.py &
else
    rm $TOGGLE
    pkill vestax.py
    pkill ecasound
fi
```

---

