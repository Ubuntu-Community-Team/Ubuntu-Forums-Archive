---
title: "desktop image hiding conky window ?"
date: 2015-09-19
forum: General Help
---

### Post by alain.roger on 2015-09-19
Hi,

under KUbuntu my conky windows does not show on my desktop background image.
Only when i shutdown or restart my computer i can see them in the background.
If i run them from terminal, they are displayed correctly on desktop background image.

my window settings in the conky script are:
>  [FONT=monospace][COLOR=#000000]own_window_type desktop [/COLOR]
own_window yes 
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
[/FONT]


so what is wrong ?
thx

---

### Post by Frogs Hair on 2015-09-19
Check the position and make sure conky is set for your monitor size. Mine is 1366 x 768

Example: ```
# Window specifications #
gap_x 1070
gap_y 40
minimum_size 268 700
maximum_width 268

```

Window Type Alternatives: 

```
own_window yes
own_window_type panel  # other options are: override/dock/desktop/panel
own_window_transparent yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below

```

---

