---
title: "if_match issue with conky"
date: 2013-03-04
forum: General Help
---

### Post by TazX on 2013-03-04
I'm running a conky2-desklet derived version of conky, which looks great, but I have just one more thing which I'd like to do, which is display a charging icon. My .conkyrc file runs fine from the terminal, and I get no errors, but the following line 'doesn't work.'

```
${if_match "${battery_short}" != "D"}${image ~/conky/charging.png -p 209,491}${else}${image ~/conky/discharging.png -p 209,491}$endif
```

The only image that shows up is the charging one (whether my laptop's plugged in or not).  Any ideas what I'm doing wrong? (I'm a noob)  I've been working on this for way too long, and my google-fu appears to have failed me.   Just in case I'll include the whole file, and the lua file, in case it's something in there.

.conkyrc
```
# Conky settings #background no
update_interval 1


cpu_avg_samples 2
net_avg_samples 2


override_utf8_locale yes


double_buffer yes
no_buffers yes


text_buffer_size 2048
#imlib_cache_size 0


temperature_unit celsius


# Window specifications #
own_window_class Conky
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below


border_inner_margin 0
border_outer_margin 0


minimum_size 350 550
maximum_width 550


alignment tr
gap_x -20
gap_y 185


# Graphics settings #
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no


# Text settings #
use_xft yes
override_utf8_locale yes
xftfont Pf Tempesta Five:bold:size=6
xftalpha 0.8
uppercase no


temperature_unit celsius


default_color 333333
color0 FB88EB
color1 363636
color2 1994D1
color3 1994D1 


# Lua Load  ##${voffset 700}
lua_load ~/conky/rings-v1.2.1.lua
lua_draw_hook_pre ring_stats


TEXT
${font Pf Tempesta Five:bold:size=6}${voffset 34}${goto 96}${color1}CPU ${alignr 145}${color1}${cpu}% / ${color1}${acpitemp}°C
${font Pf Tempesta Five:bold:size=6}${goto 79}${color1}RAM ${alignr 145}${color1}${memperc}% / ${color1}${memmax}
${font Pf Tempesta Five:bold:size=6}${goto 63}${color1}GPU ${alignr 145}${color1}${nvidia gpufreq} / ${color1}540 MHz
${font Pf Tempesta Five:bold:size=6}${goto 48}Uptime${color1}${alignr 145}${uptime_short}
${font Xirod:size=10}${color0}${voffset 3}${offset 20}SYSTEM


${font Xirod:size=8}${color0}${voffset 80}${goto 184}NETWORK
${font Pf Tempesta Five:bold:size=6}${goto 146}${color1}Up${goto 195}${color1}${totalup eth1} / ${color1}${upspeed eth1}
${font Pf Tempesta Five:bold:size=6}${goto 146}${voffset 0}Down${goto 205}${color1}${totaldown eth1} / ${color1}${downspeed eth1}


${font Pf Tempesta Five:bold:size=6}${goto 107}${voffset 4}Rot${color1}${alignr 135}${fs_used_perc /}% / ${color1}${fs_size /}
${font Pf Tempesta Five:bold:size=6}${goto 95}Home${alignr 135}${color1}${fs_used_perc /home}% / ${color1}${fs_size /home}
${font Pf Tempesta Five:bold:size=6}${goto 86}Usb${alignr 135}${color1}${fs_used_perc /media/usb0}% / ${color1}${fs_size /media/usb0}
${font Xirod:size=8}${color0}${goto 56}${voffset 16}HARD DRIVE


${font Xirod:size=8}${goto 186}${voffset 66}${color0}${time %d} ${ fcolor0}${time %A}


${font Xirod:size=8}${color0}${goto 168}${voffset 12}${color1}${battery_percent BAT0}%
${font Xirod:size=8}${color0}${goto 106}${voffset 10}BATTERY


${if_match "${battery_short}" != "D"}${image ~/conky/charging.png -p 209,491}${else}${image ~/conky/discharging.png -p 209,491}${endif}

```

And the lua file:
```
--[[Ring Meters by londonali1010 (2009)


This script draws percentage meters as rings. It is fully customisable; all options are described in the script.


IMPORTANT: if you are using the 'cpu' function, it will cause a segmentation fault if it tries to draw a ring straight away. The if statement near the end of the script uses a delay to make sure that this doesn't happen. It calculates the length of the delay by the number of updates since Conky started. Generally, a value of 5s is long enough, so if you update Conky every 1s, use update_num > 5 in that if statement (the default). If you only update Conky every 2s, you should change it to update_num > 3; conversely if you update Conky every 0.5s, you should use update_num > 10. ALSO, if you change your Conky, is it best to use "killall conky; conky" to update it, otherwise the update_num will not be reset and you will get an error.


To call this script in Conky, use the following (assuming that you save this script to ~/scripts/rings.lua):
    lua_load ~/scripts/rings-v1.2.1.lua
    lua_draw_hook_pre ring_stats
    
Changelog:
+ v1.2.1 -- Fixed minor bug that caused script to crash if conky_parse() returns a nil value (20.10.2009)
+ v1.2 -- Added option for the ending angle of the rings (07.10.2009)
+ v1.1 -- Added options for the starting angle of the rings, and added the "max" variable, to allow for variables that output a numerical value rather than a percentage (29.09.2009)
+ v1.0 -- Original release (28.09.2009)
]]


settings_table = {


    {
        name='cpu',
        arg='cpu0',
        max=100,
        bg_colour=0x363636,
        bg_alpha=1.0,
        fg_colour=0xFB88EB,
        fg_alpha=0.8,
        x=215, y=108,
        radius=70,
        thickness=20,
        start_angle=0,
        end_angle=270
    },
    {
        name='memperc',
        arg='',
        max=100,
        bg_colour=0x363636,
        bg_alpha=0.6,
        fg_colour=0xFB88EB,
        fg_alpha=0.8,
        x=215, y=108,
        radius=50,
        thickness=15,
        start_angle=0,
        end_angle=270
    },
        {
        name='nvidia',
        arg='gpufreq',
        max=540,
        bg_colour=0x363636,
        bg_alpha=0.4,
        fg_colour=0xFB88EB,
        fg_alpha=0.8,
        x=215, y=108,
        radius=35,
        thickness=10,
        start_angle=0,
        end_angle=270
    },
    {
        name='fs_used_perc',
        arg='/',
        max=100,
        bg_colour=0x363636,
        bg_alpha=1.0,
        fg_colour=0xFB88EB,
        fg_alpha=0.8,
        x=220, y=328,
        radius=40,
        thickness=15,
        start_angle=0,
        end_angle=270
    },
    {
        name='fs_used_perc',
        arg='/home',
        max=100,
        bg_colour=0x363636,
        bg_alpha=0.6,
        fg_colour=0xFB88EB,
        fg_alpha=0.8,
        x=220, y=328,
        radius=25,
        thickness=10,
        start_angle=0,
        end_angle=270
    },
    {
        name='fs_used_perc',
        arg='/media/usb0',
        max=100,
        bg_colour=0x363636,
        bg_alpha=0.4,
        fg_colour=0xFB88EB,
        fg_alpha=0.8,
        x=220, y=328,
        radius=15,
        thickness=5,
        start_angle=0,
        end_angle=270
    },
    {
        name='upspeedf',
        arg='eth1',
        max=1000,
        bg_colour=0x363636,
        bg_alpha=1.0,
        fg_colour=0xFB88EB,
        fg_alpha=0.8,
        x=140, y=224,
        radius=30,
        thickness=12,
        start_angle=180,
        end_angle=450
    },
    {
        name='downspeedf',
        arg='eth1',
        max=100,
        bg_colour=0x363636,
        bg_alpha=0.6,
        fg_colour=0xFB88EB,
        fg_alpha=0.8,
        x=140, y=224,
        radius=18,
        thickness=8,
        start_angle=180,
        end_angle=450
    },
    {
        name='time',
        arg='%S',
        max=60,
        bg_colour=0x363636,
        bg_alpha=1.0,
        fg_colour=0xFB88EB,
        fg_alpha=0.8,
        x=152, y=418,
        radius=30,
        thickness=12,
        start_angle=0,
        end_angle=360
    },
     {
        name='time',
        arg='%M',
        max=60,
        bg_colour=0x363636,
        bg_alpha=0.6,
        fg_colour=0xFB88EB,
        fg_alpha=0.8,
        x=152, y=418,
        radius=18,
        thickness=8,
        start_angle=0,
        end_angle=360
    },
    {
        name='time',
        arg='%I',
        max=12,
        bg_colour=0x363636,
        bg_alpha=0.4,
        fg_colour=0xFB88EB,
        fg_alpha=0.8,
        x=152, y=418,
        radius=10,
        thickness=4,
        start_angle=0,
        end_angle=360
    },
       {
        name='battery_percent',
        arg='BAT0',
        max=100,
        bg_colour=0x363636,
        bg_alpha=0.6,
        fg_colour=0xFB88EB,
        fg_alpha=0.8,
        x=220, y=502,
        radius=18,
        thickness=10,
        start_angle=0,
        end_angle=270
    },
}


-- Use these settings to define the origin and extent of your clock.


clock_r=36


-- "clock_x" and "clock_y" are the coordinates of the centre of the clock, in pixels, from the top left of the Conky window.


clock_x=152
clock_y=418


show_seconds=true


require 'cairo'


function rgb_to_r_g_b(colour,alpha)
    return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
end


function draw_ring(cr,t,pt)
    local w,h=conky_window.width,conky_window.height
    
    local xc,yc,ring_r,ring_w,sa,ea=pt['x'],pt['y'],pt['radius'],pt['thickness'],pt['start_angle'],pt['end_angle']
    local bgc, bga, fgc, fga=pt['bg_colour'], pt['bg_alpha'], pt['fg_colour'], pt['fg_alpha']


    local angle_0=sa*(2*math.pi/360)-math.pi/2
    local angle_f=ea*(2*math.pi/360)-math.pi/2
    local t_arc=t*(angle_f-angle_0)


    -- Draw background ring


    cairo_arc(cr,xc,yc,ring_r,angle_0,angle_f)
    cairo_set_source_rgba(cr,rgb_to_r_g_b(bgc,bga))
    cairo_set_line_width(cr,ring_w)
    cairo_stroke(cr)
    
    -- Draw indicator ring


    cairo_arc(cr,xc,yc,ring_r,angle_0,angle_0+t_arc)
    cairo_set_source_rgba(cr,rgb_to_r_g_b(fgc,fga))
    cairo_stroke(cr)        
end


function draw_clock_hands(cr,xc,yc)
    local secs,mins,hours,secs_arc,mins_arc,hours_arc
    local xh,yh,xm,ym,xs,ys
    
    secs=os.date("%S")    
    mins=os.date("%M")
    hours=os.date("%I")
        
    secs_arc=(2*math.pi/60)*secs
    mins_arc=(2*math.pi/60)*mins+secs_arc/60
    hours_arc=(2*math.pi/12)*hours+mins_arc/12
        
    -- Draw hour hand
    
    xh=xc+0.62*clock_r*math.sin(hours_arc)
    yh=yc-0.62*clock_r*math.cos(hours_arc)
    cairo_move_to(cr,xc,yc)
    cairo_line_to(cr,xh,yh)
    
    cairo_set_line_cap(cr,CAIRO_LINE_CAP_SQUARE)
    cairo_set_line_width(cr,1)
    cairo_set_source_rgba(cr,0.804,0.149,0.380,1.0)
    cairo_stroke(cr)
    
    -- Draw minute hand
    
    xm=xc+clock_r*math.sin(mins_arc)
    ym=yc-clock_r*math.cos(mins_arc)
    cairo_move_to(cr,xc,yc)
    cairo_line_to(cr,xm,ym)
    
    cairo_set_line_width(cr,1)
    cairo_stroke(cr)
    
    -- Draw seconds hand
    
    if show_seconds then
        xs=xc+clock_r*math.sin(secs_arc)
        ys=yc-clock_r*math.cos(secs_arc)
        cairo_move_to(cr,xc,yc)
        cairo_line_to(cr,xs,ys)
    
        cairo_set_line_width(cr,1)
        cairo_stroke(cr)
    end
end


function conky_ring_stats()
    local function setup_rings(cr,pt)
        local str=''
        local value=0
        
        str=string.format('${%s %s}',pt['name'],pt['arg'])
        str=conky_parse(str)
        
        value=tonumber(str)
        if value == nil then value = 0 end
        pct=value/pt['max']
        
        draw_ring(cr,pct,pt)
    end


    if conky_window==nil then return end
    local cs=cairo_xlib_surface_create(conky_window.display,conky_window.drawable,conky_window.visual, conky_window.width,conky_window.height)
    
    local cr=cairo_create(cs)    
    
    local updates=conky_parse('${updates}')
    update_num=tonumber(updates)
    
    if update_num>5 then
        for i in pairs(settings_table) do
            setup_rings(cr,settings_table[i])
        end
    end
   
    -- Check that Conky has been running for at least 5s


    if conky_window==nil then return end
    local cs=cairo_xlib_surface_create(conky_window.display,conky_window.drawable,conky_window.visual, conky_window.width,conky_window.height)
    
    local cr=cairo_create(cs)    
    
    local updates=conky_parse('${updates}')
    update_num=tonumber(updates)
    
    if update_num>5 then
        for i in pairs(settings_table) do
            setup_rings(cr,settings_table[i])

        end
    end
    draw_clock_hands(cr,clock_x,clock_y)
end
```

In case it helps here's what I've done so far.  I'd really love the ring in the centre of the 'Battery' section to change state, depending on whether I'm charging or not.
[http://imageshack.us/photo/my-images/201/magneta.png/](http://imageshack.us/photo/my-images/201/magneta.png/)

Thanks a bunch!

---

### Post by stinkeye on 2013-03-04
I would suggest putting in another line with just
```
${battery_short}
```
to test what your actual output for $battery_short is.
It may not be changing.

From man conky....
> battery_short (num) 
 Battery status and remaining percentage capacity of ACPI or APM battery. ACPI battery number can be given as argument (default is BAT0). This mode display a short status, which means that **C** is displayed instead of charging, **D** for discharging, **F** for full, **N** for not present, **E** for empty and **U** for unknown.

P.S. Wealth of knowledge here...
[**_[COLOR="#B22222"]Post your .conkyrc files w/ screenshots[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=281865&page=2167")

---

### Post by TazX on 2013-03-04
Hmm, there is a small delay in the change from C to D (and vica versa), but the letter does come up.  I get a C 88% (the battery percent) when charging, and the same (but with a D) for discharging.  So that works.  :/

---

### Post by stinkeye on 2013-03-04
Try adding this to your config above "TEXT"
```
imlib_cache_size 0
#imlib_cache_flush_interval 900
```
First line disables the image cache.
Not sure about the second line. Uncomment the second line if still doesn't work.
Do not really know how either works but is in one of my configs 
that changes a pic every minute.

Could also test the syntax of your code with
```
${if_match "${battery_short}" != "D"}Does not=D${else}Does=D$endif
```

The code looks ok but I don't have a laptop to test.
Try the thread I linked to, and someone may be able to test.

---

### Post by TazX on 2013-03-04
Ah...  At least now I know the issue is in the if_match part of the equation.  Thanks!  I did uncomment the image cache line though - thanks.  That could have, quite easily, been the issue.  I'll head off to that thread now.  :)

---

### Post by TazX on 2013-03-06
Wow, okay, so it seems that < means 'contains?' I knew that's what I needed, since the if_match needed an exact match to work.  As shown by testing the code with F instead of D:
```
[COLOR=#000000][FONT=Ubuntu Mono]${if_match "${battery_short}" != "D"}${image ~/conky/charging.png -p 209,491}${else}${image ~/conky/discharging.png -p 209,491}$endif
```
[/FONT][/COLOR]
Whatever the reason, my battery indicator now works.  Super stoked!
```
${if_match "$battery_short"<"D"}${image ~/conky/charging.png -p 209,491}$else${image ~/conky/discharging.png -p 209,491}${endif}
```

---

### Post by stinkeye on 2013-03-06
Just curious.
How did you find out about....  
< means 'contains?'

---

### Post by TazX on 2013-03-06
I don't.  I just guessed.  It said in the man pages that < was a valid option, and my improved google foo found a conky which used it, so I gave it a go and that seems to be the effect I achieved.  In the end this is the line I used:
```
${if_match "$battery_short"=="F"}${image ~/conky/full.png -p 209,491}${else}${if_match "$battery_short"<"D"}${image ~/conky/charging.png -p 209,491}$else${image ~/conky/discharging.png -p 209,491}${endif}
```
as the image would change back to the discharging one when the battery was full.

Actually, on second thoughts it must mean 'doesn't contain' - or may even mean greater than (and count the letters in numbers), in which case C is 'less than' D, but F, and U...

No, Heh, I don't really know what it means tbh, but it's working.  :)

---

### Post by stinkeye on 2013-03-06
> **TazX said:**
> 

No, Heh, I don't really know what it means tbh, but it's working.  :)
As long as it works. :)

---

### Post by Habitual on 2013-03-06
late to the party. but here's another working example for your conky skill-set/code stash...
```
${if_match ${wireless_link_qual wlan0} < 31}${color orange}bad$color$else${if_match ${wireless_link_qual wlan0} < 51}${color yellow}weak
```

---

