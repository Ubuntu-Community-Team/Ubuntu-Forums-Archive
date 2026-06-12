---
title: "gxmessage always on top?"
date: 2013-04-19
forum: General Help
---

### Post by Subito Piano on 2013-04-19
Hi!  I created a popup winow with gxmessage to remind me of a task.  It goes off regularly via alarm-clock. What command do i add to make the window always on top?  (For instance, it gets buried underneath my startup programs if the alarm time is 6AM and i start up my laptop at 7AM, so i don't see it.)

Here's my script: 

```
#!/bin/bash
clear
gxmessage TEXT OF MY TASK -center -font "sans-serif 36" -geometry 320x130 -name  ALARM
```

I tried zenity as well; either way, zenity or gxmessage, i don't know what option to add to keep the window on top.

Thanks!

---

