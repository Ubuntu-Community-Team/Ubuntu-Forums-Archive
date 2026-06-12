---
title: "how to let conky rings to change colors"
date: 2019-07-24
forum: General Help
---

### Post by koper97 on 2019-07-24
how to let conky rings to change colors.?
i mean - i have in lua script ring for battery, in blue, i wanna live this color voor 100% charged battery, 
but let change color dependend how battery charget is (red for lower than 30%). 

here is my lua script:
```

--[[
Clock Rings by londonali1010 (2009)
Configuration by Ninquitassar (2012)


This script draws percentage meters as rings, and also draws clock hands if you want! It is fully customisable; all options are described in the script. This script is based off a combination of my clock.lua script and my rings.lua script.


IMPORTANT: if you are using the 'cpu' function, it will cause a segmentation fault if it tries to draw a ring straight away. The if statement near the end of the script uses a delay to make sure that this doesn't happen. It calculates the length of the delay by the number of updates since Conky started. Generally, a value of 5s is long enough, so if you update Conky every 1s, use update_num > 5 in that if statement (the default). If you only update Conky every 2s, you should change it to update_num > 3; conversely if you update Conky every 0.5s, you should use update_num > 10. ALSO, if you change your Conky, is it best to use "killall conky; conky" to update it, otherwise the update_num will not be reset and you will get an error.


To call this script in Conky, use the following (assuming that you save this script to ~/scripts/rings.lua):
  lua_load ~/scripts/clock_rings-v1.1.1.lua
  lua_draw_hook_pre clock_rings


Changelog:
+ v1.1.1 -- Fixed minor bug that caused the script to crash if conky_parse() returns a nil value (20.10.2009)
+ v1.1 -- Added colour option for clock hands (07.10.2009)
+ v1.0 -- Original release (30.09.2009)
]]


settings_table = {
  --[[Anneau des heures
  {
    name='time',
    arg='%I.%M',
    max=12,
    bg_colour=0xffffff,
    bg_alpha=0.1,
    fg_colour=0xffffff,
    fg_alpha=0.2,
    x=60, y=70,
    radius=40,
    thickness=5,
    start_angle=0,
    end_angle=360
  },
  --Anneau des minutes
  {
    name='time',
    arg='%M.%S',
    max=60,
    bg_colour=0xffffff,
    bg_alpha=0.1,
    fg_colour=0xffffff,
    fg_alpha=0.4,
    x=60, y=70,
    radius=46,
    thickness=5,
    start_angle=0,
    end_angle=360
  },]]
  --Anneau des secondes
  {
    name='time',
    arg='%S',
    max=60,
    bg_colour=0xffffff,
    bg_alpha=0.1,
    fg_colour=0x25d9ff,		--zegar - sekundy
    fg_alpha=0.6,
    x=60, y=82,
    radius=55,
    thickness=3,
    start_angle=0,
    end_angle=360
  },
 {
    name='time',
    arg='%M.%S',
    max=60,
    bg_colour=0xffffff,
    bg_alpha=0.1,
    fg_colour=0x25d9ff,		--zegar - minuty
    fg_alpha=0.6,
    x=60, y=82,
    radius=44,
    thickness=10,
    start_angle=0,
    end_angle=360
  },
 {
    name='time',
    arg='%I.%M',
    max=12,
    bg_colour=0xffffff,
    bg_alpha=0.1,
    fg_colour=0x25d9ff,		--zegar - godziny
    fg_alpha=0.6,
    x=60, y=82,
    radius=34,
    thickness=3,
    start_angle=0,
    end_angle=360
  },
  {
    name='battery_percent',
    arg='BAT1',
    max=100,
    bg_colour=0xffffff,
    bg_alpha=0.1,
    fg_colour=0x25d9ff,		--bateria - kolor
    fg_alpha=0.6,
    x=120, y=170,
    radius=35,
    thickness=4,
    start_angle=0,
    end_angle=360
  },
{
    name='cpu',
    arg='cpu1',
    max=100,
    bg_colour=0xffffff,
    bg_alpha=0.1,
    fg_colour=0xf92626,		--procesor 1
    fg_alpha=0.6,
    x=155, y=252,
    radius=40,
    thickness=10,
    start_angle=0,
    end_angle=360
  },
{
    name='cpu',
    arg='cpu2',
    max=100,
    bg_colour=0xffffff,
    bg_alpha=0.1,
    fg_colour=0xf92626,		--proceor 2
    fg_alpha=0.6,
    x=155, y=252,
    radius=25,
    thickness=5,
    start_angle=0,
    end_angle=360
  },
{
    name='memperc',
    arg='',
    max=100,
    bg_colour=0xffffff,
    bg_alpha=0.1,
    fg_colour=0x25d9ff,		--RAM /
    fg_alpha=0.6,
    x=105, y=375,
    radius=58,
    thickness=3,
    start_angle=0,
    end_angle=360
  },
{
    name='fs_used_perc',
    arg='/',
    max=100,
    bg_colour=0xffffff,
    bg_alpha=0.1,
    fg_colour=0xf92626,		--root
    fg_alpha=0.6,
    x=105, y=375,
    radius=50,
    thickness=5,
    start_angle=0,
    end_angle=360
  },
{
    name='fs_used_perc',
    arg='/var',
    max=100,
    bg_colour=0xffffff,
    bg_alpha=0.1,
    fg_colour=0xd7d7d7,
    fg_alpha=0.6,
    x=105, y=375,
    radius=43,
    thickness=3,
    start_angle=0,
    end_angle=360
  },
{
    name='fs_used_perc',
    arg='/home',
    max=100,
    bg_colour=0xffffff,		--kolor t&#322;a paska
    bg_alpha=0.1,
    fg_colour=0xf00fff,		--home
    fg_alpha=0.6,
    x=105, y=375,
    radius=36,
    thickness=5,
    start_angle=0,
    end_angle=360
  },
}


--Use these settings to define the origin and extent of your clock.
  clock_r=50


--Coordinates of the centre of the clock, in pixels, from the top left of the Conky window.
  clock_x=60
  clock_y=82


--Colour & alpha of the clock hands
  clock_colour=0xf00fff 	--wskazówki
  clock_alpha=0.6


--Show the seconds hand ?
  show_seconds=true


require 'cairo'


function rgb_to_r_g_b(colour,alpha)
  return ((colour / 0x10000) % 0x100) / 155., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
end


function draw_ring(cr,t,pt)
  local w,h=conky_window.width,conky_window.height


  local xc,yc,ring_r,ring_w,sa,ea=pt['x'],pt['y'],pt['radius'],pt['thickness'],pt['start_angle'],pt['end_angle']
  local bgc, bga, fgc, fga=pt['bg_colour'], pt['bg_alpha'], pt['fg_colour'], pt['fg_alpha']


  local angle_0=sa*(2*math.pi/360)-math.pi/2
  local angle_f=ea*(2*math.pi/360)-math.pi/2
  local t_arc=t*(angle_f-angle_0)


  --Draw background ring
  cairo_arc(cr,xc,yc,ring_r,angle_0,angle_f)
  cairo_set_source_rgba(cr,rgb_to_r_g_b(bgc,bga))
  cairo_set_line_width(cr,ring_w)
  cairo_stroke(cr)


  --Draw indicator ring
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


  --Draw hour hand
  xh=xc+0.65*clock_r*math.sin(hours_arc)
  yh=yc-0.65*clock_r*math.cos(hours_arc)
  cairo_move_to(cr,xc,yc)
  cairo_line_to(cr,xh,yh)
  --
  cairo_set_line_cap(cr,CAIRO_LINE_CAP_ROUND)
  cairo_set_line_width(cr,5)
  cairo_set_source_rgba(cr,rgb_to_r_g_b(clock_colour,clock_alpha))
  cairo_stroke(cr)


  --Draw minute hand
  xm=xc+0.95*clock_r*math.sin(mins_arc)
  ym=yc-0.95*clock_r*math.cos(mins_arc)
  cairo_move_to(cr,xc,yc)
  cairo_line_to(cr,xm,ym)
  --
  cairo_set_line_width(cr,3)
  cairo_stroke(cr)


  -- Draw seconds hand
  if show_seconds then
    xs=xc+1.1*clock_r*math.sin(secs_arc)
    ys=yc-1.1*clock_r*math.cos(secs_arc)
    cairo_move_to(cr,xc,yc)
    cairo_line_to(cr,xs,ys)
    --
    cairo_set_line_width(cr,1)
    cairo_stroke(cr)
  end
end


function conky_clock_rings()
  local function setup_rings(cr,pt)
  local str=''
  local value=0


  str=string.format('${%s %s}',pt['name'],pt['arg'])
  str=conky_parse(str)


  value=tonumber(str)
  if value == nil then value = 0 end


--Les ajouts suivants permettent de corriger le retard prit par les anneaux
  --Ajout wlourf : conversion des minutes en centièmes d'heures
  if pt['arg'] == "%I.%M"  then
    value=os.date("%I")+os.date("%M")/60
    if value>12 then value=value-12 end
  end


  --Ajout Fenouille84 : conversion des secondes en centièmes de minutes
  if pt['arg'] == "%M.%S"  then
    value=os.date("%M")+os.date("%S")/60
  end
  --Fin ajout


  pct=value/pt['max']
  draw_ring(cr,pct,pt)
end


--Check that Conky has been running for at least 5s
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



i found on internet one working script with changing colors of clock. here it is:
```

