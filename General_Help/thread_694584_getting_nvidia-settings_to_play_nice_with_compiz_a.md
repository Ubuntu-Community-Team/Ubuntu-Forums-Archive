---
title: "getting nvidia-settings to play nice with compiz at startup"
date: 2008-02-12
forum: General Help
---

### Post by droazen on 2008-02-12
Hi,

When I log in to gnome I run the command:

```
nvidia-settings --load-config-only
```

via the gnome session manager to configure the Nvidia driver with my preferred settings. The problem is that if this command runs before compiz is fully loaded, I end up with no window borders (just white squares where they should be)!

I tried adjusting the "order" value in the session manager so that gnome would run this command AFTER all other startup commands, but that didn't seem to work. So, I decided to wrap the command in a shell script with a 20-second delay:

```

#!/bin/sh

sleep 20 
nvidia-settings --load-config-only
exit 0

```

and have gnome run the shell script instead of the command directly. This DOES work, but is kind of ugly, and it's slightly annoying to have to wait for the script to finish before I can get to work.

So, my question is: has anyone else experienced this problem? Is there a better way to do this? I've tried running nvidia-settings from /etc/X11/Xsession and /etc/X11/xinit/xinitrc, but it seems to only work when I have it run from the gnome session manager for some reason.

Any thoughts/advice would be much appreciated!

---

### Post by pointone on 2008-02-12
I've experienced similar problems a number of times; scripts needing to be loaded after Compiz starts. I've always just used sleep. What's ugly about it?

If it's just your window borders disappearing, you could try just running "gtk-window-decorator --replace" after running "nvidia-settings".

---

