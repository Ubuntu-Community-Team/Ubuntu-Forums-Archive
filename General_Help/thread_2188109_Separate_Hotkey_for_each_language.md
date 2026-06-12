---
title: "Separate Hotkey for each language"
date: 2013-11-15
forum: General Help
---

### Post by paybegun on 2013-11-15
Hello,

I'd like to change keyboard lang-layouts using separate hotkey for each lang. 
E.g.
Alt+1 for English
Alt+2 for Ukrainian
Alt+3 for Russian

After googling... I tried to set the following commands for Custom Shortcuts in System Settings->Keyboard->Shortcuts :

[PHP]
## for alt+1
setxkbmap -layout 'us,ua,ru' -option 'grp:ctrl_shift_toggle'
## for alt+2
setxkbmap -layout 'ua,ru,us' -option 'grp:ctrl_shift_toggle'
## for alt+3
setxkbmap -layout 'ru,us,ua' -option 'grp:ctrl_shift_toggle'
[/PHP]

most time it works somehow, but:
- often with delays (0.5-2 seconds)
- sometimes it doesn't change the layout at all
- also it doesn't change the layout at top-right-indicator (near the clock) and it's not too necessary
- also it mixes layouts somehow: sometimes alt+1 changes lang to English, sometimes to Russian and sometimes to Ukrainian
- it seems other hotkeys do not work sometimes when I use Russian or Ukrainian lang

I really need and want it to work perfectly (with no delays and above problems) and the method how to do this doesn't matter.. It could be 3rdparty screepts, tools, manual screepts that changes config files by itself.. etc..

If anyone has ideas, it would be great!
Thanks..

[HTML]Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise

[/HTML]

---