--[[
    Colour Change Rings v1.1 by mrmrwat (25.03.2013)
    based on Ring Meters v1.2.1 by londonali1010 (20.10.2009)
    and inspired by PolarClock by pixelbreaker
    
    v1.1 -- Supports time indicators up to year of the century
         -- Includes a few code clean ups
    v1.0 -- Original release
         -- Includes support for colour change rings and
         -- millisecond precision for smooth movement
         
    Planned changes include:
         -- Breaking some of the larger code segments out into
            dedicated functions
         -- Automating colour change option detection to allow
            efficient use of variables and functions only used
            by colour change code
         -- More colour change presets
    
    NB. Requires lua socket for socket.gettime() function
--]]


require 'cairo'
require 'socket'


settings_table = {
    {
        -- Year of the century indicator
        name = 'time',
        arg = '%y',
        max = 100,
        bg_colour = 0xffffff,
        bg_alpha = 0.1,
        fg_colour = 'rainbow_bgr',
        fg_alpha = 0.7,
        x = 180, y = 180,
        radius = 160,
        thickness = 4,
        start_angle = -60,
        end_angle = 60
    },
    {
        -- Day of the year indicator
        name = 'time',
        arg = '%j',
        max = 366,
        bg_colour = 0xffffff,
        bg_alpha = 0.1,
        fg_colour = 'rainbow_bgr',
        fg_alpha = 0.7,
        x = 180, y = 180,
        radius = 150,
        thickness = 6,
        start_angle = -60,
        end_angle = 60
    },
    {
        -- Day of the month indicator
        name = 'time',
        arg = '%d',
        -- max is reset in the setup_rings function depending on the month
        max = 31,
        bg_colour = 0xffffff,
        bg_alpha = 0.1,
        fg_colour = 'rainbow_bgr',
        fg_alpha = 0.7,
        x = 180, y = 180,
        radius = 160,
        thickness = 4,
        start_angle = 120,
        end_angle = 240
    },
    {
        -- Day of the week indicator
        name = 'time',
        arg = '%u',
        max = 7,
        bg_colour = 0xffffff,
        bg_alpha = 0.1,
        fg_colour = 'rainbow_bgr',
        fg_alpha = 0.7,
        x = 180, y = 180,
        radius = 150,
        thickness = 6,
        start_angle = 120,
        end_angle = 240
    },
    {
        -- Hour indicator
        name = 'time',
        arg = '%I',
        max = 12,
        bg_colour = 0xffffff,
        bg_alpha = 0.1,
        fg_colour = 'rainbow_bgr',
        fg_alpha = 0.7,
        x = 180, y = 180,
        radius = 75,
        thickness = 12,
        start_angle = 0,
        end_angle = 360
    },
    -- Uncomment below and comment out above for 24 hour clock
    {
        -- 24 hour indicator
        name = 'time',
        arg = '%H',
        max = 24,
        bg_colour = 0xffffff,
        bg_alpha = 0.1,
        fg_colour = 'rainbow_bgr',
        fg_alpha = 0.6,
        x = 146, y = 165,
        radius = 75,
        thickness = 12,
        start_angle = 0,
        end_angle = 360
    },
    {
        -- Minute indicator
        name = 'time',
        arg = '%M',
        max = 60,
        bg_colour = 0xffffff,
        bg_alpha = 0.1,
        fg_colour = 'rainbow_bgr',
        fg_alpha = 0.7,
        x = 180, y = 180,
        radius = 90,
        thickness = 7,
        start_angle = 0,
        end_angle = 360
    },
    {
        -- Second indicator
        name = 'time',
        arg = '%S',
        max = 60,
        bg_colour = 0xffffff,
        bg_alpha = 0.1,
        fg_colour = 'rainbow_bgr',
        fg_alpha = 0.7,
        x = 180, y = 180,
        radius = 120,
        thickness = 4,
        start_angle = 0,
        end_angle = 360
    },
}


