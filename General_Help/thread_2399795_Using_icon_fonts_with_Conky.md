---
title: "Using icon fonts with Conky"
date: 2018-08-29
forum: General Help
---

### Post by isuzufan on 2018-08-29
I can't figure out how to use icon fonts (specifically font awesome) with Conky. I've looked through the documentation on Font Awesome's website but none of their methods work for me. I have the fonts installed on my system and I know how to reference the font in Conky.  

```
${font Font Awesome 5 Free:style=Regular:pixelsize=14}
```

My problem is that I don't know how to refer to the actual icon. When I look at other Conky config files where people have used Font Awesome, the actual character is just a vertical rectangle. And it's the same vertical rectangel for ALL icons.  I don't know how to make he icon I want appear in Conky.  

Can someone point me in the right direction, please?

---

### Post by ajgreeny on 2018-08-29
Not sure if this will make any difference but do you have the fonts installed system-wide in **/usr/share/fonts** or just in your **/home/username/.fonts** folder?

Perhaps conky needs them in the system folder.

---

### Post by again? on 2018-08-30
I have been using conky for a long while but must admit I am not familiar with this type of font.
I found a [conky config on github]("https://github.com/andrea-rosa/conky-config") that uses FontAwesome.
The syntax used in the config is
```
${font FontAwesome}
```
*or include a size other than default*
```
${font FontAwesome:size=16}

```

Running the config I get as below because I don't have the font installed.
[ATTACH=CONFIG]280905[/ATTACH]

After installing the package **fonts-font-awesome** and restarting conky,
gedit and conky now show the characters.
```
sudo apt install fonts-font-awesome
```
[ATTACH=CONFIG]280906[/ATTACH]


I don't know if there is an easier way but if you want to use a different character you can open Character Map and choose
"By unicode block" in the View menu, then choose FontAwesome. 
Most of the characters in my conky I found in the "Private Use Area" section in the left panel.
Double click the character box to show in the bottom text input where you can copy. 
[ATTACH=CONFIG]280909[/ATTACH]

---

### Post by isuzufan on 2018-08-31
Thanks for replying!

I did make sure that the font was installed systemwide (it was).  So that was not the issue. But I did achieve success!  See my other post.

---

### Post by isuzufan on 2018-08-31
Thank you for replying.  Your answer helped me figure it out.  

First, I was having a problem referencing the font.  This font appears in my system as "Font Awesome 5 Free" so I assumed that was the name I needed to use. Nope. It turns out that you were correct that I needed to reference the font as FontAwesome.  I actually tried this before I posted my original question, but there seems to be another issue with Font Awesome...some of their icons just don't work.  I would paste the glyph into my document (referencing the font correctly) but all I would get is a vertical rectangle in Conky. On a whim I tried a different icon and it worked!  Some of their icons don't work, I guess. 

