---
title: "How to make chrome caption box always on top on Ubuntu 22.04"
date: 2022-08-24
forum: General Help
---

### Post by esso10 on 2022-08-24
The text box keeps hiding behind browser screen, is there something to do to make it always on top?

---

### Post by yetimon_64 on 2022-08-25
If the chrome caption box window has a window title that doesn't change, I'd look at using the devilspie2 daemon to monitor for and automatically raise that window. If the window title constantly changes then this method may not work so well.

As an example from my install here, I use devilspie2 to always keep the Caja "File Operations" window on top of all other windows. With devilspie2 installed and auto started at log in, to do the task requires a "lua" script file stored in the config directory devilspie2 ($HOME/.config/devilspie2). 

The autostart command I use for devilspie2... ```
devilspie2 --folder $HOME/.config/devilspie2
```

The lua file I use to keep the caja file operations window "always on top"...```
if get_window_name()=="File Operations" then
    debug_print "Caja File Operations window"
    make_always_on_top()
end
```I've named this file as "$HOME/.config/devilspie2/fileops.lua"

Hope this helps. Good luck, yeti.

---

