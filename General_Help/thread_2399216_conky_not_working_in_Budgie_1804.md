---
title: "conky not working in Budgie 1804"
date: 2018-08-22
forum: General Help
---

### Post by chaopoch on 2018-08-22
try many ways and find no solutions
here are error message and my config file
thanks for help

```

~/Conky$ conky -c conky-status
conky: warning: invalid head index, ignoring head settings
conky: warning: invalid head index, ignoring head settings
conky: desktop window (1e00011) is subwindow of root window (14c)
conky: window type - normal
conky: drawing to created window (0x5a00002)
conky: drawing to double buffer
Floating point exception (core dumped)
```


```


conky.config = {
    alignment = 'top_left',
    background = false,
    border_width = 1,
    border_inner_margin = 5,
    border_outer_margin = 0,
    cpu_avg_samples = 2,
    default_color = 'white',
    default_outline_color = '22ee99',
    default_shade_color = '002200',
    double_buffer = true,
    draw_borders = false,
    draw_graph_borders = false,
    draw_outline = false,
    draw_shades = false,
    extra_newline = false,
    gap_x = 20,
    gap_y = 30,
    imlib_cache_size = 0,
    minimum_height = 250,
    minimum_width = 800,
    net_avg_samples = 2,
    no_buffers = true,
    out_to_console = false,
    out_to_stderr = false,
    override_utf8_locale = true,
    own_window = true,
    own_window_argb_visual = true,
    own_window_hints = 'undecorated,below,sticky,skip_taskbar,skip_pager',
    own_window_class = 'Conky',
    own_window_type = 'normal',
    own_window_transparent = true,
    show_graph_scale = false,
    show_graph_range = false,
    stippled_borders = 0,
    text_buffer_size = 32768,
    update_interval = 1.0,
    uppercase = false,
    use_spacer = 'none',
    use_xft = true,
    font = 'xftalpha:size=0.8',
    xftalpha=1,
    xinerama_head = 1

}

conky.text = [[
${color #808080}Uptime:${color #999999} $uptime
${color #808080}CPU Frequency: ${color #999999}${execi 2 cpufreq-info -p | awk '{printf $3}'}  ${color #999999} $freq_g GHz
${color #808080}RAM ($memmax): ${color #999999} $mem ${color #808080}($memperc%)
${color #808080}SWAP ($swapmax):${color #999999} $swap ${color #808080}($swapperc%)
${voffset -52}
${offset 180}${color #808080}CPU1 : ${color #999999}${cpu cpu1}%
${offset 180}${color #808080}CPU2 : ${color #999999}${cpu cpu2}%
${offset 180}${color #808080}CPU3 : ${color #999999}${cpu cpu3}%
${offset 180}${color #808080}CPU4 : ${color #999999}${cpu cpu4}%
${voffset -52}
${offset 330}${color #808080}File System: ${color #999999}${fs_type /}
${offset 330}${color #808080}HDD Temp (60°C):${color #999999} ${hddtemp /dev/sda} °C
${offset 330}${color #808080}root : ${color #999999}${fs_free /} /${fs_size /} ${color #808080}(${fs_free_perc /}% Free)
${offset 330}${color #808080}sda2: ${color #999999}${fs_free /media/sda2} /${fs_size /media/sda2} ${color #808080}(${fs_free_perc /media/sda2}% Free)
${voffset -65}
${offset 530}${color #808080}Network:  ${color #999999}eno1
${offset 530}${color #808080}IP:${color #999999} ${addr eno1}
${offset 530}${color #808080}Upload:     ${color #999999} ${upspeed eno1} /s 
${offset 530}${color #808080}Download:${color #999999} ${downspeed eno1} /s
${voffset -65}
${offset 665}${color #808080}Power Usage (AC) : ${color #999999}${execi 2 /usr/sbin/powertop -c --time=0 |cut -c30-33} W
${offset 665}${color #808080}Highest          ${alignr}CPU(%)    Mem(%)${color #999999}
${offset 665}${top name 1}          ${alignr 26}${top cpu 1}  ${alignr 10}${top mem 1}
${offset 665}${top name 2}          ${alignr 26}${top cpu 2}  ${alignr 10}${top mem 2}
]]


```

---

### Post by Frogs Hair on 2018-08-22
I copied the syntax and got this error on Budgie. 

```
conky: Syntax error (/home/d-book/.conkyrc:76: '=' expected near '/') while reading config file. 
conky: Assuming it's in old syntax and attempting conversion.
conky: [string "..."]:139: attempt to index local 'settings' (a nil value)

```

---

### Post by chaopoch on 2018-08-22
thanks for reply,

do you know how to solve it?

---

### Post by QIII on 2018-08-22
Hello!
 
It would be helpful if you posted the entirety of your conky.rc.

---

### Post by chaopoch on 2018-08-22
> **QIII said:**
> Hello!
 
It would be helpful if you posted the entirety of your conky.rc.


I already post it

---

### Post by QIII on 2018-08-22
Forgive me.  That was not clear from the way it was originally formatted.

---

### Post by again? on 2018-08-23
The floating point error is coming from the line...
```
font = 'xftalpha:size=0.8',
```

Use something like...
```
font = 'Ubuntu Mono:bold:size=8',
```

---

### Post by chaopoch on 2018-08-23
> **guber2 said:**
> The floating point error is coming from the line...
```
font = 'xftalpha:size=0.8',
```

Use something like...
```
font = 'Ubuntu Mono:bold:size=8',
```

Thanks a lot!
problem is solved

---

