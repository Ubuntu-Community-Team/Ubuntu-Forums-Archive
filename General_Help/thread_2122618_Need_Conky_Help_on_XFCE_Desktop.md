---
title: "Need Conky Help on XFCE Desktop"
date: 2013-03-05
forum: General Help
---

### Post by techaesthete on 2013-03-05
Hi, I am using Xubuntu 12.04 X64 and have Conky running on my desktop. I am using the [Gotham]("http://psyjunta.deviantart.com/art/Gotham-Conky-config-205465419") theme that I modified for my desktop. I really like it, but I'd like to make some improvements I'll be listing here.

First, an example desktop with just the right contrast (I hope you like it!):
[IMG]https://sphotos-b.xx.fbcdn.net/hphotos-ash4/484951_483356735045071_1967407658_n.jpg[/IMG]

Next, the actual .conkyrc file:
```
use_xft yes
xftfont 123:size=8
xftalpha 0.1
update_interval 1
total_run_times 0
own_window no
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 250 5
maximum_width 500
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color white
default_shade_color red
default_outline_color green
alignment bottom_right
gap_x 90
gap_y 20
no_buffers yes
uppercase no
cpu_avg_samples 2
net_avg_samples 1
override_utf8_locale yes
use_spacer yes


TEXT
${voffset 10}${color EAEAEA}${font Ubuntu:pixelsize=120}${time %I:%M}${font}${voffset -84}${offset 10}${color FFA300}${font Ubuntu:pixelsize=42}${time %d} ${voffset -15}${color EAEAEA}${font Ubuntu:pixelsize=22}${time  %b} ${time %Y}${font}${voffset 24}${font Ubuntu:pixelsize=58}${offset -148}${time %a}${font}
${voffset 1}${offset 12}${font Ubuntu:pixelsize=12}${color FFA300}HD ${offset 11}$color${fs_free /} / ${fs_size /}${offset 30}${color FFA300}RAM ${offset 11}$color$mem / $memmax${offset 30}${color FFA300}CPU ${offset 11}$color${cpu cpu0}%
```

I like it, but not every background I use is compatible for it because of poor contrast (too bright for widget text). Is there a way I can code in a dark, shaded border like that of a desktop notification (see example below)?
[IMG]https://sphotos-a.xx.fbcdn.net/hphotos-snc7/481359_483358045044940_1186439152_n.jpg[/IMG]

It would be nice to always have a clean border to help give it more contrast. If you have a better solution, please let me know. I greatly appreciate any help!

Here's one of my example desktops, just because I like to show off:
[IMG]https://sphotos-b.xx.fbcdn.net/hphotos-ash4/481883_483358528378225_653802745_n.jpg[/IMG]

---

### Post by Mr. Shannon on 2013-03-06
Back when I was using conky (does not work well with my latest desktop environment) I used the image command to load a semi transparent background that I created in GIMP.  The command I have in my old conky config file is:
```
${image $HOME/.conky.clock.background.png -p 0,75}
```
if that helps.

---

### Post by stinkeye on 2013-03-06
You can use lua to draw a semi-transparent background.
It will draw to the size of your conky window.

Try this conkyrc and lua script.
```
use_xft yes
xftfont 123:size=8
xftalpha 0.1
update_interval 1
total_run_times 0
[COLOR="#FF0000"]own_window yes[/COLOR]
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
[COLOR="#FF0000"]minimum_size 480 180
maximum_width 480[/COLOR]
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color white
default_shade_color red
default_outline_color green
alignment bottom_right
gap_x 90
gap_y 20
no_buffers yes
uppercase no
cpu_avg_samples 2
net_avg_samples 1
override_utf8_locale yes
use_spacer yes

[COLOR="#0000FF"]lua_load /home/glen/conky/lua/draw_bg.lua
lua_draw_hook_pre draw_bg[/COLOR]

TEXT
${voffset 10}${color EAEAEA}${font Ubuntu:pixelsize=120}${time %I:%M}${font}${voffset -84}${offset 10}${color FFA300}${font Ubuntu:pixelsize=42}${time %d} ${voffset -15}${color EAEAEA}${font Ubuntu:pixelsize=22}${time  %b} ${time %Y}${font}${voffset 24}${font Ubuntu:pixelsize=58}${offset -148}${time %a}${font}
${voffset 1}${offset 12}${font Ubuntu:pixelsize=12}${color FFA300}HD ${offset 11}$color${fs_free /} / ${fs_size /}${offset 30}${color FFA300}RAM ${offset 11}$color$mem / $memmax${offset 30}${color FFA300}CPU ${offset 11}$color${cpu cpu0}%
```

