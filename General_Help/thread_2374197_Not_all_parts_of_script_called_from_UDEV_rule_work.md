---
title: "Not all parts of script called from UDEV rule work"
date: 2017-10-13
forum: General Help
---

### Post by a-pocklington on 2017-10-13
[COLOR=#111111][FONT=Ubuntu]I'm trying to make a udev rule to disable my laptop keyboard when an external keyboard is connected. So far I have the following script which works when I call it directly.
[/FONT][/COLOR]
```

[FONT=courier new]#!/bin/bash
export DISPLAY=":0"
export XAUTHORITY="/run/user/1002/gdm/Xauthority"
echo $XAUTHORITY >> /home/apockli/list
echo helloX >> /home/apockli/list
echo `which git` >> /home/apockli/list
echo `/usr/bin/git status` >>/home/apockli/list
echo `/usr/bin/xinput list` >> /home/apockli/list
/usr/bin/xinput float `/usr/bin/xinput list | awk '/Apple/' | sed -r 's/.*id=([0-9]+).*/\1/g'`
echo `/usr/bin/xinput list` >> /home/apockli/list[/FONT]
```[COLOR=#111111][FONT=Ubuntu]
When run by actually connecting the keyboard the list file contains the following:[/FONT][/COLOR]

```

[FONT=courier new]/run/user/1002/gdm/Xauthority
helloX
/usr/bin/git
*<Some trailing blank lines>*[/FONT]
```[COLOR=#111111][FONT=Ubuntu]
I really don't understand why [FONT=courier new]which git[/FONT] works but [FONT=courier new]/usr/bin/git status[/FONT] doesn't and the [FONT=courier new]xinput[/FONT] commands neither get written to the file or actually end up disabling the keyboard.  Obviously, I don't really care about the [FONT=courier new]git[/FONT] commands only the [FONT=courier new]xinput[/FONT] ones.  I was just hoping a "simpler" command would work.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Any help would be greatly appreciated as I've already spent way too long trying to get this to work.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
Thanks[/FONT][/COLOR]

---

### Post by vasa1 on 2017-10-13
Please used code tags for content derived from the terminal or for text that needs non-proportional fonts.

---

### Post by a-pocklington on 2017-10-13
Sorry, done.

---

