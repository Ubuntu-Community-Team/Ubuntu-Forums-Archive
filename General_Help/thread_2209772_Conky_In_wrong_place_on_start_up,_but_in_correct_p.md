---
title: "Conky In wrong place on start up, but in correct place when saving conkyrc"
date: 2014-03-07
forum: General Help
---

### Post by vX6 on 2014-03-07
I am running the Black Lab Linux latest version with updates and extensions, I use the xubuntu shell on log in.
I am a newbie so sorry if this is an obvious problem but google couldn't solve it for me.

I have created a .conky folder in my /home/vx/ directory, and a within it are .conkyrc_clock, conkyrc_HUD, conky_HUD.lua, lua_widgets.lua. 

I also created /home/vx/bin/ . It contains a file called conky_start, it reads:

```
#!/bin/bash
conky -c ~/.conky/.conkyrc_clock &
conky -c ~/.conky/conkyrc_HUD
```

I created an Application Autostart, using the built in Session and Startup app within settings. I clicked add, typed Conky Start in the name, then chose the file conky_start within my /home/vx/bin directory for the command with the browse button.

When I first start up my conkies appear like so:
[http://img.photobucket.com/albums/v311/vxmew/Screenshot-03072014-031302AM.png](http://img.photobucket.com/albums/v311/vxmew/Screenshot-03072014-031302AM.png)

If I open .conkyrc_clock and conkyrc_HUD change nothing and resave they appear like so:
[http://img.photobucket.com/albums/v311/vxmew/Screenshot-03072014-031440AM.png](http://img.photobucket.com/albums/v311/vxmew/Screenshot-03072014-031440AM.png)


I can post my config files if necessary, thanks for the help I've tried all I could to fix this with different terminal codes like sleep and even killall within the conky_start.

---

### Post by ajgreeny on 2014-03-07
Try using the -p (for pause) option in your conky startup commands in the shell script, ie,
```
#!/bin/bash
conky -p 10 -c ~/.conky/.conkyrc_clock &
conky -p 10 -c ~/.conky/conkyrc_HUD
```which will simply delay the start of conky by 10 seconds and may allow the startup as you want it.  In my experience conky needs the desktop up and fully running before it will start as you wish.

---

### Post by Habitual on 2014-03-07
Try adding the -p switch(es) to each of 
```
#!/bin/bash
conky -c [COLOR=#ff0000]**-p 15**[/COLOR] ~/.conky/.conkyrc_clock &
conky -c [COLOR=#ff0000]**-p 15 **[/COLOR]~/.conky/conkyrc_HUD
```
and start the script. Any change other than a 15 second delay?

Failing that. post clock and HUD RCs.

Thank you,

---

### Post by vX6 on 2014-03-07
[**[COLOR=#000000]ajgreeny[/COLOR]**]("http://ubuntuforums.org/member.php?u=27747")  your code "worked" as in it delayed them starting but they still  appeared in the wrong place when the timer was up even after changing it  to 40. [**[COLOR=#000000]Habitual[/COLOR]**]("http://ubuntuforums.org/member.php?u=504341") your code acted odd, it made a classic black and white conky at first and then no conkies were on the screen.

.conkyrc_clock's code
```
background no
update_interval 1

override_utf8_locale yes

double_buffer yes
no_buffers yes

text_buffer_size 2048
imlib_cache_size 0


own_window yes
own_window_transparent yes
own_window_argb_visual yes
own_window_type normal
#own_window_class conky-semi
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

border_inner_margin 0
border_outer_margin 0

minimum_size 600 600   #width height


alignment tl
gap_x -60
gap_y -30

draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders no

use_xft yes
xftfont pftempestafivecondensed:size=6
xftalpha 0.5

uppercase no

default_color FFFFFF

lua_load ~/.conky/lua_widgets.lua
lua_draw_hook_pre start_widgets

TEXT
${color FFFFFF}


```

.conkyrc_clock points to lua_widgets.lua
```
-- 2014-02-24 by eXpander


---------------- USER CONFIGURATION ----------------
-- Set your number of physical cores to show temperatures of each.
number_of_physical_CPU_cores = 0      

-- Your GPU model. Only NVIDIA cards with NVIDIA proprietary drivers are official supported. Issue nvidia-smi to find your model!                
graphic_card_model = "Type Your Model Here"

-- Show graphic card temperature? (Yes/No)
enable_graphic_card_temperature_sensor= "No" 

-- Colors
HTML_colors = "#043a39"
HTML_colors_current = "#14e7e5"
transparency = 1 -- From 0 to 1

-- Scaled relative position from middle. Positive x and y means left and up, negative x and y means right and down.
x_rel_pos = 0
y_rel_pos = 0

require 'cairo'

function hex2rgb(hex)
  hex = hex:gsub("#","")
  return tonumber("0x"..hex:sub(1,2)), tonumber("0x"..hex:sub(3,4)), tonumber("0x"..hex:sub(5,6))
end

r,g,b = hex2rgb(HTML_colors)
r_c,g_c,b_c = hex2rgb(HTML_colors_current)

r = r/255
g = g/255
b = b/255

r_c = r_c/255
g_c = g_c/255
b_c = b_c/255

if enable_graphic_card_temperature_sensor == "Yes" then
  number_of_physical_CPU_cores = number_of_physical_CPU_cores + 1
end


function create_circle_hdd(cr,w,h,elements,distance_between_blocks, radius, line_width, current)
  cairo_set_line_width(cr, line_width)
  cairo_set_source_rgba(cr, r,g,b,transparency)
  cairo_new_path(cr)
  local number_of_arcs = (360 - (elements*distance_between_blocks)) / elements
  local start_angel = 270
  local percent_per_element = 100.0 / elements
  local charged_elements = current / percent_per_element
  
  for i=1, elements do
    if charged_elements >= i then
      cairo_set_source_rgba(cr, r_c,g_c,b_c,transparency)
    end
    cairo_arc(cr, w,h,radius,start_angel*math.pi/180,(start_angel+number_of_arcs)*math.pi/180)
    cairo_stroke(cr)
    start_angel = start_angel+number_of_arcs+distance_between_blocks
    cairo_set_source_rgba(cr, r,g,b,transparency)
  end   
end
function create_circle(cr,w,h, elements, distance_between_blocks, two_number_degree, radius, line_width, operator, radius_shift_for_text, current, days, shift_days_distance)
  cairo_set_line_width(cr, line_width)
  cairo_set_source_rgba(cr, r,g,b,transparency)
  cairo_new_path(cr)
  local number_of_arcs = (360 - (elements*distance_between_blocks)) / elements
  local start_angel = 270
  
  for i=1, elements do
    if i == current then
      cairo_set_source_rgba(cr, r_c,g_c,b_c,transparency)
    end
    cairo_arc(cr, w/2, h/2, radius, start_angel*math.pi/180, (start_angel+number_of_arcs)*math.pi/180)
    cairo_stroke(cr)
    start_angel = start_angel+number_of_arcs+distance_between_blocks
    cairo_set_source_rgba(cr, r,g,b,transparency)
  end 
  
  start_angel = 270
  cairo_set_operator(cr, operator)
  
  for i=1, elements do
    if i == current then
      cairo_set_source_rgba(cr, r_c,g_c,b_c,transparency)
    end
    if string.len(tostring(i)) == 2 and days == "" then
      cairo_move_to(cr,w/2+((radius+radius_shift_for_text)*math.cos((start_angel+(((number_of_arcs-two_number_degree)/2)))*(math.pi/180.0))),h/2+((radius+radius_shift_for_text)*math.sin((start_angel+(((number_of_arcs-two_number_degree)/2)))*(math.pi/180.0))))
      cairo_rotate(cr, (((number_of_arcs-two_number_degree)/2)+(number_of_arcs+distance_between_blocks)*(i-1))*math.pi/180.0)
      cairo_show_text(cr,tostring(i))
      cairo_rotate(cr,-(((number_of_arcs-two_number_degree)/2)+(number_of_arcs+distance_between_blocks)*(i-1))*math.pi/180.0)
    elseif days ~= "" then
      cairo_move_to(cr,w/2+((radius+radius_shift_for_text)*math.cos((start_angel+((math.abs((number_of_arcs-shift_days_distance))/2)))*(math.pi/180.0))),h/2+((radius+radius_shift_for_text)*math.sin((start_angel+((math.abs((number_of_arcs-shift_days_distance))/2)))*(math.pi/180.0))))
      cairo_rotate(cr, ((math.abs((number_of_arcs-shift_days_distance))/2)+(number_of_arcs+distance_between_blocks)*(i-1)+4)*math.pi/180.0)
      cairo_show_text(cr,days[i])
      cairo_rotate(cr,-((math.abs((number_of_arcs-shift_days_distance))/2)+(number_of_arcs+distance_between_blocks)*(i-1)+4)*math.pi/180.0)      
    elseif string.len(tostring(i)) == 1 and days == "" then
      cairo_move_to(cr,w/2+((radius+radius_shift_for_text)*math.cos((start_angel+(((number_of_arcs-distance_between_blocks)/2)))*(math.pi/180.0))),h/2+((radius+radius_shift_for_text)*math.sin((start_angel+(((number_of_arcs-distance_between_blocks)/2)))*(math.pi/180.0))))
      cairo_rotate(cr, (((number_of_arcs-distance_between_blocks)/2)+(number_of_arcs+distance_between_blocks)*(i-1))*math.pi/180.0)
      cairo_show_text(cr,tostring(i))
      cairo_rotate(cr,-(((number_of_arcs-distance_between_blocks)/2)+(number_of_arcs+distance_between_blocks)*(i-1))*math.pi/180.0)
    end
    
    start_angel = start_angel+number_of_arcs+distance_between_blocks 
    cairo_set_source_rgba(cr, r,g,b,transparency)
  end
  cairo_close_path(cr)
  cairo_set_operator(cr, CAIRO_OPERATOR_OVER)
end


function vertical_bars(cr,w,h,x,y,conky_value)
    cairo_set_source_rgba(cr, r,g,b,transparency)
    local percent_per_block = 70 / 10
    local number_of_filled_blocks = math.floor((conky_value/percent_per_block)+0.5)
    
    for i=1,10 do
      if number_of_filled_blocks >= i then
    cairo_set_source_rgba(cr, r_c,g_c,b_c,transparency)
      end
      --cairo_rectangle(cr, w/2-x, h/2+y-i*5,15,3)
      cairo_rectangle(cr, w, h/2+y-i*5,15,3)
      cairo_fill(cr)
      cairo_set_source_rgba(cr, r,g,b,transparency)
    end
  
end

function draw_circles(cr, x_start,y_start,radius, angle_1, angle_2, free_perc, angle_step)
     cairo_select_font_face (cr, "Dejavu Sans Condensed", CAIRO_FONT_SLANT_NORMAL, CAIRO_FONT_WEIGHT_NORMAL);
     local number_of_circles = 360 / angle_step
     local angle_start = 90
     cairo_set_line_width(cr, 1)
     local percent_per_circle = 100.0 / number_of_circles
     local number_of_nonfree_circles = math.floor(((100.0 - tonumber(free_perc)) / percent_per_circle)+0.5)
     cairo_set_source_rgba(cr, r,g,b,transparency)
     
    for i=1,number_of_circles do
      cairo_arc(cr,x_start+(radius*math.cos(angle_start*(math.pi/180.0))),y_start-(radius+5)+radius-(radius*math.sin(angle_start*(math.pi/180.0))),2,angle1,angle2)
      if i <= number_of_nonfree_circles then
        cairo_set_source_rgba(cr, r_c,g_c,b_c,transparency)
        cairo_fill(cr)
      else
        cairo_set_source_rgba(cr, r,g,b,transparency)
        cairo_fill(cr)
      end
      angle_start = angle_start - angle_step
    end
    cairo_set_source_rgba(cr, r,g,b,transparency)
    
end

function draw_function(cr)
  local w,h=conky_window.width,conky_window.height    
  cairo_set_line_width(cr, 3)
  cairo_set_font_size(cr,12)
  cairo_select_font_face (cr, "Dejavu Sans Condensed", CAIRO_FONT_SLANT_NORMAL, CAIRO_FONT_WEIGHT_NORMAL);
  
-- Number of weeks per year --- 
  create_circle(cr,w-x_rel_pos,h-y_rel_pos, 52.0, 2, 3.5, 225, 3, CAIRO_OPERATOR_OVER, 4, tonumber(conky_parse('${exec date +%V}')), '')
  
-- Number of days in a month ---
  create_circle(cr,w-x_rel_pos,h-y_rel_pos, conky_parse('${exec cal |egrep -v [a-z] |wc -w}'), 2, 3.5, 200, 13,CAIRO_OPERATOR_CLEAR, -4.5,tonumber(conky_parse('${exec date +%d}')), '')
  
--- Days ---
-- function create_circle(cr,w,h, elements, distance_between_blocks, two_number_degree, radius, line_width, operator, radius_shift_for_text, current, days, shift_days_distance)
 
  local days = {"Mon", "Tue", "Wed","Thu", "Fri", "Sat", "Sun"}
  create_circle(cr,w-x_rel_pos,h-y_rel_pos, 7, 2, 3.5, 150, 13, CAIRO_OPERATOR_CLEAR, -4, tonumber(conky_parse('${exec date +%u}')), days, 8.5)
  
--- Month ---
  
  local month = {"Jan", "Feb", "Mar", "Apr", "May", "Jun", "Jul", "Aug", "Sep", "Oct", "Nov", "Dec"}
  create_circle(cr,w-x_rel_pos,h-y_rel_pos, 12, 2, 3.5, 175, 13, CAIRO_OPERATOR_CLEAR, -4, tonumber(conky_parse('${exec date +%m}')), month, 5.5)
  
  
--- Clock ---
  cairo_set_font_size(cr,42)
  cairo_move_to(cr, (w-x_rel_pos)/2-54,(h-y_rel_pos)/2)
  cairo_show_text(cr,conky_parse('${exec date +%H}') .. ":" .. conky_parse('${exec date +%M}'))
  cairo_set_font_size(cr,12)
  cairo_move_to(cr, (w-x_rel_pos)/2-24,(h-y_rel_pos)/2+14)
  cairo_show_text(cr, "")
  

--- Free space ---
  cairo_set_operator(cr, CAIRO_OPERATOR_OVER)
  angle1 = 0.0  * (math.pi/180.0);  
  angle2 = 360.0 * (math.pi/180.0);
  
  create_circle_hdd(cr,(w-x_rel_pos)/2-60,(h-y_rel_pos)/2-80,20,3, 20, 3, 100-tonumber(conky_parse("${fs_free_perc /}")))
  create_circle_hdd(cr,(w-x_rel_pos)/2+60,(h-y_rel_pos)/2-80,20,3, 20, 3,100-tonumber(conky_parse("${fs_free_perc /home}")))
  

  cairo_arc(cr,(w-x_rel_pos)/2-60,(h-y_rel_pos)/2-80,14,0,2*math.pi)
  cairo_fill(cr)
  cairo_arc(cr,(w-x_rel_pos)/2+60,(h-y_rel_pos)/2-80,14,0,2*math.pi)
  cairo_fill(cr)
  
  cairo_set_operator(cr, CAIRO_OPERATOR_CLEAR)
  cairo_move_to(cr, (w-x_rel_pos)/2-64, (h-y_rel_pos)/2-75)
  cairo_show_text(cr,"R")
  cairo_move_to(cr, (w-x_rel_pos)/2+56, (h-y_rel_pos)/2-75)
  cairo_show_text(cr,"H")
  cairo_set_operator(cr, CAIRO_OPERATOR_OVER)
  
--- Temperatures ---

  cairo_move_to(cr,(w-x_rel_pos)/2-50,(h-y_rel_pos)/2+100)
  cairo_set_font_size(cr,12)

  for i=1, number_of_physical_CPU_cores do
    x = (w-x_rel_pos)/2-((15*number_of_physical_CPU_cores)+15*(number_of_physical_CPU_cores-1))/2+30*(i-1)
    
    if enable_graphic_card_temperature_sensor == "Yes" and i == number_of_physical_CPU_cores then
      str= tonumber(conky_parse("${exec nvidia-smi | grep '" .. graphic_card_model .. "' -A 1 | tail -n 1 | awk '{print $3}' | cut -b1,2}"))
      vertical_bars(cr,x,h-y_rel_pos,64,75,str)
      cairo_arc(cr,x+8,(h-y_rel_pos)/2+90,7,0,2*math.pi)
      cairo_fill(cr)
      cairo_set_operator(cr, CAIRO_OPERATOR_CLEAR)
      cairo_move_to(cr,x+3,(h-y_rel_pos)/2+94)
      cairo_show_text(cr,"G")
      cairo_set_operator(cr, CAIRO_OPERATOR_OVER)
    else
      str = "${exec sensors|grep 'Core " .. tostring(i-1) .. ":'|awk '{print $3}'| cut -b2,3,4,5}"
      vertical_bars(cr,x,h-y_rel_pos,64,75,tonumber(conky_parse(str)))
      cairo_arc(cr,x+8,(h-y_rel_pos)/2+90,7,0,2*math.pi)
      cairo_fill(cr)
      cairo_set_operator(cr, CAIRO_OPERATOR_CLEAR)
      cairo_move_to(cr,x+5,(h-y_rel_pos)/2+94)
      cairo_show_text(cr,tostring(i-1))
      cairo_set_operator(cr, CAIRO_OPERATOR_OVER)
    end
    
  end
end

function conky_start_widgets()
    local function draw_conky_function(cr)
        local str=''
        local value=0        
        draw_function(cr)
    end
    
    -- Check that Conky has been running for at least 5s

    if conky_window==nil then return end
    local cs=cairo_xlib_surface_create(conky_window.display,conky_window.drawable,conky_window.visual, conky_window.width,conky_window.height)
    
    local cr=cairo_create(cs)    
    
    local updates=conky_parse('${updates}')
    update_num=tonumber(updates)
    
    if update_num>5 then
        draw_conky_function(cr)
    end
    cairo_surface_destroy(cs)
    cairo_destroy(cr)
end


```

conkyrc_HUD's code
```
#==============================================================================
#                            conkyrc_HUD
#
#  author  : SLK
#  version : v2011011601
#  license : Distributed under the terms of GNU GPL version 2 or later
#
#==============================================================================

background no
update_interval 1

override_utf8_locale yes

cpu_avg_samples 2
net_avg_samples 2
temperature_unit celsius

double_buffer yes
no_buffers yes

text_buffer_size 2048
imlib_cache_size 0



own_window yes
own_window_transparent yes
own_window_argb_visual yes
own_window_type normal
#own_window_class conky-semi
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

border_inner_margin 0
border_outer_margin 0

minimum_size 600 600   #width height


alignment tl
gap_x  780
gap_y  440

draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no

use_xft yes
xftfont pftempestafivecondensed:size=6
xftalpha 0.5

use_xft yes
xftfont caviar dreams:size=8
xftalpha 0.5

uppercase no

default_color FFFFFF
color1 00FFBB

lua_load ~/.conky/conky_HUD.lua
lua_draw_hook_post main

TEXT
${color1}${font ubuntu:size=10}${time %H:%M:%S}
${voffset 25}
${goto 100}${font Ubuntu:size=8,weight:bold}${color}DISKS
${goto 110}${font Ubuntu:size=7,weight:normal}${color1}size /
${goto 105}${font Ubuntu:size=9,weight:normal}${color1}${offset 5}${voffset -4}${fs_size /}
${goto 105}${font Ubuntu:size=7,weight:normal}${color1}size /home
${goto 105}${font Ubuntu:size=9,weight:normal}${color1}${offset 5}${voffset -4}${fs_size /home}

${voffset -70}
${goto 30}${font Ubuntu:size=8,weight:bold}${color}MEM

${voffset -25}
${goto 180}${font Ubuntu:size=8,weight:bold}${color}CPU


```

conkyrc_HUD points to conky_HUD.lua
```
--==============================================================================
--                              conky_HUD.lua
--
--  author  : SLK
--  version : v2011062101
--  license : Distributed under the terms of GNU GPL version 2 or later
--
--==============================================================================

require 'cairo'

--------------------------------------------------------------------------------
--                                                                    gauge DATA
gauge = {
{
    name='cpu',                    arg='cpu0',                  max_value=100,
    x=180,                         y=120,
    graph_radius=50,
    graph_thickness=5,
    graph_start_angle=0,
    graph_unit_angle=0.9,          graph_unit_thickness=0.9,
    graph_bg_colour=0x14e7e5,      graph_bg_alpha=1,
    graph_fg_colour=0x14e7e5,      graph_fg_alpha=1,
    hand_fg_colour=0x14e7e5,       hand_fg_alpha=1,
    txt_radius=40,
    txt_weight=1,                  txt_size=10.0,
    txt_fg_colour=0x14e7e5,        txt_fg_alpha=1,
    graduation_radius=30,
    graduation_thickness=0,        graduation_mark_thickness=1,
    graduation_unit_angle=27,
    graduation_fg_colour=0x14e7e5, graduation_fg_alpha=1,
    caption='',
    caption_weight=1,              caption_size=8.0,
    caption_fg_colour=0xFFFFFF,    caption_fg_alpha=1,
},
{
    name='cpu',                    arg='cpu1',                  max_value=100,
    x=180,                         y=120,
    graph_radius=60,
    graph_thickness=5,
    graph_start_angle=0,
    graph_unit_angle=0.9,          graph_unit_thickness=0.9,
    graph_bg_colour=0x14e7e5,      graph_bg_alpha=1,
    graph_fg_colour=0x14e7e5,      graph_fg_alpha=1,
    hand_fg_colour=0x14e7e5,       hand_fg_alpha=1,
    txt_radius=70,
    txt_weight=1,                  txt_size=10.0,
    txt_fg_colour=0x14e7e5,        txt_fg_alpha=1,
    graduation_radius=55,
    graduation_thickness=5,        graduation_mark_thickness=2,
    graduation_unit_angle=27,
    graduation_fg_colour=0x14e7e5, graduation_fg_alpha=1,
    caption='',
    caption_weight=1,              caption_size=1,
    caption_fg_colour=0xFFFFFF,    caption_fg_alpha=1,
},
{
    name='memperc',                arg='',                      max_value=100,
    x=40,                          y=85,
    graph_radius=34,
    graph_thickness=5,
    graph_start_angle=180,
    graph_unit_angle=2,            graph_unit_thickness=2,
    graph_bg_colour=0x14e7e5,      graph_bg_alpha=1,
    graph_fg_colour=0x14e7e5,      graph_fg_alpha=1,
    hand_fg_colour=0x14e7e5,       hand_fg_alpha=1,
    txt_radius=20,
    txt_weight=1,                  txt_size=10.0,
    txt_fg_colour=0x14e7e5,        txt_fg_alpha=1,
    graduation_radius=24,
    graduation_thickness=6,        graduation_mark_thickness=2,
    graduation_unit_angle=10,
    graduation_fg_colour=0x14e7e5, graduation_fg_alpha=1,
    caption='',
    caption_weight=1,              caption_size=10.0,
    caption_fg_colour=0xFFFFFF,    caption_fg_alpha=1,
},
{
    name='fs_used_perc',           arg='/',                     max_value=100,
    x=120,                         y=70,
    graph_radius=40,
    graph_thickness=4,
    graph_start_angle=210,
    graph_unit_angle=2,            graph_unit_thickness=2,
    graph_bg_colour=0x14e7e5,      graph_bg_alpha=1,
    graph_fg_colour=0x14e7e5,      graph_fg_alpha=1,
    hand_fg_colour=0x14e7e5,       hand_fg_alpha=1,
    txt_radius=32,
    txt_weight=1,                  txt_size=10.0,
    txt_fg_colour=0x14e7e5,        txt_fg_alpha=1,
    graduation_radius=46,
    graduation_thickness=0,        graduation_mark_thickness=2,
    graduation_unit_angle=20,
    graduation_fg_colour=0x14e7e5, graduation_fg_alpha=1,
    caption='',
    caption_weight=1,              caption_size=8.0,
    caption_fg_colour=0xFFFFFF,    caption_fg_alpha=1,
},
{
    name='fs_used_perc',           arg='/home/',                max_value=100,
    x=120,                         y=70,
    graph_radius=50,
    graph_thickness=8,
    graph_start_angle=210,
    graph_unit_angle=2,            graph_unit_thickness=2,
    graph_bg_colour=0x14e7e5,      graph_bg_alpha=1,
    graph_fg_colour=0x14e7e5,      graph_fg_alpha=1,
    hand_fg_colour=0x14e7e5,       hand_fg_alpha=1,
    txt_radius=60,
    txt_weight=1,                  txt_size=10.0,
    txt_fg_colour=0x14e7e5,        txt_fg_alpha=1,
    graduation_radius=58,
    graduation_thickness=4,        graduation_mark_thickness=2,
    graduation_unit_angle=20,
    graduation_fg_colour=0x14e7e5, graduation_fg_alpha=1,
    caption='',
    caption_weight=1,              caption_size=8.0,
    caption_fg_colour=0xFFFFFF,    caption_fg_alpha=1,
},
}

-------------------------------------------------------------------------------
--                                                                 rgb_to_r_g_b
-- converts color in hexa to decimal
--
function rgb_to_r_g_b(colour, alpha)
    return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
end

-------------------------------------------------------------------------------
--                                                            angle_to_position
-- convert degree to rad and rotate (0 degree is top/north)
--
function angle_to_position(start_angle, current_angle)
    local pos = current_angle + start_angle
    return ( ( pos * (2 * math.pi / 360) ) - (math.pi / 2) )
end

-------------------------------------------------------------------------------
--                                                              draw_gauge_ring
-- displays gauges
--
function draw_gauge_ring(display, data, value)
    local max_value = data['max_value']
    local x, y = data['x'], data['y']
    local graph_radius = data['graph_radius']
    local graph_thickness, graph_unit_thickness = data['graph_thickness'], data['graph_unit_thickness']
    local graph_start_angle = data['graph_start_angle']
    local graph_unit_angle = data['graph_unit_angle']
    local graph_bg_colour, graph_bg_alpha = data['graph_bg_colour'], data['graph_bg_alpha']
    local graph_fg_colour, graph_fg_alpha = data['graph_fg_colour'], data['graph_fg_alpha']
    local hand_fg_colour, hand_fg_alpha = data['hand_fg_colour'], data['hand_fg_alpha']
    local graph_end_angle = (max_value * graph_unit_angle) % 360

    -- background ring
    cairo_arc(display, x, y, graph_radius, angle_to_position(graph_start_angle, 0), angle_to_position(graph_start_angle, graph_end_angle))
    cairo_set_source_rgba(display, rgb_to_r_g_b(graph_bg_colour, graph_bg_alpha))
    cairo_set_line_width(display, graph_thickness)
    cairo_stroke(display)

    -- arc of value
    local val = value % (max_value + 1)
    local start_arc = 0
    local stop_arc = 0
    local i = 1
    while i <= val do
        start_arc = (graph_unit_angle * i) - graph_unit_thickness
        stop_arc = (graph_unit_angle * i)
        cairo_arc(display, x, y, graph_radius, angle_to_position(graph_start_angle, start_arc), angle_to_position(graph_start_angle, stop_arc))
        cairo_set_source_rgba(display, rgb_to_r_g_b(graph_fg_colour, graph_fg_alpha))
        cairo_stroke(display)
        i = i + 1
    end
    local angle = start_arc

    -- hand
    start_arc = (graph_unit_angle * val) - (graph_unit_thickness * 2)
    stop_arc = (graph_unit_angle * val)
    cairo_arc(display, x, y, graph_radius, angle_to_position(graph_start_angle, start_arc), angle_to_position(graph_start_angle, stop_arc))
    cairo_set_source_rgba(display, rgb_to_r_g_b(hand_fg_colour, hand_fg_alpha))
    cairo_stroke(display)

    -- graduations marks
    local graduation_radius = data['graduation_radius']
    local graduation_thickness, graduation_mark_thickness = data['graduation_thickness'], data['graduation_mark_thickness']
    local graduation_unit_angle = data['graduation_unit_angle']
    local graduation_fg_colour, graduation_fg_alpha = data['graduation_fg_colour'], data['graduation_fg_alpha']
    if graduation_radius > 0 and graduation_thickness > 0 and graduation_unit_angle > 0 then
        local nb_graduation = graph_end_angle / graduation_unit_angle
        local i = 0
        while i < nb_graduation do
            cairo_set_line_width(display, graduation_thickness)
            start_arc = (graduation_unit_angle * i) - (graduation_mark_thickness / 2)
            stop_arc = (graduation_unit_angle * i) + (graduation_mark_thickness / 2)
            cairo_arc(display, x, y, graduation_radius, angle_to_position(graph_start_angle, start_arc), angle_to_position(graph_start_angle, stop_arc))
            cairo_set_source_rgba(display,rgb_to_r_g_b(graduation_fg_colour,graduation_fg_alpha))
            cairo_stroke(display)
            cairo_set_line_width(display, graph_thickness)
            i = i + 1
        end
    end

    -- text
    local txt_radius = data['txt_radius']
    local txt_weight, txt_size = data['txt_weight'], data['txt_size']
    local txt_fg_colour, txt_fg_alpha = data['txt_fg_colour'], data['txt_fg_alpha']
    local movex = txt_radius * math.cos(angle_to_position(graph_start_angle, angle))
    local movey = txt_radius * math.sin(angle_to_position(graph_start_angle, angle))
    cairo_select_font_face (display, "ubuntu", CAIRO_FONT_SLANT_NORMAL, txt_weight)
    cairo_set_font_size (display, txt_size)
    cairo_set_source_rgba (display, rgb_to_r_g_b(txt_fg_colour, txt_fg_alpha))
    cairo_move_to (display, x + movex - (txt_size / 2), y + movey + 3)
    cairo_show_text (display, value)
    cairo_stroke (display)

    -- caption
    local caption = data['caption']
    local caption_weight, caption_size = data['caption_weight'], data['caption_size']
    local caption_fg_colour, caption_fg_alpha = data['caption_fg_colour'], data['caption_fg_alpha']
    local tox = graph_radius * (math.cos((graph_start_angle * 2 * math.pi / 360)-(math.pi/2)))
    local toy = graph_radius * (math.sin((graph_start_angle * 2 * math.pi / 360)-(math.pi/2)))
    cairo_select_font_face (display, "ubuntu", CAIRO_FONT_SLANT_NORMAL, caption_weight);
    cairo_set_font_size (display, caption_size)
    cairo_set_source_rgba (display, rgb_to_r_g_b(caption_fg_colour, caption_fg_alpha))
    cairo_move_to (display, x + tox + 5, y + toy + 1)
    -- bad hack but not enough time !
    if graph_start_angle < 105 then
        cairo_move_to (display, x + tox - 30, y + toy + 1)
    end
    cairo_show_text (display, caption)
    cairo_stroke (display)
end

-------------------------------------------------------------------------------
--                                                               go_gauge_rings
-- loads data and displays gauges
--
function go_gauge_rings(display)
    local function load_gauge_rings(display, data)
        local str, value = '', 0
        str = string.format('${%s %s}',data['name'], data['arg'])
        str = conky_parse(str)
        value = tonumber(str)
        draw_gauge_ring(display, data, value)
    end
    
    for i in pairs(gauge) do
        load_gauge_rings(display, gauge[i])
    end
end

-------------------------------------------------------------------------------
--                                                                         MAIN
function conky_main()
    if conky_window == nil then 
        return
    end

    local cs = cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, conky_window.width, conky_window.height)
    local display = cairo_create(cs)
    
    local updates = conky_parse('${updates}')
    update_num = tonumber(updates)
    
    if update_num > 5 then
        go_gauge_rings(display)
    end
    
    cairo_surface_destroy(cs)
    cairo_destroy(display)
end


```

---

### Post by Habitual on 2014-03-07
> **vX6 said:**
> [**[COLOR=#000000]ajgreeny[/COLOR]**]("http://ubuntuforums.org/member.php?u=27747")  your code "worked" as in it delayed them starting but they still  appeared in the wrong place when the timer was up even after changing it  to 40. [**[COLOR=#000000]Habitual[/COLOR]**]("http://ubuntuforums.org/member.php?u=504341") your code acted odd, it made a classic black and white conky at first and then no conkies were on the screen.I guess placement matters? -p before -c :)

I completely missed ajgreeny's post.

Edit these values then:
```

alignment tl
gap_x -60
gap_y -30
``` where did this code come from?

---

### Post by ajgreeny on 2014-03-07
My .conkyrc file contains the following in the config above the TEXT line
```
# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
#alignment bottom_left
alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 25
gap_y 50
```
So play around with these positions and figures till you get something similar for the placements you want for each conky window.

---

### Post by Habitual on 2014-03-07
```
alignment tl
gap_x -60
gap_y -30
``` I'll bet 1 dollar US that the source machine had 2 monitors. Any takers?

---

### Post by ajgreeny on 2014-03-07
> **Habitual said:**
> ```
alignment tl
gap_x -60
gap_y -30
``` I'll bet 1 dollar US that the source machine had 2 monitors. Any takers?
No idea, but I've never seen the **alignment tl** line before, nor any minus figures for the gaps.

---

### Post by vX6 on 2014-03-08
Well interesting results here... "alignment tm" which I assumed meant "top middle" was in the origanol file for the conky clock found here
[http://xfce-look.org/content/show.php/Conky+Calendar+Extra++?content=163754](http://xfce-look.org/content/show.php/Conky+Calendar+Extra++?content=163754)
I changed it to tl to try to make it start in the top left which moves the conky when you do but I am not sure how or why or what it means.

I removed the alignment tl line entirely. This caused the conky (both seporatly) to move so I modified the gap_x and gap _y to place the conky where I wanted it. .conkyrc_clock now reads:

```
background no
update_interval 1

override_utf8_locale yes

double_buffer yes
no_buffers yes

text_buffer_size 2048
imlib_cache_size 0


own_window yes
own_window_transparent yes
own_window_argb_visual yes
own_window_type normal
#own_window_class conky-semi
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

border_inner_margin 0
border_outer_margin 0

minimum_size 600 600   #width height

gap_x -50
gap_y 40

draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders no

use_xft yes
xftfont pftempestafivecondensed:size=6
xftalpha 0.5

uppercase no

default_color FFFFFF

lua_load ~/.conky/lua_widgets.lua
lua_draw_hook_pre start_widgets

TEXT
${color FFFFFF}


```

Notice I still had to use a negitive number to get it correct, I did the same thing with the conkyrc_HUD

Now they stay put on startup so thank you for pointing out you had never seen a code like this!

*ultra newb*):P

---

### Post by ajgreeny on 2014-03-08
This has always been one of the biggest problems of conky in my experience, ie the config file syntax is so complicated that it is a real game of "hit and miss" if things displayed don't work out quite how you want or expect, and trying to find detailed info is like searching a sandy beach for a dropped penny; long and  complicated, and often unsuccessful.

However, I am very happy to have at least given you a clue about where to start looking for an answer in your config files.

---

### Post by Habitual on 2014-03-08
Glad you got it working!

---

### Post by RallyDarkstrike on 2014-05-06
Hi guys - sorry to intrude on this older thread, but I'm having the same issue exactly. Although my alignment isn't that much different from where I want it, my Conky is ALSO in the wrong place on startup. I tried the pause command as well for 90 seconds at start and it's still in the wrong place. As with the OP, when I do a re-save of the .conkyrc file, all goes back to normal. I should note that I am using only one Conky file in my home directory, but am running into the same problem as the OP on two different machines, a netbook running Linux Mint 14 XFCE and a desktop running Xubuntu 14.04 LTS (both running the same Conky theme)

Code is as follows:

```
# Conky settings #
background yes
update_interval 1
double_buffer yes
no_buffers yes
imlib_cache_size 10

# Window specifications #
gap_x 775
gap_y 2
minimum_size 268 620
maximum_width 268
own_window yes
own_window_type normal  # other options are: override/dock/desktop/panel
own_window_transparent yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below
border_inner_margin 0
border_outer_margin 0
#alignment middle_middle
#own_window_argb_visual yes
#own_window_argb_value 0

# Graphics settings #
draw_shades no
default_shade_color AAAAAA
draw_outline no
default_outline_color AAAAAA
draw_borders no
draw_graph_borders no
default_graph_size 26 80
show_graph_scale no
show_graph_range no

# Text settings #
use_xft yes
xftalpha 0
xftfont Droid Sans:size=8
text_buffer_size 256
override_utf8_locale yes

# Useful shortenings #
short_units yes
pad_percents 2
top_name_width 7

# Color scheme #
default_color ffffff
color1 ffffff
color2 ffffff
color3 ffffff
color4 F9F9F9
color5 D80000
color6 DCDCDC
color7 252525
color8 2D2D2D

TEXT
# Various images #
${execi 300 curl -s "http://weather.yahooapis.com/forecastrss?w=4184&u=c" -o ~/.cache/weather.xml}
${image ~/.conky-weather/assets/Numix/God-Mode/top-bg.png -p 20,30 -s 228x61}\
${image ~/.conky-weather/assets/Numix/God-Mode/bottom-bg.png -p 20,473 -s 228x119}\
${image ~/.conky-weather/assets/Numix/God-Mode/border.png -p 20,91 -s 228x86}\
${image ~/.conky-weather/assets/Numix/God-Mode/fav-color.png -p 20,91 -s 228x86}\
${image ~/.conky-weather/assets/Numix/God-Mode/bg-1.png -p 20,177 -s 228x86}\
${image ~/.conky-weather/assets/Numix/God-Mode/bg-2.png -p 20,263 -s 228x105}\
${image ~/.conky-weather/assets/Numix/God-Mode/bg-3.png -p 20,368 -s 228x105}\
${image ~/.conky-weather/assets/Numix/God-Mode/bg-4.png -p 20,478 -s 228x14}\
${image ~/.conky-weather/assets/Numix/God-Mode/separator-v.png -p 95,185 -s 1x76}\
${image ~/.conky-weather/assets/Numix/God-Mode/separator-v.png -p 172,185 -s 1x76}\
${image ~/.conky-weather/assets/Numix/God-Mode/separator-h.png -p 33,369 -s 202x1}\
${image ~/.conky-weather/assets/Numix/God-Mode/separator-h.png -p 33,269 -s 202x1}\
\
# The days of the forecast #
\
${color3}${voffset 172}${alignc 77}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "day=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==1' | tr '[a-z]' '[A-Z]'}${color}
${color3}${voffset -13}${alignc}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "day=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==2' | tr '[a-z]' '[A-Z]'}${color}
${color3}${voffset -13}${alignc -77}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "day=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==3' | tr '[a-z]' '[A-Z]'}${color}
\
# The temperatures of the forecast #
\
${color2}${voffset 51}${alignc 77}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "low=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==1'}°/${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "high=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==1'}°${color}
${color2}${voffset -13}${alignc}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "low=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==2'}°/${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "high=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==2'}°${color}
${color2}${voffset -13}${alignc -77}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "low=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==3'}°/${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "high=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==3'}°${color}
\
# The "conditions" section of the conky #
\
${goto 36}${voffset -172}${font Droid Sans :size=36}${color4}${execi 300 grep "yweather:condition" ~/.cache/weather.xml | grep -o "temp=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"}°${font}${color}
${goto 46}${voffset 14}${font Droid Sans :size=12}${color4}${execi 300 grep "yweather:condition" ~/.cache/weather.xml | grep -o "text=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"}${font}${color}
${color1}${alignr 52}${voffset -73}${execi 300 grep "yweather:atmosphere" ~/.cache/weather.xml | grep -o "pressure=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"} ${execi 300 grep "yweather:units" ~/.cache/weather.xml | grep -o "pressure=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"}
${color1}${alignr 52}${voffset 7}${execi 300 grep "yweather:atmosphere" ~/.cache/weather.xml | grep -o "humidity=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"} %${color}
${color1}${alignr 52}${voffset 7}${execi 300 grep "yweather:wind" ~/.cache/weather.xml | grep -o "speed=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"} ${execi 300 grep "yweather:units" ~/.cache/weather.xml | grep -o "speed=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"}${color}
\
# Clock + calendar #
\
${voffset -117}${font Droid Sans Mono :size=22}${alignc}${color2}${time %l:%M %p}${font}${color}
${voffset 4}${font Droid Sans :size=10}${alignc}${color6}${time %A, %B %_d, %Y}${font}${color}
\
# Cpu, memory, uptime, and load graph #
\
${voffset 294}${goto 40}${color5}CPU:${color}
${voffset 4}${goto 40}${color5}RAM:${color}
${voffset 4}${goto 40}${color5}System Uptime:${color}
${voffset -47}${alignr 39}${color6}${cpu cpu0}%${color}
${voffset 4}${alignr 39}${color6}${mem} / ${memmax}${color}
${voffset 4}${alignr 39}${color6}${uptime_short}${color}
${voffset -47}${alignc}${color2}${cpubar 5,36}${color}
${voffset 4}${alignc}${color2}${membar 5,36}${color}
${voffset 29}${goto 40}${loadgraph 26,190 ffffff D80000 -l}
\
# The processes section #
\
${voffset 26}${goto 40}${color5}${top_mem name 1}${color}
${voffset 4}${goto 40}${color5}${top_mem name 2}${color}
${voffset 4}${goto 40}${color5}${top_mem name 3}${color}
${voffset 4}${goto 40}${color5}${top_mem name 4}${color}
${voffset 4}${goto 40}${color5}${top_mem name 5}${color}
${voffset -81}${alignc}${color2}${top_mem mem 1}%${color}
${voffset 4}${alignc}${color2}${top_mem mem 2}%${color}
${voffset 4}${alignc}${color2}${top_mem mem 3}%${color}
${voffset 4}${alignc}${color2}${top_mem mem 4}%${color}
${voffset 4}${alignc}${color2}${top_mem mem 5}%${color}
${voffset -81}${alignr 39}${color6}${top_mem mem_res 1}${color}
${voffset 4}${alignr 39}${color6}${top_mem mem_res 2}${color}
${voffset 4}${alignr 39}${color6}${top_mem mem_res 3}${color}
${voffset 4}${alignr 39}${color6}${top_mem mem_res 4}${color}
${voffset 4}${alignr 39}${color6}${top_mem mem_res 5}${color}
${voffset -106}${goto 40}${color4}Process${color}
${voffset -13}${alignc}${color4}Memory %${color}
${voffset -13}${alignr 39}${color4}Memory${color}
\
# The network section #
\
${if_existing /proc/net/route ppp0}
${voffset -227}${goto 40}${color5}Up: ${color2}${upspeed ppp0}${color5}${goto 150}Down: ${color2}${downspeed ppp0}
${voffset 10}${goto 40}${upspeedgraph ppp0 26,80 ffffff D80000}${goto 150}${downspeedgraph ppp0 26,80 ffffff D80000}
${voffset 9}${goto 40}${color5}Sent: ${color2}${totalup ppp0}${color5}${goto 150}Received: ${color2}${totaldown ppp0}
${else}
${if_existing /proc/net/route ppp1}
${voffset -240}${goto 40}${color5}Up: ${color2}${upspeed ppp1}${color5}${goto 150}Down: ${color2}${downspeed ppp1}
${voffset 10}${goto 40}${upspeedgraph ppp1 26,80 ffffff D80000}${goto 150}${downspeedgraph ppp1 26,80 ffffff D80000}
${voffset 9}${goto 40}${color5}Sent: ${color2}${totalup ppp1}${color5}${goto 150}Received: ${color2}${totaldown ppp1}
${else}
${if_existing /proc/net/route wlp2s1}
${voffset -253}${goto 40}${color5}Up: ${color2}${upspeed wlp2s1}${color5}${goto 150}Down: ${color2}${downspeed wlp2s1}
${voffset 10}${goto 40}${upspeedgraph wlp2s1 26,80 ffffff D80000}${goto 150}${downspeedgraph wlp2s1 26,80 ffffff D80000}
${voffset 9}${goto 40}${color5}Sent: ${color2}${totalup wlp2s1}${color5}${goto 150}Received: ${color2}${totaldown wlp2s1}
${else}
${if_existing /proc/net/route wlp2s0}
${voffset -266}${goto 40}${color5}Up: ${color2}${upspeed wlp2s0}${color5}${goto 150}Down: ${color2}${downspeed wlp2s0}
${voffset 10}${goto 40}${upspeedgraph wlp2s0 26,80 ffffff D80000}${goto 150}${downspeedgraph wlp2s0 26,80 ffffff D80000}
${voffset 9}${goto 40}${color5}Sent: ${color2}${totalup wlp2s0}${color5}${goto 150}Received: ${color2}${totaldown wlp2s0}
${else}
${if_existing /proc/net/route wlan0}
${voffset -279}${goto 40}${color5}Up: ${color2}${upspeed wlan0}${color5}${goto 150}Down: ${color2}${downspeed wlan0}
${voffset 8}${goto 40}${upspeedgraph wlan0 26,80 ffffff D80000}${goto 150}${downspeedgraph wlan0 26,80 ffffff D80000}
${voffset 9}${goto 40}${color5}Sent: ${color2}${totalup wlan0}${color5}${goto 150}Received: ${color2}${totaldown wlan0}
${else}
${if_existing /proc/net/route wlan1}
${voffset -292}${goto 40}${color5}Up: ${color2}${upspeed wlan1}${color5}${goto 150}Down: ${color2}${downspeed wlan1}
${voffset 10}${goto 40}${upspeedgraph wlan1 26,80 ffffff D80000}${goto 150}${downspeedgraph wlan1 26,80 ffffff D80000}
${voffset 9}${goto 40}${color5}Sent: ${color2}${totalup wlan1}${color5}${goto 150}Received: ${color2}${totaldown wlan1}
${else}
${if_existing /proc/net/route eth1}
${voffset -305}${goto 40}${color5}Up: ${color2}${upspeed eth1}${color5}${goto 150}Down: ${color2}${downspeed eth1}
${voffset 10}${goto 40}${upspeedgraph eth1 26,80 ffffff D80000}${goto 150}${downspeedgraph eth1 26,80 ffffff D80000}
${voffset 9}${goto 40}${color5}Sent: ${color2}${totalup eth1}${color5}${goto 150}Received: ${color2}${totaldown eth1}
${else}
${if_existing /proc/net/route eth0}
${voffset -318}${goto 40}${color5}Up: ${color2}${upspeed eth0}${color5}${goto 150}Down: ${color2}${downspeed eth0}
${voffset 10}${goto 40}${upspeedgraph eth0 26,80 ffffff D80000}${goto 150}${downspeedgraph eth0 26,80 ffffff D80000}
${voffset 9}${goto 40}${color5}Sent: ${color2}${totalup eth0}${color5}${goto 150}Received: ${color2}${totaldown eth0}
${else}
${if_existing /proc/net/route enp0s0}
${voffset -331}${goto 40}${color5}Up: ${color2}${upspeed enp0s0}${color5}${goto 150}Down: ${color2}${downspeed enp0s0}
${voffset 10}${goto 40}${upspeedgraph enp0s0 26,80 ffffff D80000}${goto 150}${downspeedgraph enp0s0 26,80 ffffff D80000}
${voffset 9}${goto 40}${color5}Sent: ${color2}${totalup enp0s0}${color5}${goto 150}Received: ${color2}${totaldown enp0s0}
${else}
${if_existing /proc/net/route enp0s1}
${voffset -344}${goto 40}${color5}Up: ${color2}${upspeed enp0s1}${color5}${goto 150}Down: ${color2}${downspeed enp0s1}
${voffset 10}${goto 40}${upspeedgraph enp0s1 26,80 ffffff D80000}${goto 150}${downspeedgraph enp0s1 26,80 ffffff D80000}
${voffset 9}${goto 40}${color5}Sent: ${color2}${totalup enp0s1}${color5}${goto 150}Received: ${color2}${totaldown enp0s1}
${else}
${voffset -311}${goto 40}${color5}Network disconnected${color}
${image ~/.conky-weather/assets/Numix/God-Mode/offline.png -p 44,284 -s 16x16}
${endif}${endif}${endif}${endif}${endif}${endif}${endif}${endif}${endif}${endif}
\
# Various images including the icons of the forecast #
\
${image ~/.conky-weather/assets/Numix/God-Mode/pressure.png -p 224,95 -s 16x16}\
${image ~/.conky-weather/assets/Numix/God-Mode/humidity.png -p 224,115 -s 16x16}\
${image ~/.conky-weather/assets/Numix/God-Mode/wind-2.png -p 224,136 -s 16x16}\
${execi 300 cp -f ~/.conky-weather/icons/weather-icons-light2/$(grep "yweather:forecast" ~/.cache/weather.xml | grep -o "code=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==1').png ~/.cache/weather-1.png}${image ~/.cache/weather-1.png -p 41,207 -s 32x32}\
${execi 300 cp -f ~/.conky-weather/icons/weather-icons-light2/$(grep "yweather:forecast" ~/.cache/weather.xml | grep -o "code=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==2').png ~/.cache/weather-2.png}${image ~/.cache/weather-2.png -p 119,207 -s 32x32}\
${execi 300 cp -f ~/.conky-weather/icons/weather-icons-light2/$(grep "yweather:forecast" ~/.cache/weather.xml | grep -o "code=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==3').png ~/.cache/weather-3.png}${image ~/.cache/weather-3.png -p 195,207 -s 32x32}${font}${voffset -120}\
```

I didn't have to touch the alignment code at all as it was commented out for me by default, meaning it shouldn't be affecting anything. I too had to modify the gap_y and gap_x commands when I first set up Conky to get my display where I wanted it (it's a modified version of the Harmattan Conky theme).

Any help or suggestions are appreciated! :)

---

