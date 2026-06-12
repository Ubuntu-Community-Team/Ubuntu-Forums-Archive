---
title: "Conky help...."
date: 2018-01-24
forum: General Help
---

### Post by Furycd001 on 2018-01-24
HI Guys

Looking some help with conky. I've created a single line config but everytime it updates it updates on top of itself instead of just simply refreshing. I also can't seem to find out how to change the length of the battery bar. And also also how what do I need to set or change in order for the bar to be the width / length of the screen. If I add anything to my current config it doesn't appear properly and gets cut off. [Here's a link to my config file....]("https://paste.ubuntu.com/26451220/")

Many thanks in advanced for all of your help.

---

### Post by again? on 2018-01-24
Add
```
double_buffer = true,
```
to your conky.config section.

Be aware if you add to end of section to add a comma to previous line.
ie
```
    use_spacer = 'none',
    show_graph_scale = false,
    show_graph_range = false[COLOR="#FF0000"],[/COLOR]
    double_buffer = true,
 }
```

From "man conky"
> **battery_bar** (height),(width) (num)
Battery percentage remaining of ACPI battery in a bar. ACPI battery number can be given as argument (default is BAT0, use all to get the mean percentage remaining for all batteries).
eg
```
${battery_bar 10,100 BAT0}
```

Some of your config values are not right as well.
Lua uses true/false not yes/no. See my config.

If you want conky to fill the width of your screen use these values
```
minimum_width = [COLOR="#FF8C00"]1680[/COLOR],
maximum_width = [COLOR="#FF8C00"]1680[/COLOR],
minimum_height = 26,
```
[COLOR="#FF8C00"]1680[/COLOR] is my screen width. Use your width.

This is a one liner I use as an always visible bottom panel.
It won't work on your computer but use as reference for your config.
```
conky.config = {
--###
--# Use XFT? Required to Force UTF8 (see below).

	use_xft = true,
	font = 'Ubuntu:bold:size=10',
	xftalpha = 0.8,
	text_buffer_size = 1024,

--###
--# Force UTF8? Requires XFT (see above).
--# Displays degree symbol, instead of Â°, etc.

	override_utf8_locale = true,

--###
--# Daemonize Conky, aka 'fork to background'.

	background = false,

--###
--# Update interval in seconds.

	update_interval = 1.0,

--###
--# This is the number of times Conky will update before quitting.
--# Set to zero to run forever.

	total_run_times = 0,

--###
--# Create own window instead of using desktop (required in nautilus)?

	own_window = true,
	own_window_colour = '#2F343F',--#676767 use gtk-theme-config to set unity panel color then use gcolor2 eyedropper to get your panel color
	own_window_type = 'panel',
	own_window_transparent = false,
	own_window_hints = 'undecorated,sticky,skip_taskbar,skip_pager,above',
	default_color = 'dim gray',
	own_window_argb_visual = false,--# change to no if problems
	own_window_argb_value = 0,

--###
--# Use double buffering? Reduces flicker.

	double_buffer = true,

--###
--# Draw shades?

	draw_shades = false,
	default_shade_color = '#000000',

--###
--# Draw outlines?

	draw_outline = false,
--default_outline_color 000000

--###
--# Draw borders around text?

	draw_borders = false,

--###
--# Draw borders around graphs?

	draw_graph_borders = false,

--###
--# Print text to stdout?
--# Print text in console?

	out_to_ncurses = false,
	out_to_console = false,

--###
--# Text alignment.

	alignment = 'bottom_left',

--###
--# Minimum size of text area.

	minimum_width = 1680,
	maximum_width = 1680,
	minimum_height = 26,

--###
--# Gap between text and screen borders.

	gap_x = 0,
	gap_y = 0,

--###
--# Shorten MiB/GiB to M/G in stats.

	short_units = true,

--###
--# Pad % symbol spacing after numbers.

	pad_percents = 0,

--###
--# Pad spacing between text and borders.

	border_inner_margin = 0,
	border_outer_margin = 0,
	border_width = 0,

--###
--# Limit the length of names in "Top Processes".

	top_name_width = 10,

--###
--# Subtract file system -/+buffers/cache from used memory?
--# Set to yes, to produce meaningful physical memory stats.

	no_buffers = true,

--###
--# Set to yes, if you want all text to be in UPPERCASE.

	uppercase = false,

--###
--# Number of cpu samples to average.
--# Set to 1 to disable averaging.

	cpu_avg_samples = 2,

--###
--# Number of net samples to average.
--# Set to 1 to disable averaging.

	net_avg_samples = 2,

--###
--# Add spaces to keep things from moving around?
--# Only affects certain objects.

	use_spacer = 'right',

--###
--# My colors (suit yourself).

	color0 = 'White',
	color1 = 'Ivory',
	color2 = 'Ivory2',
	color3 = 'Ivory3',
	color4 = '#FF4040',
	color5 = '#FCE3BB',--text colour
	color6 = 'Gray',
	color7 = 'AntiqueWhite4',
	color8 = '#F9A41E',
	color9 = '#FFDB58',--icon

	lua_load = '~/conky/lua/bargraph_smallcpu-artful.lua',
	lua_draw_hook_post = 'main_bars',

--nvidia-settings -t -q GPUCoreTemp | head -n1
--sensors nouveau-pci-0100 | grep temp1 | awk '{print $2}' | cut -c2-3

};

conky.text = [[
${goto 680}${voffset 6}${color9}${font StyleBats:size=12}q${font}${color5}${offset 1}${voffset -2}CPU${font GE Inspira:bold:size=10}\
${goto 785}${execpi 3 sensors it8728-isa-0228 | awk '/temp2/ {gsub("[^0-9.+-]","",$2); printf("%.0f\n", $2)}' | xargs ~/conky/ColorTemp/ColorTempCPU.sh}°C\
${goto 830}${voffset 2}${color9}${font StyleBats:size=12}q${voffset -2}${offset 1}${font}${color5}HDD ${font GE Inspira:bold:size=10}${color orange}${execpi 10 hddtemp -n /dev/sda | xargs /home/glen/conky/ColorTemp/ColorTempHDD.sh}°C\
${goto 920}${voffset 1}${color9}${font StyleBats:size=12}q${offset 1}${voffset -1}${font}${color5}GPU ${font GE Inspira:bold:size=10}${font GE Inspira:bold:size=10}${execpi 5 nvidia-settings -t -q GPUCoreTemp | head -n1 | xargs /home/glen/conky/ColorTemp/ColorTempGPU.sh}°C\
${goto 1010}${color9}${voffset 1}${font StyleBats:size=12}q${font}${color5}${voffset -1}MEM ${font GE Inspira:bold:size=10}${color cyan1}${mem}\
${goto 1130}${voffset 1}${color green}${font PizzaDudeBullets:size=12}T${font GE Inspira:bold:size=10}${downspeedf enp3s0}\
${goto 1220}${voffset 0}${color yellow}${font PizzaDudeBullets:size=12}N${font GE Inspira:bold:size=10}${upspeedf eth enp3s0}${color5}\
${alignr 5}${font}${color5}DESK ${color cyan1}${font Circled:size=16}${desktop_name}${font}
]];
```

---

### Post by Furycd001 on 2018-01-25
Thank you very much. This has helped sort my problem ^^"

---

