---
title: "Script writing help"
date: 2007-04-14
forum: General Help
---

### Post by aknapp on 2007-04-14
*If this isn't the appropriate forum for this post, please move it. Thanks.*

> #!/bin/bash
# Disable mouse acceleration
xset m 0 0
# Set gamma correctly
nvidia-settings -l --config="/home/knapp/.wine/drive_c/Program Files/Steam/nvidia-cs-settings"
# Start Counter-Strike
WINEDEBUG=fixme-all wine C:/Program\ Files/Steam/Steam.exe  -fullscreen -width 800 -height 640 -applaunch 10 -heapsize 512000 +map_background none & sleep 1

# Undo all of that
xset m 2 3
nvidia-settings -l --config="/home/knapp/.wine/drive_c/Program Files/Steam/nvidia-settings"


This is what I have and it doesn't work. Everything executes fine, but it immediately undoes it (ie it disables mouse accel, but then executes the xset m 2 3, turning it back on). How can I make it set it, then once the application is close, undo it?
 
Also I was wondering why, if you set anything to a certain nice level with the nice -n command, it doesn't show in the system monitor?

Thanks,
Aaron

---

### Post by CompShrink on 2007-04-14
That's quite simple actually. Since you already run it with the & at the end, this should work:

Not the one extra & (probably not needed) and simply adding a "wait" will wait until everything preceding it with an & (aka new threads) finish before continuing.

```
#!/bin/bash
# Disable mouse acceleration
xset m 0 0
# Set gamma correctly
nvidia-settings -l --config="/home/knapp/.wine/drive_c/Program Files/Steam/nvidia-cs-settings"
# Start Counter-Strike
WINEDEBUG=fixme-all wine C:/Program\ Files/Steam/Steam.exe -fullscreen -width 800 -height 640 -applaunch 10 -heapsize 512000 +map_background none & sleep 1 &
wait
# Undo all of that
xset m 2 3
nvidia-settings -l --config="/home/knapp/.wine/drive_c/Program Files/Steam/nvidia-settings"
```

---

### Post by aknapp on 2007-04-16
Thanks a lot for your response. That worked perfectly. :)

---

