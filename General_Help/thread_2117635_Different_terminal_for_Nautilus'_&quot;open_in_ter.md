---
title: "Different terminal for Nautilus' &quot;open in terminal&quot;"
date: 2013-02-19
forum: General Help
---

### Post by chriscrutch on 2013-02-19
When using Nautilus (3.4.2 in 12.04), in the file menu, there is "Open in Terminal" which opens a terminal using the currently displayed directory as the working directory.  I use this feature a lot, but I don't like that it opens in gnome-terminal.  I'd rather have it open in terminator, but I can't seem to find any way to change it.  

Nautilus preferences has no settings for it.  "System settings...details...default applications" has no entry for terminal emulators.  exo-preferred-applications does have such an entry, but it seems to have no effect on Nautilus.

Where can I change this?

--chriscrutch

---

### Post by mc4man on 2013-02-19
If you can't find a way (open in terminal is a nautilus extension & only editable in it's source), then you could create a nautilus action. (sudo apt-get install nautilus-actions
screens show command & mimetype settings windows, for mime you type in & press enter while focus is on what you typed
The command parameter line is - 
```
--working-directory=%f
```

edit: preferred here to open nautilus-actions Preferences menu & disable the 2 menu layout options so actions show directly in context menu & not in sub-menu

---

### Post by dcstar on 2013-02-20
> **chriscrutch said:**
> When using Nautilus (3.4.2 in 12.04), in the file menu, there is "Open in Terminal" which opens a terminal using the currently displayed directory as the working directory.  I use this feature a lot, but I don't like that it opens in gnome-terminal.  I'd rather have it open in terminator, but I can't seem to find any way to change it.  

Nautilus preferences has no settings for it.  "System settings...details...default applications" has no entry for terminal emulators.  exo-preferred-applications does have such an entry, but it seems to have no effect on Nautilus.

Where can I change this?

Try changing this key in Applications-System Tools-Configuration Editor:

```
/desktop/gnome/applications/terminal/exec
```

---

### Post by chriscrutch on 2013-02-22
Thanks for thinking about this.  

mc4man, that certainly works, but it adds some complexity that I'm trying to avoid.

dcstar, I didn't have gconf-editor on my system, and after installing it and making the change you suggested, it doesn't seem to have any effect, even after log outs and a reboot.

I've never really liked Nautilus as a file manager, anyway, so I guess it's time to move on.

Thanks again to you both.

--chriscrutch

---

### Post by GrouchyGaijin on 2013-04-05
> **chriscrutch said:**
> 
mc4man, that certainly works, but it adds some complexity that I'm trying to avoid.

--chriscrutch

Here is a solution similar to mc4man's: **Total time involved less than 5 minutes**

Save this script to ~/.gnome2/nautilus-scripts.  Call it something like **Open Terminator Here**

```
#!/bin/bash

loc=`echo $NAUTILUS_SCRIPT_CURRENT_URI | sed s/file:\/\///g`


terminator --working-directory="$loc"
```

Restart Nautilus
```
nautilus -q
```

Right click in a folder and go to the scripts menu then choose Open Terminator Here

---