function rgb_to_r_g_b(colour, alpha)
    return ((colour / 0x10000) % 0x100) / 255.,
        ((colour / 0x100) % 0x100) / 255.,
        (colour % 0x100) / 255.,
        alpha
end


function draw_ring(cr, t, pt)
    local w, h = conky_window.width, conky_window.height
    
    local xc, yc, ring_r, ring_w, sa, ea = pt['x'], pt['y'],
        pt['radius'], pt['thickness'],
        pt['start_angle'], pt['end_angle']
    local bgc, bga, fgc, fga = pt['bg_colour'], pt['bg_alpha'],
        pt['fg_colour'], pt['fg_alpha']


    local angle_0 = sa * (2 * math.pi / 360) - math.pi / 2
    local angle_f = ea * (2 * math.pi / 360) - math.pi / 2
    local t_arc = t * (angle_f - angle_0)


    -- Draw background ring
    
    cairo_arc(cr, xc, yc, ring_r, angle_0, angle_f)
    cairo_set_source_rgba(cr, rgb_to_r_g_b(bgc, bga))
    cairo_set_line_width(cr, ring_w)
    cairo_stroke(cr)
    
    -- Draw indicator ring
    
    cairo_arc(cr, xc, yc, ring_r, angle_0, angle_0 + t_arc)
    
    -- New if statement holds colour change logic
    
    if fgc == 'rainbow_rgb' then
        local r, g, b = 0
        local sixth = t * 6
        if sixth < 1 then
            r, g, b = 1, sixth, 0
        elseif sixth < 2 then
            r, g, b = 2 - sixth, 1, 0
        elseif sixth < 3 then
            r, g, b = 0, 1, sixth - 2
        elseif sixth < 4 then
            r, g, b = 0, 4 - sixth, 1
        elseif sixth < 5 then
            r, g, b = sixth - 4, 0, 1
        elseif sixth < 6 then
            r, g, b = 1, 0, 6 - sixth
        end
        cairo_set_source_rgba(cr, r, g, b, fga)
    elseif fgc == 'rainbow_bgr' then
        local r, g, b = 0
        local sixth = t * 6
        if sixth < 1 then
            r, g, b = 0, sixth, 1
        elseif sixth < 2 then
            r, g, b = 0, 1, 2 - sixth
        elseif sixth < 3 then
            r, g, b = sixth - 2, 1, 0
        elseif sixth < 4 then
            r, g, b = 1, 4 - sixth, 0
        elseif sixth < 5 then
            r, g, b = 1, 0, sixth - 4
        elseif sixth < 6 then
            r, g, b = 6 - sixth, 0, 1
        end
        cairo_set_source_rgba(cr, r, g, b, fga)
    elseif fgc == 'traffic' then
        local r, g, b = 0
        local third = t * 3
        if third < 1 then
            r, g, b = 0, 1, 0
        elseif third < 2 then
            r, g, b = third - 1, 1, 0
        elseif third < 3 then
            r, g, b = 1, 3 - third, 0
        end
        cairo_set_source_rgba(cr, r, g, b, fga)
    elseif fgc == 'traffic_rev' then
        local r, g, b = 0
        local half = t * 2
        if half < 1 then
            r, g, b = 1, half, 0
        elseif half < 2 then
            r, g, b = 2 - half, 1, 0
        end
        cairo_set_source_rgba(cr, r, g, b, fga)
    else
        -- Original set_source code
        
        cairo_set_source_rgba(cr, rgb_to_r_g_b(fgc, fga))
    end
    
    cairo_stroke(cr)
