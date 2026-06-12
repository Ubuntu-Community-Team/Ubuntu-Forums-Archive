---
title: "scheduled session suspend?"
date: 2013-04-14
forum: General Help
---

### Post by lightsaberlesbian on 2013-04-14
I like to listen to audio books before going to bed.  Is there a way I can schedule VLC or Amarok to stop playing after 10 minutes for example?  I know Ubuntu must have a sleep feature that can be scheduled similar to "halt" at least.  Couldn't find any commands via google though.

---

### Post by dabl on 2013-04-14
Google found a suitable script [**[color=green]here[/color]**](http://stackoverflow.com/questions/2387485/limiting-the-time-a-program-runs-in-linux), which I tested with kate:

```
#!/bin/bash
trapped=""
trap 'trapped=yes' SIGCHLD
kate &
sleep 20
[ -z "$trapped" ] && kill $! 2>/dev/null && echo '...'
#end
```

I tested the script with kate, and it works.  In the script, replace "kate" with "vlc" or "amarok", and replace the "20" with the time that you want the package to run, in seconds.  Give the script a name, and run it in a console window with a "sh" prefix.  When your package comes up, start your audio book, and after the stated time, the package will close.

---

