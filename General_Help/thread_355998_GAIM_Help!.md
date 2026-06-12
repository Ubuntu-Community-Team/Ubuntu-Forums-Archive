---
title: "GAIM Help!"
date: 2007-02-07
forum: General Help
---

### Post by coldopm on 2007-02-07
OK so when I close my GAIM, it closes right down now instead of popping into the top tool bar on my desktop..I use Edgy. It used to pop up there but I removed it from panel unintentionally trying to remove the icon beside it. I now can't get it back so when I close down my buddy list it takes me right offline....

Any help at all?:confused:

---

### Post by coldopm on 2007-02-07
Anyone with any idea? It has to be something simple I would think, but I am new to Edgy so I am not to sure what ;p

---

### Post by tacm on 2007-02-07
mine did the same thing.  Last night I removed my theme i was running and reset gnome to its defaults.  My icon is now back on the tool bar. Im sure there is a better way to do this but Im a noob.   I hope this helps. Ciao

---

### Post by victorbrca on 2007-02-07
This may help...   Not 100% sure...


```
killall gnome-panel
```


Vic.

---

### Post by Polygon on 2007-02-07
try running gaim from the terminal, sometimes helpful error messages pop up there

and if not, try backing up / deleting your gaim configuration, and then try it again, if it suddenly works, then its something wrong with your config files and just deleting it will fix it. If that still doesnt help, then it might be a problem with gaim itself (try reinstalling it) or gnome-panel

---

### Post by coldopm on 2007-02-07
Poly, neither of the previous options worked, and I dont know how to restore gnome defaults.

Can you tell me how to run GAIM from the terminal?

---

### Post by coldopm on 2007-02-07
NM I figured out how to run from terminal and it did not give me any errors, and when I try to uninstall GAIM from add/remove it says I can't so???

---

### Post by AusIV4 on 2007-02-07
You're on the wrong track entirely. 

Open Gaim. 
Tools -> Plugins.

3rd plugin from the bottom will put Gaim in the system tray when you close it.

---

### Post by tacm on 2007-02-07
> **coldopm said:**
> Poly, neither of the previous options worked, and I dont know how to restore gnome defaults.

Can you tell me how to run GAIM from the terminal?

To tell you the truth Im a dumb fook and someone gave me some code to run...Ill see if I can find it.

---

### Post by coldopm on 2007-02-07
Yeah that plugin is checked.

What I did was right clicked on the seperator bar looks kin of like this :: but longer, beside my gaim icon, I then chose remove from panel. not only did it remove that :: but also my Gaim icon.

I have removed gaim and reinstalled, the plugin is checked off and I still cant get it to work....GAH

Anyone?

---

### Post by victorbrca on 2007-02-08
I think you removed your notification area.

Right click on the panel bar, click "add to panel", got to utilities and choose "Notification Area".

Hope that works..


Vic.

---

### Post by coldopm on 2007-02-08
This is what I get in Debug window if it means anything to anyone!

prefs: /gaim/gtk/debug/enabled changed, scheduling save.
prefs: /gaim/gtk/debug/width changed, scheduling save.
util: Writing file prefs.xml to directory /home/coldopm/.gaim
msn: C: NS 000: PNG
msn: S: NS 000: QNG 48
msn: C: NS 000: PNG
msn: S: NS 000: QNG 40
msn: C: NS 000: PNG
msn: S: NS 000: QNG 43
prefs: /gaim/gtk/blist/list_maximized changed, scheduling save.
g_log: gaim_dbus_pointer_to_id: assertion `id || node == NULL' failed
prefs: /gaim/gtk/blist/list_maximized changed, scheduling save.
util: Writing file prefs.xml to directory /home/coldopm/.gaim
msn: C: NS 000: PNG
msn: S: NS 000: QNG 40
g_log: gaim_dbus_pointer_to_id: assertion `id || node == NULL' failed
msn: C: NS 000: PNG
msn: S: NS 000: QNG 46
g_log: gaim_dbus_pointer_to_id: assertion `id || node == NULL' failed
g_log: gaim_dbus_pointer_to_id: assertion `id || node == NULL' failed
g_log: gaim_dbus_pointer_to_id: assertion `id || node == NULL' failed
g_log: gaim_dbus_pointer_to_id: assertion `id || node == NULL' failed
g_log: gaim_dbus_pointer_to_id: assertion `id || node == NULL' failed
g_log: gaim_dbus_pointer_to_id: assertion `id || node == NULL' failed
g_log: gaim_dbus_pointer_to_id: assertion `id || node == NULL' failed
g_log: gaim_dbus_pointer_to_id: assertion `id || node == NULL' failed
g_log: gaim_dbus_pointer_to_id: assertion `id || node == NULL' failed
g_log: gaim_dbus_pointer_to_id: assertion `id || node == NULL' failed
msn: C: NS 000: PNG
msn: S: NS 000: QNG 45
g_log: gaim_dbus_pointer_to_id: assertion `id || node == NULL' failed

---

### Post by coldopm on 2007-02-08
Bang on Victor. Thank you very much!

---

### Post by victorbrca on 2007-02-08
> **coldopm said:**
> Bang on Victor. Thank you very much!

No problem!!!  :) 


Vic.

---

