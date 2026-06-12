---
title: "Gnome-terminal opening automatically when VSCode launches"
date: 2020-11-04
forum: General Help
---

### Post by rmacfarlane1983 on 2020-11-04
Hi everyone,

I've written a bash script to automatically launch a fullscreen gnome-terminal session on my right-hand monitor upon login. 

```

#!/bin/bash
# Opens gnome-terminal fullscreen on right-hand monitor upon login
# sleep 10
gnome-terminal --geometry 1x1+1981+999 --full-screen
```

This works fine, but something unexpected and undesired has come along  with it. When VSCode is launched, a second fullscreen gnome-terminal  opens on the right hand monitor. This does not occur when launching  other apps. I'm baffled as to why this is occurring or how to fix it.  Any insights? Ubuntu 20.04.

---

### Post by dragonfly41 on 2020-11-04
I have VSCode dormant (for when I might need it) and I use Atom instead as my main dev editor.
I might suggest opening developer tools in VSCode to inspect the instances of gnome-terminal.
You could apply inotify to gnome-terminal to see where it is opened.
Or some tool like Stacer to observe the running processes.
End of my detective suggestions.

---