end


function conky_ring_stats()
    local function setup_rings(cr, pt)
        local str = ''
        local value = 0
        
        -- New if statement holds millisecond precision clock logic
        
        if pt['name'] == 'time' then
            if pt['arg'] == '%y' then
                -- Year of the century
                local doy = conky_parse('${time %j}')
                local yr  = conky_parse('${time %y}')
                value = yr + (doy / 365)
            elseif pt['arg'] == '%j' then
                -- Day of the year
                local hrs = conky_parse('${time %H}')
                local doy = conky_parse('${time %j}')
                value = (doy - 1) + (hrs / 24)
            elseif pt['arg'] == '%d' then
                -- Day of the month
                local mon = conky_parse('${time %m}')
                if mon == 1 or mon == 3 or mon == 5 or mon == 7 or mon == 8
                    or mon == 10 or mon == 12 then
                        pt['max'] = 31
                elseif mon == 2 then
                    pt['max'] = 28
                else
                    pt['max'] = 30
                end
                local hrs = conky_parse('${time %H}')
                local dom = conky_parse('${time %d}')
                value = (dom - 1) + (hrs / 24)
            elseif pt['arg'] == '%u' then
                -- Day of the week
                local mins = conky_parse('${time %M}')
                local hrs  = conky_parse('${time %H}')
                local dow  = conky_parse('${time %u}')
                value = (dow - 1) + (hrs / 24) + (mins / 1440)
            elseif pt['arg'] == '%I' then
                -- Hours
                local secs = conky_parse('${time %S}')
                local mins = conky_parse('${time %M}')
                local hrs  = conky_parse('${time %I}')
                value = (hrs % 12) + (mins / 60) + (secs / 3600)
            elseif pt['arg'] == '%H' then
                -- 24 hours
                local secs = conky_parse('${time %S}')
                local mins = conky_parse('${time %M}')
                local hrs  = conky_parse('${time %H}')
                value = hrs + (mins / 60) + (secs / 3600)
            elseif pt['arg'] == '%M' then
                -- Minutes
                local temp_secs = os.time()
                local mils = socket.gettime() - temp_secs
                local secs = conky_parse('${time %S}') + mils
                local mins = conky_parse('${time %M}')
                value = mins + (secs / 60)
            elseif pt['arg'] == '%S' then
                -- Seconds
                local temp_secs = os.time()
                local mils = socket.gettime() - temp_secs
                local secs = conky_parse('${time %S}') + mils
                value = secs
            else
                -- Original conky_parse code replicated here to prevent
                -- breakages in times which don't use any of the above variables
                
                str = string.format('${%s %s}', pt['name'], pt['arg'])
                str = conky_parse(str)
                value = tonumber(str)
            end
        else
            -- Original conky_parse code
            
            str = string.format('${%s %s}', pt['name'], pt['arg'])
            str = conky_parse(str)
            value = tonumber(str)
        end
        
        pct = value / pt['max']
        
        draw_ring(cr, pct, pt)
    end


    if conky_window == nil then return end
    
    local cs = cairo_xlib_surface_create(conky_window.display,
        conky_window.drawable, conky_window.visual,
        conky_window.width, conky_window.height)
    local cr = cairo_create(cs) 
    
    local updates = conky_parse('${updates}')
    update_num = tonumber(updates)
    
    if update_num > 5 then
        for i in pairs(settings_table) do
            setup_rings(cr, settings_table[i])
        end
    end
