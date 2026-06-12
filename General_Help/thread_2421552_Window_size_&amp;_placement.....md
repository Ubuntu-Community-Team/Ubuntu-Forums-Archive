---
title: "Window size &amp; placement...."
date: 2019-06-23
forum: General Help
---

### Post by Furycd001 on 2019-06-23
HI

I have this one file that I open in atom and I want it to always open a certain size & place. Atom for me seems to save the window size & placement by default which is great, but then all windows open at this same size & position. I only want this one certain file to open this size & placement NOT all files. I want EVERY other file to open the same size & placement bar this one.

I open the file through **CTRL+ALT+A** keybinding with the following command.
```
atom /home/furycd001/Mezzamorphis/Glo/Delirious.md
```

I found xdotool & can use the code below to get atoms id.
```
xdotool search --onlyvisible --name atom
```

I can then use the code below to set the window size & placement for atom.
```
xdotool search --onlyvisible --name atom && xdotool windowsize 83886081 800 400 && xdotool windowmove 83886081 1090 480
```

The problem is that the id seems to change every time I close atom. How can I go about this and is there a way to easily accomplish this ??

---

### Post by TheFu on 2019-06-23
I don't use atom, but well-written X/Windows applications support -geometry options, so
```
uxterm -sb -geometry 80x25+0+0  -e ssh -X hadar &
```
will open a uxterm, with a scrollbar at the specific location, run an ssh login with X11 forwarding.
Sadly, GTK has decided that X11 options aren't worth implementing (which really means just *not* getting in the way of the libX11 implementations that are used.

---

### Post by Furycd001 on 2019-06-24
Thanks for this comment. I completely overlook "-geometry" but it doesn't work with atom anyway....

---

### Post by Furycd001 on 2019-06-25
Updated my code to be called from a script, but still no luck. Atom opens, but the window size & position are left untouched. The method I used in my first post works, but the problem still is that the id for atom seems to change every time it's closed & opened....

```

#!/bin/bash

atom /home/furycd001/Sites/Lacey\ Laney/Markdown.md && /bin/sleep 4 | xdotool search --onlyvisible --name atom | xargs -I{} xdotool windowsize {} 800 400
```

---

### Post by again? on 2019-06-25
I think your first pipe should be &&.
eg
```
atom /home/furycd001/Sites/Lacey\ Laney/Markdown.md && /bin/sleep 4 [COLOR="#FF0000"]&&[/COLOR] xdotool search --onlyvisible --name atom | xargs -I{} xdotool windowsize {} 800 400
```

---

### Post by TheFu on 2019-06-25
Perhaps using the "Class" instead of using the "name" option?

When I need Chromium full screen, this is what works:
```
chromium-browser --app=http://some.great.website.com/
sleep 3;
xdotool search --sync --onlyvisible --class "Chromium" windowactivate key F11
```
I only have 1 window, so don't need to tell 20 windows to resize.

---

### Post by again? on 2019-06-25
Also looking at my old notes if the last window was maximized you have to remove the maximized state first or it won't resize.
I used to use wmctrl to do this.
Open atom and get a window list.
```
wmctrl -xl
```
You should have a line similar to 
```
0x06200001  0 [COLOR="#FF0000"]atom.Atom[/COLOR]             Bionic Welcome Guide — ~ — Atom
```

Use the third column to define your window.

eg
```
#!/bin/bash 

atom /home/furycd001/Sites/Lacey\ Laney/Markdown.md
sleep 4

## removes max states then resizes and positions
wmctrl -xa [COLOR="#FF0000"]atom.Atom[/COLOR] -b remove,maximized_vert,maximized_horz && wmctrl -xa [COLOR="#FF0000"]atom.Atom[/COLOR] -e 0,450,260,800,400
```
See [**HERE**]("https://ubuntuforums.org/showthread.php?t=1942500&p=11776457#post11776457") for info on the wmctrl  -e 0,450,260,800,400 values


You could also bind a shortcut key to a script to resize and reposition the active window.
```
#!/bin/bash

wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz && wmctrl -r :ACTIVE: -e 0,450,260,800,400
```

---

### Post by Furycd001 on 2019-06-25
> **guber2 said:**
> Also looking at my old notes if the last window was maximized you have to remove the maximized state first or it won't resize.
I used to use wmctrl to do this.
Open atom and get a window list.
```
wmctrl -xl
```
You should have a line similar to 
```
0x06200001  0 [COLOR=#FF0000]atom.Atom[/COLOR]             Bionic Welcome Guide — ~ — Atom
```

Use the third column to define your window.

eg
```
#!/bin/bash 

atom /home/furycd001/Sites/Lacey\ Laney/Markdown.md
sleep 4

## removes max states then resizes and positions
wmctrl -xa [COLOR=#FF0000]atom.Atom[/COLOR] -b remove,maximized_vert,maximized_horz && wmctrl -xa [COLOR=#FF0000]atom.Atom[/COLOR] -e 0,450,260,800,400
```
See [**HERE**]("https://ubuntuforums.org/showthread.php?t=1942500&p=11776457#post11776457") for info on the wmctrl  -e 0,450,260,800,400 values


You could also bind a shortcut key to a script to resize and reposition the active window.
```
#!/bin/bash

wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz && wmctrl -r :ACTIVE: -e 0,450,260,800,400
```

Thank you for this very detail comment. Using this code opens the file in atom, but the window is neither re-sized or moved position. Any ideas ??

---

### Post by Furycd001 on 2019-06-25
Atom is somewhat strangly developed, but I managed to solve my problem. Here's the code for anyone that's interested....

```

#!/usr/bin/env bash
# Run the command and fork it into the background, after grabbing its PID
atom /home/furycd001/Sites/Lacey\ Laney/Markdown.md

# Poll until the command spawned a window, then get its window ID
for ((;;)); {
    wIDs=$(xdotool search --onlyvisible --name Atom 2> /dev/null) && break
}

# Resize known windows
for wID in $wIDs; {
    xdotool windowsize $wID 800 400
}

# Moves known windows
for wID in $wIDs; {
    xdotool windowmove $wID 1090 480
}

```

---

