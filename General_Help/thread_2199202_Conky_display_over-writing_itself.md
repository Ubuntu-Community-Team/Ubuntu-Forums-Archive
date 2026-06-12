---
title: "Conky display over-writing itself"
date: 2014-01-12
forum: General Help
---

### Post by dfjarvis03 on 2014-01-12
Good afternoon,

forgive me if this has already been covered in another thread... typically, I pride myself on my Google-foo, but after a couple hours of searching and playing with settings, I am getting no where.

I have configured conky as follows, and when conky updates the display, it just writes over itself, instead of clearing the previous data, resulting in non-changing test getting bolder, and changing text getting scrambled:

[IMG]http://i268.photobucket.com/albums/jj19/blufish2004/Screenshotfrom2014-01-12160801_zpsd52688d3.png[/IMG]

I do not have any flickering of any kind, and double buffering is already set to yes. This is happening on a default Ubuntu 13.10 install (updated, and some extra packages from the Ubuntu Software Center, such as conky, installed), running on an ASUS Z87-PRO with an Intel i7 4770K, utilizing the onboard video output (no fancy high-end video cards for me yet).

Any thoughts?

My conky configuration is as follows:
```
total_run_times 0out_to_console no
double_buffer yes
no_buffers yes
text_buffer_size 1024
update_interval 5
cpu_avg_samples 1
net_avg_samples 2
alignment top_left
minimum_size 300 500
maximum_width 300
gap_x 10
gap_y 30
draw_shades no
draw_outline no
draw_borders no
border_width 1
border_margin 1
background yes
own_window yes
own_window_type override # normal / override / desktop
own_window_transparent yes
use_xft yes
xftalpha 1
override_utf8_locale yes # force UTF8
xftfont saxMono:size=9 #OCR A Std:size=6
uppercase no
use_spacer yes
stippled_borders 5
default_color FFFFFF
default_shade_color
default_outline_color black


color3 FFFFFF
color2 FFFFFF
color1 FFFFFF


TEXT
${font Visitor TT1 BRK : pixelsize=12}${color1}Time${font}
${color3}${voffset -5}${hr}
${offset 15}${color1}${time %A %d %B %Y %H:%M:%S}
${offset 15}${color1}Uptime  : ${color3}${uptime}

```

---

### Post by stinkeye on 2014-01-12
Don't know if it was a copy paste error and shouldn't be the cause of your problem, but the first line should be two lines..
```
total_run_times 0out_to_console no
```
should be...
```
total_run_times 0
out_to_console no
```

Your config runs fine here on 13.10. [COLOR="#FF0000"] Edit:[/COLOR]started out fine then blurred....doing the below fix worked.
[ATTACH=CONFIG]249446[/ATTACH]


I have had this in one of my conkys and I think adding a **${font}** to the end fixed it.
eg
```
TEXT
${font Visitor TT1 BRK : pixelsize=12}${color1}Time${font}
${color3}${voffset -5}${hr}
${offset 15}${color1}${time %A %d %B %Y %H:%M:%S}
${offset 15}${color1}Uptime  : ${color3}${uptime}**[COLOR="#FF0000"]${font}[/COLOR]**
```
Also check you have the [**_[COLOR="#B22222"]Visitor font[/COLOR]_**]("http://www.dafont.com/visitor.font")

---

### Post by dfjarvis03 on 2014-01-12
Thanks stinkeye. I went back and tried that, and still didn't have much luck, so I tried putting a $font} tag at the end of EVERY line in the TEXT section, like the following, and while that seems silly, it did fix the problem. 

```

[COLOR=#000000][FONT=Ubuntu Mono]TEXT
[/FONT][/COLOR]${font Visitor TT1 BRK : pixelsize=12}${color1}Time${font}
${color3}${voffset -5}${hr}**[COLOR=#FF0000]${font}[/COLOR]**
${offset 15}${color1}${time %A %d %B %Y %H:%M:%S}**[COLOR=#FF0000]${font}[/COLOR]**
[COLOR=#000000][FONT=Ubuntu Mono]${offset 15}${color1}Uptime  : ${color3}${uptime}[/FONT][/COLOR][B][COLOR=#FF0000]${font}
[/COLOR][/B]
```

Also, yes, the first two lines of the config I provided in my original post were a copy/paste error, but thanks for catching it none the less!

---

### Post by stinkeye on 2014-01-12
> **dfjarvis03 said:**
> Thanks stinkeye. I went back and tried that, and still didn't have much luck, so I tried putting a $font} tag at the end of EVERY line in the TEXT section, like the following, and while that seems silly, it did fix the problem. 

```

[COLOR=#000000][FONT=Ubuntu Mono]TEXT
[/FONT][/COLOR]${font Visitor TT1 BRK : pixelsize=12}${color1}Time${font}
${color3}${voffset -5}${hr}**[COLOR=#FF0000]${font}[/COLOR]**
${offset 15}${color1}${time %A %d %B %Y %H:%M:%S}**[COLOR=#FF0000]${font}[/COLOR]**
[COLOR=#000000][FONT=Ubuntu Mono]${offset 15}${color1}Uptime  : ${color3}${uptime}[/FONT][/COLOR][B][COLOR=#FF0000]${font}
[/COLOR][/B]
```

Also, yes, the first two lines of the config I provided in my original post were a copy/paste error, but thanks for catching it none the less!

Yes, after it was running for a while it went blurry again.
What seemed to fix was using **${goto 15}** in place of  **${offset 15}**.
eg

```
TEXT
${font Visitor TT1 BRK : pixelsize=12}${color1}Time${font}
${color3}${voffset -5}${hr}
[COLOR="#FF0000"]${goto 15}[/COLOR]${color1}${time %A %d %B %Y %H:%M:%S}
[COLOR="#FF0000"]${goto 15}[/COLOR]${color1}Uptime  : ${color3}${uptime}${font}
```

Anyway , seems you have something that works.

---

