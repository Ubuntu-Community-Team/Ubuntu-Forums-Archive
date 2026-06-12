---
title: "Disabling the Gnome screensaver with a script, is it possible?"
date: 2007-04-03
forum: General Help
---

### Post by kemeris on 2007-04-03
I'm looking for a way to automatically disable the Gnome screensaver when a certain program (more specifically, Kaffeine) is started and to re-enable it after the program closes. 

So far I have tried to solve this with the following simple shell script

```

#!/bin/bash

sudo killall gnome-screensaver
kaffeine %U
gnome-screensaver

```

and have also added following line to /etc/sudoers

```
kemeris    ALL=NOPASSWD: /home/kemeris/kaffeine_start.sh
```

If I have understood things correctly, this should make it possible to use the above script without any password queries from sudo. However, it still prompts for the password if I try to run the script from terminal or just kind of hangs if started from Nautilus. I'm kind of running out of ideas what might be wrong with the script... or is there any alternate way to disable the screensaver when needed?

---

### Post by &amp;)ky#)^ on 2008-02-11
I wrote a similar script, but I used gnome-screensaver-command --exit  instead of sudo killall gnome-screensaver.  It's a little nicer and it doesn't require sudo.

---

