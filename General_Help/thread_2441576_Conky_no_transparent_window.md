---
title: "Conky: no transparent window"
date: 2020-04-24
forum: General Help
---

### Post by ajgreeny on 2020-04-24
Clean install of Xubuntu 20.04 on my machine in dual boot with 18.04.

Conky will not show a transparent display on 20.04 but does so on 18.04 using the same .conkyrc config file. Anybody have any clues why this is happening?

I'm  not on that laptop at present so can't  attach the config file but will do so when  able.

---

### Post by CatKiller on 2020-04-24
> **ajgreeny said:**
> Anybody have any clues why this is happening?

Because conky is a largely unmaintained stack of hacks upon hacks, whose assumptions about how window managers behave are much less true than they were in the past? 

Sorry I can't give any concrete assistance. I find conky really useful, but it's transparency behaviour is just a complete nightmare. I have to keep a black section on my desktop wallpaper, for example, because otherwise the images become randomly transparent based on the luminance of the colours of the background. Been like that for years. 

Erm... Good luck!

---

### Post by ajgreeny on 2020-04-25
A lot of searching has found the answer in the forum for Xfce-4.14 at [https://forum.xfce.org/viewtopic.php?id=13723](https://forum.xfce.org/viewtopic.php?id=13723), which in post #7 suggests
```
own_window_transparent no
own_window_argb_visual yes
own_window_argb_value 145
```
Notice this is in the old config style, so I edited that to
```
own_window_transparent = true,
own_window_argb_visual = true,
own_window_argb_value = 145,
```
and now have full transparency again.

I am no expert with conky but have used it for many years and would miss it if it was not looking as I want it.  However I have no real idea what those extra code lines really mean; I'm just glad that they work.

EDIT:
I've been fiddling further and now find that the final of those three lines ***own_window_argb_value = 145,*** is not needed, only the line ***own_window_argb_visual = true,*** is needed for transparency.

---

### Post by Cavsfan on 2020-04-25
> **ajgreeny said:**
> A lot of searching has found the answer in the forum for Xfce-4.14 at [https://forum.xfce.org/viewtopic.php?id=13723](https://forum.xfce.org/viewtopic.php?id=13723), which in post #7 suggests
```
own_window_transparent no
own_window_argb_visual yes
own_window_argb_value 145
```
Notice this is in the old config style, so I edited that to
```
own_window_transparent = true,
own_window_argb_visual = true,
own_window_argb_value = 145,
```
and now have full transparency again.

I am no expert with conky but have used it for many years and would miss it if it was not looking as I want it.  However I have no real idea what those extra code lines really mean; I'm just glad that they work.

EDIT:
I've been fiddling further and now find that the final of those three lines ***own_window_argb_value = 145,*** is not needed, only the line ***own_window_argb_visual = true,*** is needed for transparency.

I meant to post a reply to this yesterday but, I see I didn't. If you want to adjust the transparency, comment out **own_window_transparent = true** and use **own_window_argb_visual = true** and the **own_window_argb_value** can be set to adjust the transparency.

```
    --own_window_transparent = true,
    -- if own_window_transparent is set to true then this value own_window_argb is irrelevant else can be set to anything 0 to 255
    own_window_argb_visual = true,
    own_window_argb_value = 40,
```

0 or not having the variable is true transparent 40 provides a little shade, 255 would of course be black. But, I like the range.

Since I could not get my conkys to work I took the conky that is default and adjusted it some mainly to give me the 2 most important things I want to know CPU and GPU temperatures.
I'll use this until I get a little further and can get the other to work. I have a 4k monitor so you might have some adjusting if you want to try this.
```
conky.config = {
    alignment = 'bottom_right',
    background = false,
    border_width = 1,
    cpu_avg_samples = 2,
    default_color = 'white',
    default_outline_color = 'white',
    default_shade_color = 'white',
    draw_borders = false,
    draw_graph_borders = true,
    draw_outline = false,
    draw_shades = false,
    use_xft = true,
    font = 'DejaVu Sans Mono:size=12',
    gap_x = 5,
    gap_y = 60,
    minimum_height = 5,
    minimum_width = 5,
    net_avg_samples = 2,
    no_buffers = true,
    out_to_console = false,
    out_to_stderr = false,
    extra_newline = false,

    --own_window = true,
    --own_window_class = 'Conky',
    --own_window_type = 'desktop',

    own_window_type = 'normal',
    -------------------------------------------------------------
    -- uncomment below hints line if not using override
    -------------------------------------------------------------
    own_window_hints = 'below,sticky,undecorated,skip_taskbar,skip_pager',

    own_window_class = 'Conky',
    own_window = true,
    --own_window_transparent = true,
    -- if own_window_transparent is set to true then this value own_window_argb is irrelevant else can be set to anything 0 to 255
    own_window_argb_visual = true,
    own_window_argb_value = 40,
    stippled_borders = 0,
    update_interval = 2.5,
    uppercase = false,
    use_spacer = 'none',
    show_graph_scale = false,
    show_graph_range = false
}

conky.text = [[
#${scroll 200 Xubuntu 20.04 - $sysname $kernel on $machine }
${alignr}${scroll 47 3 Xubuntu 20.04 (LTS) Focal Fossa -
$kernel on $machine }
$hr
${color grey}Uptime:$color $uptime
${color grey}Frequency (in MHz):$color $freq
${color grey}Frequency (in GHz):$color $freq_g
${color grey}RAM Usage:$color $mem/$memmax - $memperc% ${membar 4}
${color grey}Swap Usage:$color $swap/$swapmax - $swapperc% ${swapbar 4}
${color grey}CPU Usage:$color $cpu% ${cpubar 4}
${color grey}Processes:$color $processes  ${color grey}Running:$color $running_processes ${hr 1}
$hr
${color grey}File systems:
/ ${fs_used /}/${fs_size /} ${fs_bar 6 /}
/Media ${fs_used /Media}/${fs_size /Media} ${fs_bar 6 /}
$hr
${color grey}Networking:
Up:$color ${upspeed enp3s0} ${color grey} - Down:$color ${downspeed enp3s0} ${hr 1}
$hr
#${color grey}Video Card ${alignr}Driver:
${color grey}${execpi 1800 nvidia-smi -q | grep "Product Name" | sed -e 's/.*: /nVidia /'}${alignr}${execpi 1800 nvidia-smi -q | grep "Driver Version" | awk '{print $4}'}
#${color grey}${execpi 2 nvidia-smi --query-gpu=temperature.gpu --format=csv,noheader,nounits}x9/5+32°
${color grey}Video Card Temperature ${alignr}${execpi 2 nvidia-smi --query-gpu=temperature.gpu --format=csv,noheader,nounits}C°
${color grey}Processors $hr
${color grey}CPU1 ${cpu cpu1}%${goto 150}${cpubar cpu1 4,400} ${alignr}${execpi 3 sensors -f | grep -e "Core 0:" | awk '{print $3 " "'}}
${color grey}CPU2 ${cpu cpu2}%${goto 150}${cpubar cpu2 4,400} ${alignr}${execpi 3 sensors -f | grep -e "Core 1:" | awk '{print $3 " "'}}
${color grey}CPU3 ${cpu cpu3}%${goto 150}${cpubar cpu3 4,400} ${alignr}${execpi 3 sensors -f | grep -e "Core 2:" | awk '{print $3 " "'}}
${color grey}CPU4 ${cpu cpu4}%${goto 150}${cpubar cpu4 4,400} ${alignr}${execpi 3 sensors -f | grep -e "Core 3:" | awk '{print $3 " "'}}
${color grey}CPU Fan Speed:${alignr}${execpi 5 sensors -f | grep -e "fan2" |  awk '{print $2 " " $3}'}
#${color grey}${execpi 5 sensors -f | grep -e "Core 0:" | awk '{print $3 " "'}} ${execpi 5 sensors -f | grep -e "Core 1:" | awk '{print $3 " "'}} ${execpi 5 sensors -f | grep -e "Core 2:" | awk '{print $3 " "'}} ${execpi 5 sensors -f | grep -e "Core 3:" | awk '{print $3 " "'}}
$hr
${color grey}Process Name          PID      CPU%     MEM%
${color lightgrey} ${top name 1}    ${top pid 1}   ${top cpu 1}   ${top mem 1}
${color lightgrey} ${top name 2}    ${top pid 2}   ${top cpu 2}   ${top mem 2}
${color lightgrey} ${top name 3}    ${top pid 3}   ${top cpu 3}   ${top mem 3}
${color lightgrey} ${top name 4}    ${top pid 4}   ${top cpu 4}   ${top mem 4}
${color lightgrey} ${top name 5}    ${top pid 5}   ${top cpu 5}   ${top mem 5}
${color lightgrey} ${top name 6}    ${top pid 6}   ${top cpu 6}   ${top mem 6}
${color lightgrey} ${top name 7}    ${top pid 7}   ${top cpu 7}   ${top mem 7}
${color lightgrey} ${top name 8}    ${top pid 8}   ${top cpu 8}   ${top mem 8}
${color lightgrey} ${top name 9}    ${top pid 9}   ${top cpu 9}   ${top mem 9}
${color lightgrey} ${top name 10}    ${top pid 10}   ${top cpu 10}   ${top mem 10}

]]

```

[[IMG]http://i.imgur.com/OlFVjCol.png[/IMG]]("https://imgur.com/OlFVjCo")

---

