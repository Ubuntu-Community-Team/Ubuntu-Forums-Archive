---
title: "Problem with keyboard layout swithing"
date: 2007-11-17
forum: General Help
---

### Post by huan.kaktus on 2007-11-17
Ubuntu Gutsy 64 bits.
I have 3 layouts, but with keyboard shortcuts can switch only between two. For third layout I need click on layout indicator. Can any help to me?

Output of xprop -root | grep XKB:
_XKB_RULES_NAMES(STRING) = "base", "pc105", "us,lv,ru", ",,winkeys", "grp:alts_toggle"

---

### Post by x64Jimbo on 2007-11-17
I seem to recall there being a setting to use keyboard shortcuts for running arbitrary scripts/programs... I have my layout commands plugged into scripts with launcher buttons that run the scripts. 
These are the commands that I use in my scripts... 
setxkbmap dvorak
setxkbmap us
Maybe you could make your own scripts and link them to keyboard shortcuts.

---

### Post by huan.kaktus on 2007-11-18
Yes, I can write my own scripts for layout switching, but I seems, it is not correct problem solution method. With scripts I can not set layouts individualy for diferent windows.
Maybe this problem is bug, and need to be reported?

---

### Post by x64Jimbo on 2007-11-18
Ohhhh... See, I can't stand having the layout switching on me whenever I switch windows. But I see that you actually prefer this behavior. I'm sorry I misunderstood the question.

---

