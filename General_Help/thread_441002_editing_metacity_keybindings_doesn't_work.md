---
title: "editing metacity keybindings doesn't work?"
date: 2007-05-12
forum: General Help
---

### Post by dgel on 2007-05-12
Hi

I tried editing the global keybindings, so i could set <Control><Alt><Del> to run the system monitor, but when i set it, it does nothing.
Here is what i did:
i set command_1 to /usr/bin/gnome-system-monitor
and i set run_command_1 to <Control><Alt><Del>
but after doing so, nothing happens when i hit <Control><Alt><Del>.
Any ideas what went wrong? I'm using Feisty btw.

Na-Fiann

---

### Post by benanzo on 2007-05-12
Are you running Beryl?  if so, you have to set the global keybindings in Beryl Settings Manager, not gconf, unfortunately.

I just tried what you describe under Metacity and it worked fine.

---

### Post by henriquemaia on 2007-05-17
> **benanzo said:**
> Are you running Beryl?  if so, you have to set the global keybindings in Beryl Settings Manager, not gconf, unfortunately.

[...]

Thanks for this. I&#8217;m running beryl and I was trying to find a way of having my old keybinds. It worked like a charm ;)

---

### Post by aysiu on 2007-05-17
From my previous experience using Gnome, I think it should be ```
<Control><Alt>Delete
``` instead of ```
<Control><Alt><Delete>
```

---

### Post by dgel on 2007-05-18
Thanks, I'll try that :)

---

### Post by bobby_d on 2008-01-26
Hi all, 

Sorry to respond to old topic :) 

Just experienced the same original problem - but I use 6.06, without Beryl and the like.. Guess this shouldve been posted to [http://ubuntuforums.org/showthread.php?t=179178](http://ubuntuforums.org/showthread.php?t=179178), but that forum is closed. Anyways - I use the persistent version of LiveCD from USB, and wanted to try some bindings but couldn't do it (tried to map <Alt>F3 to command_1) - restarting didn't quite work. 

Finally, I tried to run 
metacity --replace

And this DID finally allow <Alt>F3 to be pressed and ran the command - but it also made all  window title bars dissapear. 

Finally, I read somewhere I should try 
metacity --replace &

so as to have it run in the background... I've discovered that, after this, as long as the terminal window is open, while I press <Alt>F3 it is recognized and run, but as soon as I close the terminal window - even if it is with CTRL-D, which should allow the background process to keep on running - then metacity stops catching <Alt>F3 and running the command.. 

Sorry about the bit off-topic from this post - but anyone have any ideas on this?

---

### Post by bobby_d on 2008-01-26
Ok, I think I got how to have the key bindings in "persistent" 6.06 to work - simply use System/Preferences/Sessions, go to Startup Programs tab, and Add a command containing only 

metacity_replace.sh

Then go to /bin, make a new file called metacity_replace.sh, and inside write: 

#!/bin/sh

gksudo "metacity --replace &"

and that should do it ... :)

---