end

```

but it is to difficult for me, to understand it and write own code. i think i need something like: if bat1 == 100% then color else if....
can somebody help me with this please

---

### Post by again? on 2019-07-25
I have attached an archive containing a lua script.  
This lua script can draw bar graphs, ring meters and ellipse meters.

It is slightly different than other lua scripts in that it has a separate config file.
Extract the attachment and move the lua-draw folder to where you keep your conky stuff.
Most people use a ~/.conky directory but can be wherever you like.

To run the included sample conky config you need to change directory(cd) to where 
you placed the lua-draw folder and then run conky using the conkyrc config.
eg (assuming you placed the lua-draw folder in ~/.conky)
```
cd ~/.conky/lua-draw && conky -c conkyrc
```
[ATTACH=CONFIG]283670[/ATTACH]

Open both the conky_draw_config.lua file and the conkyrc file.
Experiment with the **conky_draw_config.lua** to see what the changes do.
Do not edit **conky_draw.lua**.

For what you want, look at the "[COLOR="#696969"]-- ring graph memperc[/COLOR]" section
where you will find configs to define a critical threshold and bar color...
```
critical_threshold = 85,
bar_color_critical = 0x[COLOR="#FF0000"]FF2B36[/COLOR],
```
Use gpick to pick [COLOR="#FF0000"]your color[/COLOR].
After editing conky_draw_config.lua and saving, also save conkyrc whereas the conky window should reload showing changes.

See [https://github.com/fisadev/conky-draw/](https://github.com/fisadev/conky-draw/) for more info.

---

### Post by koper97 on 2019-07-25
Thank you!! tonight i gonna to play with these scripts :)

---

