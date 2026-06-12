---
title: "Weird conky text outline"
date: 2018-11-25
forum: General Help
---

### Post by CatKiller on 2018-11-25
I'm running Kubuntu 18.04. I've got conky showing the date and time. Sometimes it develops this ugly outline of a different colour.

I don't know what's causing it, and I've tried everything I can think of to stop it happening, but I'm out of ideas.

Has anyone else seen this?

---

### Post by ajgreeny on 2018-11-25
What graphic hardware?
Also please show us your .conkyrc file content using command ```
cat .conkyrc
``` though it is strange that the problem is intermittent  and I think the hardware is more likely the problem.

Please use **Code-Tags** for terminal output to show that text in a more readable format, the same as it is in the terminal, not as plain text. See my signature below for a **How-to**

---

### Post by CatKiller on 2018-11-25
RTX 2080 Ti, using the 410.73 driver.

The conkyrc's don't do anything weird:

```
conky.config = {
    background = true,
    own_window = true,
    own_window_transparent = true,
    own_window_colour = '000000',
    own_window_type = 'normal',
    own_window_argb_visual = true,
    own_window_argb_value = 255,
    own_window_hints = 'undecorated,below,sticky,skip_taskbar,skip_pager',
    double_buffer = true,
    use_xft = true,
    xftalpha = 1.0,
    text_buffer_size = 2048,
    format_human_readable = true,
    short_units = false,
    override_utf8_locale = true,
    update_interval = 1800,
    draw_shades = false,
    draw_outline = false,
    draw_borders = false,
    uppercase = false,
    border_inner_margin = 0,
    border_outer_margin = 0,
    border_width = 0,
    default_color = 'AEA79F', --Warm Grey 5
    color1 = 'DD4814', --Ubuntu Orange
    color2 = 'AEA79F',
    color3 = 'AEA79F',
    color4 = 'AEA79F',
    alignment = 'bottom_left',
    gap_x = 40,
    gap_y = 15,
    top_cpu_separate = true,
    top_name_width = 30,
    cpu_avg_samples = 2,
    net_avg_samples = 2,
}
 
conky.text = [[
${color2}${font Futura LT:size=70:weight=light}${time %A}${font}${color}
${color1}${voffset 8}${hr 1}${color}
${color3}${voffset 2}${font Futura LT:size=40}${time %d} ${time %B}${color} ${color4}${time %Y}${font}${color}
]]

```

It appears that fullscreen games can trigger it (but not always), but I'm pretty sure that it's happened without that too. It is also sometimes like that on login (but not always).

---

### Post by ajgreeny on 2018-11-25
I have just tried out your .conkyrc on my Xubuntu 18.04 and it seems to work perfectly.

My hardware is entirely Intel, including integrated graphic card, so I wonder if your nvidia card is implicated in some way; is it an optimus card which could mean the OS nouveau driver sometimes is used, not the nvidia driver (I think that's what an optimus card using bumblebee means, but I've never used nvidia)

---

### Post by CatKiller on 2018-11-25
No, and no.

Optimus is for when you have integrated graphics on the CPU and a separate Nvidia GPU - laptops and the like - so you can keep the GPU powered down when you aren't using it to save on the battery. I don't have integrated graphics.

I've forced triple-buffering for KWin and then did a bit of rallying, and the conky hasn't turned ugly. Possibly that's done the trick. Hard to say just yet, since it's intermittent, but I'll keep an eye on it and report back either way.

---

### Post by again? on 2018-11-25
Try setting transparency solely to argb.
eg just argb
```
own_window_transparent = [COLOR="#FF0000"]false[/COLOR],
own_window_argb_visual = true,
own_window_argb_value = [COLOR="#FF0000"]0[/COLOR],
```

or just fake transparency(comment argb in lua --)
```
own_window_transparent = [COLOR="#FF0000"]True[/COLOR],
[COLOR="#FF0000"]--[/COLOR] own_window_argb_visual = true,
[COLOR="#FF0000"]--[/COLOR] own_window_argb_value = [COLOR="#FF0000"]0[/COLOR],
```

---

### Post by CatKiller on 2018-11-26
Did some trucking. Got the ugly outline. Triple buffering isn't a sufficient change :(

I'll play around with those transparency options later.

---

### Post by CatKiller on 2018-12-10
I tried the first transparency suggestion on one half of my conky setup to see if it would make a difference.

```
own_window_transparent = [COLOR=#FF0000]false[/COLOR],
own_window_argb_visual = true,
own_window_argb_value = [COLOR=#FF0000]0[/COLOR],
```

Interestingly, it's changed the colours in a completely different way. You can see that the orange has been made much more yellow. I wouldn't be surprised if that is the colour that you get by adding the orange and the grey together.

[ATTACH=CONFIG]281910[/ATTACH]

In this instance, the other half of my conky setup (with the original settings) has the orange outline. I've still got no idea if it's a conky issue or a KWin issue. Killing and restarting conky makes it display properly, as before.

Edit: On further investigation, it seems to be the own_window_argb_value setting that determines the manifestation: own_window_argb_value 255 gives the outline, own_window_argb_value 0 gives the blend. I'm no closer to knowing what's causing it to display incorrectly in the first place, though.

---

### Post by CatKiller on 2018-12-18
OK, I've fixed it, kinda, I think.

From poking around, it seems that Kubuntu defaults to restoring the previous session rather than starting a new one. I think that's what was causing the text rendering of either Conky or KWin to get confused. Forcing it to start a new session each time seems to have helped significantly.

I'll see how it holds up over time.

---

### Post by david-longe on 2018-12-18
To me it looks like 2 instances of your conky are running at the same time. Next time the text looks wonky check your system monitor to see if you have more than one conky running.

---

### Post by again? on 2018-12-19
@david-longe could be right.
Check for running instances...
```
ps aux | grep -i '[c]onky'
```

If you start conky from a script, could begin with a **killall conky**.

---

### Post by CatKiller on 2018-12-19
> **david-longe said:**
> To me it looks like 2 instances of your conky are running at the same time. Next time the text looks wonky check your system monitor to see if you have more than one conky running.

It's not as straightforward as that: I have, on prior machines, had doubled-up conky, and it doesn't look quite like that. You'll notice that the outline of the text is orange, rather than the grey it would be if there were simply two of them.

It seems to be an initialisation issue. On resuming the session, and resuming the compositor after running games.

---

