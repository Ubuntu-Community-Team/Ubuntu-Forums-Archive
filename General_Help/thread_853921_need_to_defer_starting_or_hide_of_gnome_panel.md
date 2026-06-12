---
title: "need to defer starting or hide of gnome panel"
date: 2008-07-09
forum: General Help
---

### Post by Mr.Jkate on 2008-07-09
When system boots up, I need to defer creation of gone panel (task bar) 
can any body tell me how ?

Or somebody can tell me how to hide and unhide (not auto hide) using command line at run time.

---

### Post by sayakb on 2008-07-09
First, goto *System->Preferences->Sessions *and click the **Current Session** tab.
Change the style of gnome-panel from *Restart *to [B][I]Trash.
[/I][/B]Now, at a terminal, do:
```
killall gnome-panel
```
Again goto System->Preferences->Sessions->Session Options and **Check** the "Automatically remember ...." checkbox and restart X (Ctrl+Alt+Backspace).
Open the Sessions preferences again and to startup programs, add two entries:
```
killall gnome-panel
```
And:
```
sleep 10&&gnome-panel
```

Not sure if this would actually work ;) 
But just give it a try..

---

