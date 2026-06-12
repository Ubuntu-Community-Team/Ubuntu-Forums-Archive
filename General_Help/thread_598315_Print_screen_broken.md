---
title: "Print screen broken"
date: 2007-10-31
forum: General Help
---

### Post by Cubedude04 on 2007-10-31
Hey i removed compiz i believe and now when i press prnt screen it says

There was an error running "/usr/share/compiz/take-screenshot.sh":
Failed to execute child process "/usr/share/compiz/take-screenshot.sh" (No such file or directory).

Is there anyway to fix this?

Thanks in advance

---

### Post by Pathfinder_ on 2007-11-04
Same problem here.

---

### Post by minus198 on 2007-11-04
rm -r .gconf/apps/compiz/

And then reboot X.

That will probably sort it out.

---

### Post by Pathfinder_ on 2007-11-04
I did not see your post but I just fixed another way.
in gconf-editor go to apps/metacity/keybinding_commands
there should be a key called command_screenshot. 
change its value from ```
/usr/share/compiz/take-screenshot.sh
``` to ```
/usr/bin/gnome-screenshot
```

---

