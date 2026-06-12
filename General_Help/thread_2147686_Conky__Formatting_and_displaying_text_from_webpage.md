---
title: "Conky : Formatting and displaying text from webpage"
date: 2013-05-22
forum: General Help
---

### Post by AshNova on 2013-05-22
Hi everyone,

I have a Conky script which gets the game time and game day of Eternal lands from this website :

[http://trinity.el-bots.zapto.org/eltime.php]("http://trinity.el-bots.zapto.org/eltime.php")

Although there is a EL time indicator it is buggy for me and I prefer to have the info on my desktop.

The problem is that while the text from the webpage normally sits nicely, top_middle on my wallpaper, when there is a lot of text, some of it gets cut off and it intrudes into space it's not meant to be in :

[ATTACH=CONFIG]242905[/ATTACH]

How do I format the text from the website, so that nothing gets cut off and it sits in the middle of the desktop?

This is my Conky script :

```
alignment top_middle
background no
border_width 1
default_color white
default_outline_color white
default_shade_color white
draw_shades no
use_xft yes
xftfont DejaVu Sans Mono:size=9.5
gap_x 120
gap_y 50
minimum_size 5 5
no_buffers yes
out_to_console no
out_to_stderr no
# Window settings
own_window_argb_visual true
own_window_argb_value 0
own_window yes
own_window_transparent yes
own_window_class Conky
own_window_type normal
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
# Use double buffering (reduces flicker)
double_buffer yes
stippled_borders 0
update_interval 61.0
# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

TEXT
${execi 61 curl http://trinity.el-bots.zapto.org/eltime.php}
```

Also, is there a way to make this script more efficient/cleaner?

I'm having way more fun getting this to work than actually playing the game :P

---

### Post by HiImTye on 2013-05-22
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
try max_text_width
[http://conky.sourceforge.net/config_settings.html](http://conky.sourceforge.net/config_settings.html)

---

### Post by Vaphell on 2013-05-22
set text_buffer_size big enough for the message to fit, eg
```
text_buffer_size 512 
```
i haven't seen in conky settings anything about on-whitespace wrapping (if i understand correctly max_text_width doesn't care about readability and will break in the middle of the word if that's where the limit hits), so in order to achieve nice wrap use *fold -s*. Default target width is 80 but you can set something else with *-w WIDTH*
```
${execi 61 curl http://trinity.el-bots.zapto.org/eltime.php **| fold -s** }
```

in case the text is cut off by its window you will have to play with window size settings.

---

### Post by HiImTye on 2013-05-22
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
yeah, I don't use anything large enough to require wrapping, I just remembered seeing a variable for it, but you're right it says the next char, not word. fold might just be a better option

---

### Post by AshNova on 2013-05-23
Thank you HilmTye, Vaphell :)

```
text_buffer_size 800
```

and 

```
${execi 610 curl http://trinity.el-bots.zapto.org/eltime.php | fold -s}
```

seems to have done the trick.

I'm curious, what does the -s option stand for?

---

### Post by Habitual on 2013-05-23
```
man fold
```
      -s, --spaces
              break at spaces

---

### Post by AshNova on 2013-05-24
Thank you Habitual :)

Now I can use the 'man' command instead of googling all the time :D

---

### Post by Vaphell on 2013-05-24
if find *man* too verbose for my usual needs. Most commands support **--help** switch that returns a comprehensive list of supported features.

---

### Post by AshNova on 2013-05-29
> **Vaphell said:**
> if find *man* too verbose for my usual needs. Most commands support **--help** switch that returns a comprehensive list of supported features.

Thank you Vaphell, I'll be sure to use the --help switch as well :)

---

