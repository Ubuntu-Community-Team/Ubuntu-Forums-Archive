---
title: "A Script that kill restart gnome-panel, and restart nm-applet w/ notification"
date: 2008-03-19
forum: General Help
---

### Post by justin_c18 on 2008-03-19
I made a shell script that will kill gnome-panel, and turn nm-applet back on after gnome-panel has been killed and restarted. I allso stuck a notification in the script. I basically saved the script as a shell script in my home folder, and used the code below to enable the icon usage, and script usage of course.

```
/home/<user>/script.sh
```

The code for the script is as follows:

```

#!/bin/bash

killall gnome-panel && sleep 3 && nm-applet && sleep 1
notify-send "Restarting Gnome-Terminal & Starting nm-applet"

#Note
#Make sure you save the file as a .sh, make it executable
#Make sure when you make an icon, the icon command
#is set to a given directory before you execute the script.

#Make sure you have libnotify-bin installed in your
#current installation.

#That's all, thanks. Enjoy!

```

Make sure the script is executable.

I got sick of opening up a terminal typing, "killall gnome-panel" then, pressing "ALT-F2" that opens a dialog to run a command, which I typed, "nm-applet". The gnome panel freeze has happened ever since I've used Ubuntu, and, figured I'd give BASH a try and it worked with a little research.

If you can make the script any better, please do so! 

That is all, thanks. And, Enjoy! :twisted:

-Justin

---

### Post by kaens on 2008-03-20
Hey, looks like you're starting to learn shell scripting. It's got a lot of quirks, but can make your life a lot simpler when dealing with linux.

If you're interested, check out the ABS link in my sig - it's a great way to bring yourself up to speed.

---