[COLOR="#FF0000"]Changes I made[/COLOR] to your config.
[COLOR="#0000FF"]Lines to load the lua script.[/COLOR] Edit the path to reflect where you save draw_bg.lua

Save as **draw_bg.lua**
```
--[[	Background by londonali1010 (2009)
	VinDSL Background Hack (2010-2011)

This script draws a background to the Conky window. It covers the whole of the Conky window, but you can specify rounded corners, if you wish.

To call this script in Conky, use (assuming you have saved this script to ~/scripts/):
	lua_load ~/scripts/draw_bg.lua
	lua_draw_hook_pre draw_bg

Changelog:
	+ v3.0	VinDSL Hack (01.28.2011) Killed memory leak.
	+ v2.4	VinDSL Hack (01.25.2011) Declared all variables in local.
	+ v2.3	VinDSL Hack (12.31.2010) Added shading example(s).
	+ v2.2	VinDSL Hack (12.30.2010) Cleaned up the code a bit.
	+ v2.1	VinDSL Hack (12.24.2010) Added cairo destroy function(s).
	+ v2.0	VinDSL Hack (12.21.2010) Added height adjustment variable.
	+ v1.0	Original release (07.10.2009)

]]

--------------START OF PARAMETERS ------------

-- Change these settings to affect your background:

-- "corner_r" is the radius, in pixels, of the rounded corners. If you don't want rounded corners, use 0.

	local corner_r = 30

-- Set the colour and transparency (alpha) of your background (0.00 - 0.99).

--	(Light Shading Example)
--	local bg_colour = 0x4d4d4d
--	local bg_alpha = 0.50

--	(Medium Shading Example)
--	local bg_colour = 0x222222
--	local bg_alpha = 0.50

--	(Dark Shading Example)
--	local bg_colour = 0x000000
--	local bg_alpha = 0.02

--	(Brown Shading Example)
--	local bg_colour = 0x330000
--	local bg_alpha = 0.04

--	(Ivory Black Shading Example)
--	local bg_colour = 0x292421
--	local bg_alpha = 0.22

--	(Navy Blue Shading Example)
--	local bg_colour = 0x33339F
--	local bg_alpha = 0.33

--	(Olive Green Shading Example)
--	local bg_colour = 0x333319
--	local bg_alpha = 0.13

--	(Silver Shading Example)
--	local bg_colour = 0xc0c0c0
--	local bg_alpha = 0.05

	local bg_colour = 0x112024
	local bg_alpha = 0.75

-- Tweaks the height of your background, in pixels. If you don't need to adjust the height, use 0.

--	(Default Setting)
	local vindsl_hack_height = 0

--	local vindsl_hack_height = -228

---------------END OF PARAMETERS -------------

require 'cairo'
local	cs, cr = nil

local function rgb_to_r_g_b(colour,alpha)
	return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
	end

function conky_draw_bg()
	if conky_window == nil then return end
	if cs == nil then cairo_surface_destroy(cs) end
	if cr == nil then cairo_destroy(cr) end
	local w = conky_window.width
	local h = conky_window.height
	local v = vindsl_hack_height
	local cs = cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, conky_window.width, conky_window.height)
	local cr = cairo_create(cs)
	
	cairo_move_to(cr,corner_r,0)
	cairo_line_to(cr,w-corner_r,0)
	cairo_curve_to(cr,w,0,w,0,w,corner_r)
	cairo_line_to(cr,w,h+v-corner_r)
	cairo_curve_to(cr,w,h+v,w,h+v,w-corner_r,h+v)
	cairo_line_to(cr,corner_r,h+v)
	cairo_curve_to(cr,0,h+v,0,h+v,0,h+v-corner_r)
	cairo_line_to(cr,0,corner_r)
	cairo_curve_to(cr,0,0,0,0,corner_r,0)
	cairo_close_path(cr)

	cairo_set_source_rgba(cr,rgb_to_r_g_b(bg_colour,bg_alpha))
	cairo_fill(cr)

	cairo_surface_destroy(cs)
	cairo_destroy(cr)
	end
```
In the lua script..
line 27 allows you to change the corner radius.
lines 63 & 64 the colour and transparency.

I'm using Unity so not sure how it will display in xfce.

---

