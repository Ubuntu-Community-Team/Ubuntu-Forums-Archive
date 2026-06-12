---
title: "Help with a script (how to kill and relaunch AWN and screenlets)"
date: 2008-03-21
forum: General Help
---

### Post by Depressed Man on 2008-03-21
Alright, forgive me if this script is in bad form (haven't done a script in a while)

Anyway here's my script to run Google Earth in metacity because it doesn't display when Compiz fusion is on. 

```

#!/bin/bash
metacity --replace &
/opt/google-earth//googleearth %f
compiz --replace
```

The problem is I have screenlets and avant windows navigator usually running as well. So how would I kill these two before launching Google Earth and then relaunching these programs after Google Earth finishes running? 

I think screenlets may be able to be killed if you take out screenletsd (the daemon for them). Unsure however, anyone have any advice?

---

### Post by forrestcupp on 2008-03-21
I think they'll be killed automatically when the compositor is turned off.  Just put the commands to run them again at the bottom after compiz --replace.

---

### Post by Depressed Man on 2008-03-21
Nah, screenlets stay (not sure about avant). Screenlets will stay on top (well partially because of my on top setting). I'll try turning that off to see if it stays in front of the other screens in metacity though.

---

### Post by Whise on 2008-03-21
why kill screenlets? they run perfectly in metacity since 0.0.12

---

### Post by forrestcupp on 2008-03-22
If AWN isn't taken care of on it's own, the commands are 
```
killall avant-window-navigator
```
to get rid of it, and just avant-window-navigator to get it back.

Hopefully your screenlets will just be ok with metacity because it looks like it's going to be a pain to kill them.  You pretty much have to kill them one by one by determining what their process id's are and killing those id numbers.  Then to start them back up, you have to know what all the screenlets are, and just run their python files.

---

### Post by Depressed Man on 2008-03-22
> **Whise said:**
> why kill screenlets? they run perfectly in metacity since 0.0.12

Ah ok, thanks for that information!

And yeah, it was because of my always on top setting that they were being shown in front in metacity. In Compiz I usually have them set on a widget layer.

---

