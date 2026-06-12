---
title: "mouse circles on ctrl-key"
date: 2015-04-17
forum: General Help
---

### Post by Nazaroo on 2015-04-17
This is driving me nuts. 

Half the time I can't capture text because the ctrl-C feature is being interfered with 
by the useless "orange dots" feature that shows the mouse location when I press ctrl key down.

Also, damn it, I can't find the box that lets you turn that off in Ubuntu 14.04.

It should be in Preferences / Mouse & , but there is no box to unclick.
**box: [COLOR=#0000cd]"Show position of pointer when the Control key is pressed".[/COLOR]**
Where has it been moved? 

Or, conversely, if I've been hijacked by malware (cause it sure feels like it)
how can I unhook such "addons" or "plugins" to my mouse?

arrrgh with me for moment.

thanks.

---

### Post by Holger_Gehrke on 2015-04-18
I do believe it's actually an accessibility feature for vision-impaired users, so I would look for it in the accessibility options.

---

### Post by CantankRus on 2015-04-18
The locate-pointer feature is disabled by default.
Don't know if/where the setting can be changed by a GUI in ubuntu 14.04

Reset to default with this terminal command...
```
gsettings reset org.gnome.settings-daemon.peripherals.mouse locate-pointer
```

---

