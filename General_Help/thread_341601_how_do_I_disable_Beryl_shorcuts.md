---
title: "how do I disable Beryl shorcuts"
date: 2007-01-18
forum: General Help
---

### Post by db9s on 2007-01-18
yes how do I, especially the one that turns saturation on/off which has a HUGE conflict with firefox's zoom (ctrl + scroll).
whenever I try to change it thorugh the shortcut menu, it either doesn't let me or crashes the beryl Settings Manager

thanks

---

### Post by allwin on 2007-01-18
Use Beryl Manager itself to disable the shortcuts.  Look under each category of plugin and so forth for "bindings".  You should be able to turn them all off.  However, Beryl just got updated this evening and is now 0.1.5, and things look considerably different, so not knowing which version you have, I can't say exactly where the settings are.  Turn Beryl off and go back to Metacity as window manager before making the settings.  It's touchy, that's for sure.

---

### Post by db9s on 2007-01-19
I'm using the latest one (just updated) but the problem is that 'Saturation' is under the General Options category. So there is no way to disable it altogether. 

I just want to get rid of the (ctrl+scroll) shortcut that's associated with it, is there a way to edit some settings file to disable this shortcut?

---

### Post by db9s on 2007-01-19
fixed it!!!!!!!!!!!!
go to .beryl folder in your home direcotory, open the settings file

in it you should see lines where like
```

a_saturation_decrease__mouse      
```

change that to
```
a_saturation_decrease__mouse=#Button0
```

do the same for the _increase located right near it. Infact you can change all the shortcuts through this!

---

