---
title: "xdotool, works for one App but not for another.. ?!"
date: 2015-11-04
forum: General Help
---

### Post by simba4 on 2015-11-04
I use 'xdotool search --class kodi windowactivate' to Bring that App to focus, But when I try to do the same for another App called 'Kmag' it does absolutely nothing.

xdotool search --class kodi windowactivate - [COLOR=#008000]work[/COLOR]
xdotool search --class kmag windowactivate - [COLOR=#ff0000]dosn't work[/COLOR]
xdotool search --classname kmag windowactivate - [COLOR=#ff0000]dosn't work[/COLOR]
xdotool search --name kmag windowactivate - [COLOR=#ff0000]dosn't work[/COLOR]
xdotool search --any --name --classname --class kmag windowactivate - [COLOR=#ff0000]dosn't work[/COLOR]

Obviously, that Kmag App is running and minimized. 
I can call it by clicking its dashboard icon, but not with xdotool search command. I've tried all kind of options, none work.

I wonder why?

James

---

### Post by vasa1 on 2015-11-04
I don't have Kmag installed but could you try Kmag instead of kmag?

---

### Post by simba4 on 2015-11-04
I had a premonition that it will be asked.
Well, I already tried all the variations. Kmag, KMag, KMAG, kmag - [COLOR=#ff0000]None work[/COLOR]


BTW, the other application doesn't care. kodi, Kodi, KODI, kODi - [COLOR=#008000]All work[/COLOR]



James

---

### Post by CantankRus on 2015-11-05
Try using wmctrl. (needs to be installed)
eg this command will bring kmag to the front if running or launch it if not...
```
wmctrl -a KMag || kmag
```

---

