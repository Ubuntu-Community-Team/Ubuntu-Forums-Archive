---
title: "HELP!! Conky: you don't need that many fonts, sorry.  --(not the normal bug)"
date: 2016-05-31
forum: General Help
---

### Post by dave238 on 2016-05-31
Hi all,

I need a little assistance with conky. After a period of time i get the error message "Conky: you don't need that many fonts, sorry."

I have researched the error and this error is supposed to occur when conky tries to use more than 256 fonts.

The remedy for the problem is to balance out the $(font} calls on either side of any IF statements.

The trouble is........ i have removed all IF statements from conky and I still get the error!

I have a Lua script for conky which contains IF statements but not any ${font} changes......only ${color} changes.

I'm new to linux, scripting and conky so any help would be great.

Here is my conky code....

```
format_human_readable no
alignment top_right
background no
border_width 1
cpu_avg_samples 2
default_color white
default_outline_color white
default_shade_color white
draw_borders no
draw_graph_borders yes
draw_outline no
draw_shades no
use_xft yes
font Nimbus Mono L:size=12
gap_x 5
gap_y 5
minimum_size 5 5
net_avg_samples 2
no_buffers yes
out_to_console no
out_to_stderr no
extra_newline no
own_window yes
own_window_class Conky
own_window_type desktop
own_window_transparent yes
stippled_borders 0
update_interval 2.0
uppercase no
use_spacer none
show_graph_scale no
show_graph_range no
lua_load /home/dave/Documents/conky.lua.script.lua

TEXT
${color grey}${voffset -10}${hr}
${voffset -15}${hr}${lua_parse alert_func}
${voffset -13}${font Clubland:size=55}${alignc}${time %H}:${time %M}${color grey}
${voffset -50}${hr}
${voffset -80}${font URW Chancery L:size=16}${alignc}${time %A %d}#
${lua_parse add_letters_func} ${time %b} 
${voffset -17}${hr}${color white}
${font}Load:${font Heydings Icons:size=12}${goto 60}${color grey}W${color white}#
${font DejaVu Sans Mono:size=10}${voffset -2}${goto 85}${cpu}${font}${goto 105}#
${voffset -1}%${alignr}${color grey}${cpubar 6, 120}${color white}
${color white}Temp:${font Heydings Icons:size=12}${goto 60}${color grey}4#
${color white}${font DejaVu Sans Mono:size=10}${voffset -2}${goto 85}#
${acpitemp}${font}°c${goto 130}at:${font DejaVu Sans Mono:size=10}${goto 175}#
${freq}${font}${alignr}MHz
${color white}Jobs:${font Heydings Icons:size=12}${goto 60}${color grey}Y#
${color white}${font DejaVu Sans Mono:size=10}${voffset 0}${goto 85}#
${running_processes}${font}${goto 130}of:${font DejaVu Sans Mono:size=10}#
${goto 175}$processes${font}
${color white}RAM:${font Heydings Icons:size=12}${goto 60}${color grey}G#
${color white}${font DejaVu Sans Mono:size=10}${goto 85}${memperc}${font}#
${goto 105}${voffset -1}%${alignr}${color grey}${membar 6, 120}${color white}

${alignc}------ Networking ------
WiFi:${font Heydings Icons:size=12}${goto 60}${color grey}R${color white}#
${font Dejavu Sans Mono:size=10}${goto 85}${wireless_link_qual_perc wlan0}#
${font}${goto 105}%${alignr}${color grey}${wireless_link_bar 6, 120 wlan0}#
${color white}
SSID:${font Globe Icons:size=16}${goto 60}${color grey}b#
${color white}${font} ${color white}${voffset -3}#
${font DejaVu Sans Mono:size=10}${goto 85}${wireless_essid wlan0}#
${font}
IP:${font Heydings Icons:size=12}${goto 60}${color grey}g#
${color white}${font DejaVu Sans Mono:size=10} ${addr wlan0}#
${font}${color white}
Rate:${font Heydings Icons:size=12}${goto 60}${color grey}#
${voffset 1}d${color white}${font DejaVu Sans Mono:size=10} #
${voffset -1}${color white}${lua_parse down_only_func}${goto 160}${voffset -2}#
${font Heydings Icons:size=12}${color grey}u${color white}#
${font DejaVu Sans Mono:size=10} ${voffset -1}${lua_parse up_only_func}#
${font}

${color white}${alignc}------- Storage -------
${color white}Root:${goto 60}${font Heydings Icons:size=12}${color grey}F#
${font Dejavu Sans Mono:size=10} ${color white}${fs_used_perc /}${font}#
${goto 105}${voffset -1}% ${color white}${alignr}${color grey}${color grey}#
${fs_bar 6, 120 /}${color white}${font}
Home:${goto 60}${font Heydings Icons:size=12}${color grey}H#
${font Dejavu Sans Mono:size=10} ${color white}${fs_used_perc /home/dave}#
${font}${goto 105}${voffset -1}% ${color white}${alignr}${color grey}#
${fs_bar 6, 120 /home/dave}${color white}${font}
${color white}USB:${goto 60}${font Heydings Icons:size=12}${color grey}Z#
${font Dejavu Sans Mono:size=10} ${color white}${fs_used_perc /media/dave/4TBHDD}#
${font}${goto 105}${voffset -1}% ${color grey}${alignr}#
${fs_bar 6, 120 /media/dave/4TBHDD}${color white}${font}

${voffset -10}${color grey}$hr${font Nimbus Mono L:size=10}
${voffset -4}${color white}GMT: ${tztime Europe/London %R}${alignr}#
${color white}Uptime: ${color white}${uptime_short}
${voffset -8}${color grey}${hr}


```