Second, using your advice I was able to cut and paste a glyph from their online icon gallery[https://fontawesome.com/icons?d=gallery](https://fontawesome.com/icons?d=gallery) and paste it into my conkyrc file. In the following sample code, the icon appears as a rectangle. But in my conkyrc file, it appears as an icon. 

```
${font FontAwesome:size=14}&#61461;
```

Anyway, here's a screen capture of my conky.  Thanks for your help!

[IMG]https://lh3.googleusercontent.com/-I-Ta9YbWj3w/W4k9eNMbCoI/AAAAAAAA-0o/kxk0-u_K8dU1kZnfHiTQwxCYUpQuu4JzQCJoC/w530-h673-n-rw/desktop_conky_only.png[/IMG]

---

### Post by again? on 2018-09-01
> **isuzufan said:**
> Thank you for replying.  Your answer helped me figure it out.  

First, I was having a problem referencing the font.  This font appears in my system as "Font Awesome 5 Free" so I assumed that was the name I needed to use. Nope. It turns out that you were correct that I needed to reference the font as FontAwesome.  I actually tried this before I posted my original question, but there seems to be another issue with Font Awesome...some of their icons just don't work.  I would paste the glyph into my document (referencing the font correctly) but all I would get is a vertical rectangle in Conky. On a whim I tried a different icon and it worked!  Some of their icons don't work, I guess. 

Second, using your advice I was able to cut and paste a glyph from their online icon gallery[https://fontawesome.com/icons?d=gallery](https://fontawesome.com/icons?d=gallery) and paste it into my conkyrc file. In the following sample code, the icon appears as a rectangle. But in my conkyrc file, it appears as an icon. 

```
${font FontAwesome:size=14}&#61461;
```

Anyway, here's a screen capture of my conky.  Thanks for your help!



Can you post your conkyrc please.

---

### Post by isuzufan on 2018-09-02
> **guber2 said:**
> Can you post your conkyrc please.

Sure.  Here you go....

```
--[[ conky configuration ------------------------------
 For conky variables and commands use the terminal command:


 man conky


 ------------------------------
 BunsenLabs conky threads


 Index » Scripts, Tutorials & Tips » Conky - Calendars / Clocks / Time
 https://forums.bunsenlabs.org/viewtopic.php?id=516


 Open a thread and post conky questions in: Index » GUI & Applications
 https://forums.bunsenlabs.org/viewforum.php?id=4


 Display your completed conky and codes
 Index » Scripts, Tutorials & Tips » Show us your conky
 https://forums.bunsenlabs.org/viewtopic.php?id=512


 ------------------------------
 BunsenLabs conky scripts help
 Openbox Menu/Preferences/Conky/Conky Manager Help


 If there are one or more conkys running, it is possible to kill one conky with
 the following command, IF you used what is between the quotes to start the conky, e.g.:
 pkill -xf "conky -q -c $HOME/.config/conky/BL-Default.conkyrc"
]]




conky.config = {


--  Window Settings
    own_window = true,
    own_window_type = 'normal',
    own_window_transparent = true,
    own_window_hints = 'undecorated,below,skip_taskbar,skip_pager,sticky',
    own_window_colour = '678b8b',
    own_window_class = 'Conky',
    own_window_title = 'BunsenLabs Default Conky',


-- ARGB can be used for real transparency
--own_window_argb_visual = true, -- Options: true|false


-- NOTE that a composite manager is required for real transparency and ARGB will not
-- work as desired (in most cases) in conjunction with 'own_window_type override'.
-- Use with: own_window_type = 'normal',
-- Use with: own_window_transparent = false,


-- When ARGB visuals are enabled, use the following to modify the alpha value. Valid
-- range is 0-255, where 0 is 0% opacity, and 255 is 100% opacity.
--own_window_argb_value = 150,


    minimum_width = 260, minimum_height = 20,-- width | height
    maximum_width = 600,


    gap_x = 980,-- left | right
    gap_y = -275,-- up | down


--alignment = 'top_right',
--  End Window Settings




--  Font Settings
-- Use Xft (anti-aliased font and stuff)
    use_xft = true,


--font = 'Liberation Mono:bold:size=10',
--font = 'Liberation Sans:size=10',
--Icons: ${font Conky Icons by Carelli:size=14}
    font = 'Roboto:size=12',
 
-- Alpha of Xft font. Must be a value at or between 1 and 0
    xftalpha = 1,


-- Force UTF8? requires XFT
    override_utf8_locale = true,


    uppercase = false,
--  End Font Settings


--  Color Settings
    draw_shades = false,
    default_shade_color = 'eae2d9',


    draw_outline = false,-- amplifies text if true
    default_outline_color = 'eae2d9',


--default_color = '678b8b', -- Beam green
--default_color = '656667', -- Waldorf original colour
--default_color = '7a7a7a', -- Flame  & BunsenLabs Grey
--default_color = '929292', -- BunsenLabs Grey
	default_color = 'C0C0C0', -- BunsenLabs Silver
    color0 = 'B0E0E6', -- PowderBlue
    color1 = '778899', -- LightSlateGray
    color2 = 'D8BFD8', -- Thistle
    color3 = 'c1c8e5', -- YellowGreen
	color4 = 'ffa886', -- LightSalmon2
--color4 = 'af5450', -- LightSalmon2
--color4 = 'FFC4AD', -- LightSalmon2
    color5 = '6f8ae9', -- SpaceDarkBlue
--color5 = 'D7DCEE', -- SpaceLightBlue
    color6 = '00BFFF', -- DeepSkyBlue
    color7 = '5F9EA0', -- CadetBlue
    color8 = 'eae2d9', -- TreeLightBrown
--color8 = 'e5e8f4', -- SpaceLightBlue2
    color9 = 'f3f4fa', -- light
    
--  End Color Settings




--  Borders Section
    draw_borders = false,
-- Stippled borders?
    stippled_borders = 5,
-- border margins
    border_inner_margin = 5,
    border_outer_margin = 0,
-- border width
    border_width = 2,
-- graph borders
    draw_graph_borders = false,
--default_graph_height = 15,
--default_graph_width = 40,
--  End Borders Section




--  Miscellaneous Section
-- Boolean value, if true, Conky will be forked to background when started.
    background = true,


-- Adds spaces around certain objects to stop them from moving other things
-- around, this only helps if you are using a mono font
-- Options: right, left or none
    use_spacer = 'none',


-- Default and Minimum size is 256 - needs more for single commands that
-- "call" a lot of text IE: bash scripts
--text_buffer_size = 6144,


-- Subtract (file system) buffers from used memory?
    no_buffers = true,


-- change GiB to G and MiB to M
    short_units = true,


-- Imlib2 image cache size, in bytes. Default 4MiB Increase this value if you use
-- $image lots. Set to 0 to disable the image cache.
    imlib_cache_size = 0,


-- Use the Xdbe extension? (eliminates flicker)
-- It is highly recommended to use own window with this one
-- so double buffer won't be so big.
    double_buffer = true,


-- Maximum size of user text buffer, i.e. layout below TEXT line in config file
-- (default is 16384 bytes)
--max_user_text = 16384,


-- Desired output unit of all objects displaying a temperature. Parameters are
-- either "fahrenheit" or "celsius". The default unit is degree Celsius.
--temperature_unit = 'Fahrenheit',


-- Update interval in seconds
    update_interval = 1,


--  End Miscellaneous Section
};




conky.text = [[
#
${alignr}${color8}${font Roboto:style=Regular:pixelsize=50}${time %H:%M}${font}
${alignr}${color8}${font Roboto:style=Regular:pixelsize=16}${time %A} ${color4}${time %d} ${time %B} ${color8}${time %Y}${font}
#${time %A %d %B %Y}
${voffset 15}
#
${goto 105}${color8}${font Roboto:style=Regular:pixelsize=12}(${mem} / ${memmax})${font}
${voffset -3}${goto 105}${color8}${membar 10}
#
${goto 17}${voffset -40}${color8}${font FontAwesome:size=20}&#62171;${font}
${goto 16}${voffset -6}${color8}${font Roboto:style=Regular:pixelsize=14}ram${font}
${voffset -33}${goto 60}${color4}${font Roboto:style=Regular:pixelsize=16}${memperc}%${font}
#
#
#
${voffset 15}
#
#
#
${goto 60}${color4}${cpu cpu1}% ${goto 105}${color8}${cpubar cpu1 10}${font}
${goto 60}${color4}${cpu cpu2}% ${goto 105}${color8}${cpubar cpu2 10}${font}
#
${goto 15}${voffset -38}${color8}${font FontAwesome:size=20}&#62003;${font}
${goto 17}${voffset -7}${color8}${font Roboto:style=Regular:pixelsize=14}cpu${font}
#
#
#
${voffset 8}
#
#
#
${goto 65}${color8}${font FontAwesome:size=13}&#62098;${font}${goto 105}${color8}${fs_bar 10 /}${font}
${voffset -3}${goto 60}${color4}${font Roboto:style=Regular:pixelsize=16}${fs_used_perc /}%${color8}${font Roboto:style=Regular:pixelsize=12}${goto 105}${color8}(${fs_used /} / ${fs_size /})${font}
${voffset -18}
${goto 65}${color8}${font FontAwesome:size=14}&#61461;${goto 105}${color8}${voffset 2}${fs_bar 10 /home}${font}
${voffset -3}${goto 60}${color4}${font Roboto:style=Regular:pixelsize=16}${fs_used_perc /home}%${goto 105}${voffset -1}${font Roboto:style=Regular:pixelsize=12}${color8}(${fs_used /home} / ${fs_size /home})${font}
#
${goto 16}${voffset -65}${color8}${font FontAwesome:size=20}&#61888;${font}
${goto 15}${voffset -1}${color8}${font Roboto:style=Regular:pixelsize=14}disk${font}
#
#
#
${voffset 25}
#
#
#
${goto 98}${font Conky Icons by Carelli:size=13}&#386;${font}${goto 120}${voffset -1}${color4}${upspeed wlp5s0}${color8}${font}${goto 209}${font Conky Icons by Carelli:size=13}&#386; ${font}${goto 232}${voffset -1}${color4}${upspeed enp6s5}${color8}${font}
${goto 98}${font Conky Icons by Carelli:size=13}&#385; ${font}${goto 120}${voffset -1}${color4}${downspeed wlp5s0}${color8}${font}${goto 209}${font Conky Icons by Carelli:size=13}&#385; ${font}${goto 232}${voffset -1}${color4}${downspeed enp6s5}${color8}${font}
${voffset -35}${goto 63}${color8}${font FontAwesome:size=16}&#61931;
${voffset -9}${goto 60}${font Roboto:style=Regular:pixelsize=10}wlp5s0${font}
${voffset -39}${goto 176}${color8}${font FontAwesome:size=16}&#61672;
${voffset -9}${goto 170}${font Roboto:style=Regular:pixelsize=10}enp6s5${font}
${goto 17}${voffset -45}${color8}${font FontAwesome:size=20}&#61612;${font}
${goto 15}${voffset -5}${color8}${font Roboto:style=Regular:pixelsize=14}com${font}
#
#
#
${voffset 10}
#
#
#
#S Y S T E M    I N F O
#${hr}
#Host:${alignr}${nodename}
#Uptime:${alignr}${uptime}
#RAM:$alignr${mem} / ${memmax}
#Swap usage:${alignr}${swap} / ${swapmax}
#Disk usage:$alignr${fs_used /} / ${fs_size /}
#Root usage:$alignr${fs_used /} / ${fs_size /}
#Home usage:$alignr${fs_used /home} / ${fs_size /home}
#CPU Average:${alignr}${cpu cpu0}%
#
# Weather information from openweathermap.org can be displayed in conky by
# using the script $HOME/.config/conky/scripts/bunsenweather.sh. The openweathermap
# service requires registration in order to receive an API Key, which has to be
# added to bunsenweather.sh. For further info see this script and the following thread:
# https://forums.bunsenlabs.org/viewtopic.php?id=2060
#
# Calling bunsenweather.sh from conky works by using
# ${execpi <t> /path/to/bunsenweather.sh "yourlocation"}
# where <t> is the update interval. If "yourlocation" is not defined, the script
# sets geolocation based on your IP adress using the website ipinfo.io.
#
#W E A T H E R
#${hr}
#${execpi 600 $HOME/.config/conky/scripts/bunsenweather.sh}


${color8}${font Roboto:style=Light:pixelsize=14}S H O R T C U T    K E Y S${font}${color8}
${hr}
Win${alignr}Main Menu
Win + r${alignr}Run Dialog${voffset 10}
#
Win + t${alignr}Terminal
Win + f${alignr}File Manager${voffset 10}
#
Alt + Sh + w${alignr}Screen Cap Full
Alt + Sh + s${alignr}Screen Cap Active
Alt + Sh + c${alignr}Color Picker
Alt + Sh + m${alignr}Ruler${voffset 10}
#
Win + h${alignr}Task Manager
Win + Esc${alignr}Kill Crosshairs
Win + l${alignr}Lock Screen${voffset 5}${font}
#Win + x${alignr}Logout
#Win + e${alignr}Editor
#Win + m${alignr}Media Player
#Win + w${alignr}Web Browser
#Win + v${alignr}Volume Control
#Alt + F2${alignr}Run Dialog
#Alt + F3${alignr}Alt Menu
#Win + Tab${alignr}Active Apps
]];



```

---

