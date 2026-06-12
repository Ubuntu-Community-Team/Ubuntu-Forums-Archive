---
title: "help with session"
date: 2006-12-02
forum: General Help
---

### Post by redDEADresolve on 2006-12-02
I've been looking for a way to run certain programs at startup when I load into a certain session. I want one program to load for my gnome session and about 3 to run in my xgl session. I know I can add them to sessions but they load in both gnome and xgl sessions making things not work.

Basically i need to run 
GNOME
bightside

XGL
beryl-manager
gnome-settings-daemon
/usr/bin/keyboardfix

I found this in the beryl forums for running beryl manager only in xgl sessions
```
#!/bin/bash
#
# Start beryl-manager within gnome-session
#
if [ `ps -A -o comm | grep -c '^Xgl$'` == "1" ]; then
       DISPLAY=:1 beryl-manager
       DISPLAY=:1 beryl-xgl
else echo "${0}: Error: beryl-manager not launched. Xgl not running?"
fi

```

Any idea how to edit it to run the others at startup? How to get brightside to only load in gnome?

---

