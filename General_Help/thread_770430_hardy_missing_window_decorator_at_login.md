---
title: "hardy: missing window decorator at login"
date: 2008-04-27
forum: General Help
---

### Post by raindog21 on 2008-04-27
Hi,

I have compiz and awn configured to start at login as well as the compiz fusion icon.  Every time I log in I have to select Reload Window Manger in order to get the Emerald window decorations.  Emerald won't start at login.

Any ideas?

I'm starting compiz using the following script

#!/bin/bash

compiz --replace &

while true; do
	if ps -C emerald > /dev/null
	then
		# emerald running, break
		break
	else
		# emerald not running, launch
		emerald --replace &
	fi
done

---

### Post by raindog21 on 2008-04-27
also - 

having a separate entry in my session for emerald --replace & at login does not fix the problem.  Only performing reload window manager after login from compiz fusion icon seems to have any effect on the problem

---

### Post by akshar_patel_47 on 2008-04-27
Compiz doesn't need a script to start at login.. It does that automatically. Delete that script and then place ```
emerald --replace
``` in sessions startup.

---

### Post by Zorael on 2008-04-27
Well, it's hard to say why it isn't starting, and I'm not familiar with the fusion-icon app (haven't installed it yet). First of all, do you have the Window Decorations plugin enabled?


I wrote this for someone who had Emerald crash on him all the time;  after the script is started, it will launch Emerald, and if the process dies it will relaunch it after waiting 2 seconds, indefinitely. So it's a dirty fix and you shouldn't use it if you're using fusion-icon to switch between stuff. You need to do 'killall <script name>' in a terminal to end the loop.
```
#!/bin/bash

while true; do emerald --replace; sleep 2; done &
```

---

### Post by raindog21 on 2008-04-27
Hi,

When I remove the compiz script at login and replace it with only 

```
emerald --replace &
```

then compiz does not start.  In this case "Reload Window Manager" starts compiz, emerald, and awn after login.

You say that compiz does not require as script to start but is it possible there is a config file somewhere that is not being written properly to save its state causing gnome to forget that compiz is supposed to load?  Maybe a permissions problem?  I have no idea where to look.

---

### Post by Zorael on 2008-04-27
I believe it's somewhere in the gconf settings. Try running 'gconftool-2', not sure if that's it, it's been too long.

Emerald needs a window compositioner to run (read: Compiz). When Compiz is started (by Gnome, via a terminal, anything), if you have the Window Decorations plugin, it should start a decorator automatically. You need that plugin activated.

In the case where it *still* doesn't start it for some reason and you need to start it separately, emerald --replace is the way to go. However, you need to make sure compiz is started before emerald, hence the script.

---

### Post by raindog21 on 2008-04-27
fixed.  

```

compiz --replace ccp $@ &
```

instead of

```
compiz --replace $@ &
```

in the startup script resolved my emerald problems

---

