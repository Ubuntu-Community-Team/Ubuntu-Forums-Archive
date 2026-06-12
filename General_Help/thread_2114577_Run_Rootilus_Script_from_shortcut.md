---
title: "Run Rootilus Script from shortcut?"
date: 2013-02-10
forum: General Help
---

### Post by GameX2 on 2013-02-10
Hi,


I have a Nautilus Script called Rootilus, which open the current Nautilus windows as Root:
```

#!/bin/bash

if [[ -x /usr/bin/gksu || -x /opt/gnome/bin/gksu ]]; then
    sudotool=gksu
elif [[ -x /usr/bin/gnomesu || -x /opt/gnome/bin/gnomesu ]]; then
    sudotool=gnomesu
fi

$sudotool "nautilus --no-desktop $NAUTILUS_SCRIPT_CURRENT_URI"
```

Currently, when I'm in a folder, I always have to rick-click>Scripts>Run as Root.  I want to avoid doing this all the time, and set a keyboard shortcut to the script instead.

The problem is if I set Ctrl-Alt-R as a shortcut to run the script, the script will only open my Home folder, and not the folder I am currently in.

How can I fix this, by modifying a bit the script?

Thank you!

---

### Post by stinkeye on 2013-02-10
Don't know how to fix the script but there is a ppa to add
**open as root** to the main right click menu to save the extra step.
See [**_[COLOR="DarkRed"]HERE[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=12500854&postcount=7")

---

