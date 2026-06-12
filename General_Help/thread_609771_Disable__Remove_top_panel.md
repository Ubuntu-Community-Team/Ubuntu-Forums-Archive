---
title: "Disable / Remove top panel"
date: 2007-11-11
forum: General Help
---

### Post by GreatSlovakia on 2007-11-11
I have set Avant Window Navigator up in such a way that I don't need any panels any more, yet for some reason the delete this panel option is disabled for the upper panel. All I know is that I have to mess with this part of the system: /home/david/.gconf/apps/panel/toplevels  but as I already re installed my stem maybe 4 times I don't plan to mess with things without tutorial or instructions any more.

(It wouldn't be a bad idea to implent awn into ubuntu standard, as it would make it far easier for mac users to switch to ubuntu)



[update]One really small question, how do you subscribe to a topic on this forum...?[/update]

---

### Post by Perpetual on 2007-11-11
> **GreatSlovakia said:**
> 
[update]One really small question, how do you subscribe to a topic on this forum...?[/update]

I will answer the easy part, I am not on Ubuntu right now (at work so can't figure out the real question)... click Thread Tools and Subscribe To Thread from the drop down menu.

---

### Post by GreatSlovakia on 2007-11-11
> **Perpetual said:**
> I will answer the easy part, I am not on Ubuntu right now (at work so can't figure out the real question)... click Thread Tools and Subscribe To Thread from the drop down menu.

Thx, didn't recognized these links as menu's

---

### Post by GreatSlovakia on 2007-11-12
Guess no one knows how to do this... as I am quite new to linux, is there some documentation about more less all standard files (Including /home/david/.gconf/apps/panel/toplevels in this case)

---

### Post by The Joe on 2007-11-12
This is a stab in the dark (and I'm not sure about it being automatic) try
```

sudo killall gnome-panel

```

Add killall gnome-panel to sessions as well, that should make it automatic.

---

### Post by elcasey on 2007-11-13
"killall gnome-panel" doesn't work, by the way. It just reloads itself. I'm trying to figure this out myself without much luck.

---

### Post by mhouston100 on 2008-01-30
Any luck with this yet, killing the process doesn't work for me either, it just reloads... its really anoying :) Everything is gone from the panel so I just have this little grey square hovering over everything.

Any luck yet?

---

### Post by DjBones on 2008-01-30
searched the forums, and  this is what *JohnnyD'* said about three days ago:

> You can disable the gnome panel by going to Sessions-->Current Session and remove gnome panel from the list of running applications.

Then go to Session Options and click on the Remember button..

---

