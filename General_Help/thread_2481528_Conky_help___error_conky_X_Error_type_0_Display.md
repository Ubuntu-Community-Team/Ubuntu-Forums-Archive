---
title: "Conky help   error: conky: X Error: type 0 Display"
date: 2022-12-01
forum: General Help
---

### Post by PantherStu on 2022-12-01
Hi all, 
back to linux after a few years, and trying to get my custom conky running.

So have installed and checked it all worked with the default conky.conf.  But I get an error when I run with my conky, so know it must be my conky.conf file.
Any help to fix this would be great. Thanks

error:
```
stu@stu-Lenovo-B590:~$ conky -c /home/stu/.conky/conkyrc-right.confconky: desktop window (600102) is subwindow of root window (230)
conky: drawing to desktop window
conky: X Error: type 0 Display 560f037547e0 XID 6291714 serial 120 error_code 8 request_code 55 minor_code 0 other Display: 560f037547e0



```

My current conky.conf file
```


conky.config = {
	update_interval = 2,
	total_run_times = 0,
	net_avg_samples = 1,
	cpu_avg_samples = 1,
	imlib_cache_size = 0,
	double_buffer = yes,
	no_buffers = yes,
	use_xft = yes,
	override_utf8_locale = yes,
	text_buffer_size = 2048,
	own_window_argb_visual = yes,
	own_window_colour = '#000000',
	own_window_argb_value = 0,
	own_window = yes,
	own_window_class = 'Conky',
	own_window_type = 'normal',
	own_window_transparent = yes,
	own_window_hints = 'undecorated,sticky,skip_taskbar,skip_pager',
	alignment = 'top_right',
	gap_x = 0,
	gap_y = 30,
	minimum_width = 280, minimum_height = 0,
	draw_shades = no,
	default_color = '#ffffff',
	default_shade_color = '#000000',
	color0 = '#00d9ff',
	color1 = '#ffffff',
	color2 = '#c5c5c5',
	color3 = '#ff8400',
}


conky.text = [[
${goto 210}${color0}${font Zekton:style=bold:size=13}${voffset 40}${exec whoami}
${voffset -45}${font Zekton:style=Bold:size=12}${color}${goto 90}${uptime}
${goto 90}${color1}${font Zekton:style=Bold:size=12}${color3}${distribution}${color}${font}
${font Chinacat:size=12}${offset 70}${voffset 45}${time %B %d, %Y}
${voffset -11}${goto 65}${color3}${font Zekton:style=bold:size=30}${time %H:%M}
${voffset -30}${font}${color1}${goto 200}${font Zekton:style=Bold:size=11}PC Temp
${goto 220}${font Zekton:style=Bold:size=11}${color1}${font Zekton:style=bold:size=11}${acpitemp}${font Zekton:style=bold:size=11}°C 
${voffset 30}${goto 82}/home 
${goto 82}${font Zekton:style=Bold:size=10}${fs_used /home}
${voffset 30}${goto 25}${font Zekton:style=Bold:size=10}/dev/sda2${goto 113}/dev/sda3${font Zekton:style=Bold:size=10}${color1}${goto 207}/root
${goto 30}${font Zekton:size=9}${diskio /dev/sda2}${goto 120}${diskio /dev/sda3} ${goto 207}${font Zekton:size=9}${fs_used /}
${voffset 22}${font Zekton:style=Bold:size=11}${goto 83}RAM${goto 175}SWAP
${font Zekton:style=Bold:size=9}${goto 83}${memperc}%${goto 175}${swapperc}%
${font Zekton:style=Bold:size=10}${voffset 40}${goto 50}kernel${goto 130} ${kernel}
${font Zekton:style=Bold:size=10}${goto 50}machine${goto 130}${machine}
${font Zekton:style=Bold:size=10}${voffset 10}${goto 50}Cpu 0 ${goto 130}${cpugraph cpu0 15,100 ffffff 000000 -t} ${font Zekton:size=8}${cpu cpu0}%
${font Zekton:style=Bold:size=10}${goto 50}Cpu 1 ${goto 130}${cpugraph cpu1 15,100 ffffff 000000 -t} ${font Zekton:size=8}${cpu cpu1}%
${font Zekton:style=Bold:size=10}${goto 50}Cpu 2 ${goto 130}${cpugraph cpu2 15,100 ffffff 000000 -t} ${font Zekton:size=8}${cpu cpu2}%
${font Zekton:style=Bold:size=10}${goto 50}Cpu 3 ${goto 130}${cpugraph cpu3 15,100 ffffff 000000 -t} ${font Zekton:size=8}${cpu cpu3}%


${image ~/.conky/LinuxLarge.png -p 10,0}
]]



```


If you need anymore info, please let me know

---

### Post by MAFoElffen on 2022-12-02
There is an extra coma character at the end of line 30, right before the first ending curly brace ([SIZE=4]**}**[/SIZE]) in line 31... Take that out and it should work.

---

### Post by PantherStu on 2022-12-02
Hi I have just looked and cannot find the extra comma, 

i have line 30 as
```
	color2 = '#c5c5c5',
```
and the line before the first ( } ) is 
```
	color3 = '#ff8400',
``` 
which also only has one comma

---

### Post by MAFoElffen on 2022-12-02
This in red
```

            color2 = '#c5c5c5',
            color3 = '#ff8400'[COLOR=#ff0000],[/COLOR]
        }

```
The comas are field separators... But there shouldn't be one at the end, before the closing curly brace.

EDIT: With it there, it is expecting another field (which is not there).

---

### Post by PantherStu on 2022-12-02
Awesome thankyou, didnt even think of that.
Thanks

---

