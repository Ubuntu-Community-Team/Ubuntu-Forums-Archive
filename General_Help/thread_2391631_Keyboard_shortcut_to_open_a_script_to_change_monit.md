---
title: "Keyboard shortcut to open a script to change monitors"
date: 2018-05-11
forum: General Help
---

### Post by krisjan on 2018-05-11
So basically I'm trying to do a keyboard shortcut that upon pressing would change my monitor layout to external only from both being on and *vice versa.*

I added two shortcuts in Settings > Devices > Keyboard.
The first one is
```

Name           Change to both monitors
Command        gnome-open home/kris/scripts/change-both.sh
Shortcut       Super + Print

```

And the second one is
```

Name           Change to external monitors
Command        gnome-open home/kris/scripts/change-external.sh
Shortcut       Super + Pause

```

The scripts have this code inside of them
change-external.sh
```

#!/bin/bash
xrandr --output HDMI-1 --auto
xrandr --output eDP-1 --off

```

change-both.sh
```

#!/bin/bash
xrandr --output HDMI-1 --auto --left-of eDP-1 --primary 
xrandr --output eDP-1 --auto

```

The problem is that I have no clue where I went wrong. I'm guessing I messed up with either the paths, because for some reason they're confusing for me, or something in the keyboard shortcuts. Can you help me find the issue?

---