....and the Lua script

```
--this rounds numbers to decimal places
local function round(num, idp)
  local mult = 10^(idp or 0)
  return math.floor(num * mult + 0.5) / mult
end

--this IS a sub func for up and down
local function up_down_func(up_down)
    up_down=up_down+0
    if up_down > 50000 or up_down == 0 then return ""
        elseif up_down <= 1024 then return "Bytes" 
        else up_down = up_down/1024
             up_down = round(up_down, 0)
        return string.format(up_down) .. "${goto 100} KB"
        end
end

--down function lands here
function conky_down_func()
    up_down=conky_parse("${downspeed wlan0}")
    return up_down_func(up_down)
end

--up function lands here ---
--TO DO change the assigned goto position on up/down
--then delete the old up and down functions for the more consice functions
function conky_up_func()
    up_down=conky_parse("${upspeed wlan0}")
    return up_down_func(up_down)
end
--this is a working date suffixer
function conky_add_letters_func()
    day1_31 = os.date("%d")
        if day1_31 == "1" or day1_31 == "21" or day1_31 == "31" then suffix = "st"
            elseif day1_31 == "2" or day1_31 == "22" then suffix = "nd"
            elseif day1_31 == "3" or day1_31 == "23" then suffix = "rd" 
            else suffix = "th" 
        end
    return string.format(suffix)
end

--this is down only concise function
function conky_down_only_func()
    up_down=conky_parse("${downspeed wlan0}")
    up_down=up_down+0
    if up_down > 50000 or up_down == 0 then return ""
        elseif up_down <= 1024 then return "Bytes"
        else up_down = up_down/1024
             up_down = round(up_down, 0)
        return string.format(up_down) .. "${goto 100} KB"
    end
end

--this is the up only function
function conky_up_only_func()
        up_down=conky_parse("${downspeed wlan0}")
        up_down=up_down+0
        if up_down > 50000 then return "Zero" end
        if up_down == 0 then
            return "Zero" 
        end
        if up_down <= 1024 then
            return  "Bytes"
        end
        if up_down > 1024 then
            up_down = up_down/1024
            up_down = round(up_down, 0)
            return string.format(up_down) .. "${alignr}KB"
        end
end

--this changes time colour on net loss
function conky_alert_func()
    --is internet online?
    alert=conky_parse("${addr wlan0}")
    --return string.format(alert)
    if alert=="No Address" then return "${color red}" 
        else return "${color white}" 
    end
end

--this will average cpu % over 4 cpus

function conky_frequency_func()
    freq=conky_parse("${freq 1}")
    freq=freq+conky_parse("${freq 2}")
    freq=freq+conky_parse("${freq 3}")
    freq=freq+conky_parse("${freq 4}")
    freq=freq/4
    freq=round(freq, 0)
    return string.format (freq)
end


```

..... and a screen shot in case that helps?

[ATTACH=CONFIG]269369[/ATTACH]

---

