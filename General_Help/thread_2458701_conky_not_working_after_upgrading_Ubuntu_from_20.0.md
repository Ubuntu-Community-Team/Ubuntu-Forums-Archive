---
title: "conky not working after upgrading Ubuntu from 20.04 to 20.10"
date: 2021-03-02
forum: General Help
---

### Post by shmu26 on 2021-03-02
I probably need to update my .conkyrc but the automatic tool didn't help for that,
maybe someone can tell me what I need to change here?
```
background yes
use_xft yes
xftfont Liberation Sans:size=9
xftalpha 1
update_interval 1.0
total_run_times 0
own_window yes
own_window_transparent yes
own_window_type normal

own_window_hints undecorated,below,skip_taskbar,skip_pager
double_buffer yes
minimum_size 700 150
maximum_width 500
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no

default_shade_color 000000
default_outline_color 828282
alignment top_right
gap_x -1100
gap_y 60
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale yes

default_color edf1f6
color1 2da83b
color2 2da73b
color3 db303e

own_window_argb_value 0
own_window_colour 000000


own_window_argb_visual yes
TEXT
#time
${offset 170}${color}${font Quicksand - U:pixelsize=70}${if_match "pmfix${time %p}" == "pmfix"}${time %k:%M}${else}${time %I:%M}${endif}${font}${font}${voffset -45}${offset 10}${font Roboto-Light - U:pixelsize=35}${time %P}${font}



#date
${voffset 5}${offset 100}${color2}${font Droid:pixelsize=30}${time %A}${font}${goto 275}${voffset -18}${color2}${font Droid:pixelsize=30}  ${time %x}${font}

#sys
${offset 130}${font Roboto-Light:pixelsize=20}${offset 9}${offset 9}${color1}hdd ${color}${offset 9}$color${fs_used_perc /}%${offset 9}${color1}mem ${offset 9}${color}${memperc}%${offset 9}${offset 9}${color1}cpu${offset 9}${color}${cpu}%${font}
```

---

### Post by ajgreeny on 2021-03-02
You say conky's not working but does that mean you get a a bad display for conky or do you see nothing at all?

If you try to start conky in terminal with command ```
conky
``` you will probably see some error messages telling you what is not working.

Post those errors back here and we may be able to help further.

---

### Post by shmu26 on 2021-03-02
```
conky 
conky: Syntax error (/home/shmuel/.conkyrc:1: syntax error near 'ye
s') while reading config file.  
conky: Assuming it's in old syntax and attempting conversion. 
conky: [string "..."]:159: attempt to call a nil value (global 'loa
dstring')



```

---

### Post by ajgreeny on 2021-03-03
Well it is obviously a problem with your .conkyrc file which now uses "true" in place of "yes" in the settings.
Have a look in your .conkyrc (after backing it up) and then replace all instances of ***yes*** with ***true*** to see if that helps

Please post its content here if you can not find the problem yourself, using code-tags please, (not HTML tags as you did above).
See my signature below for a How-to for code-tags.

---

### Post by deadflowr on 2021-03-03
Personally, I would recommend converting the conkyrc into the new lua-based syntax.
There are some converter scripts around, or you can do it manually.
Methods found here should still apply: [https://forums.bunsenlabs.org/viewtopic.php?id=3983]("https://forums.bunsenlabs.org/viewtopic.php?id=3983")

---

### Post by ajgreeny on 2021-03-04
Thanks deaflowr.
I was pretty sure there was a conversion script that I had tried (without success, if I remember correctly, but it was three years ago or more so perhaps it did work) but I could not find it and did not have time to search.

Your comments have, nevertheless, mentioned several things I was unaware of, such as the hex colour codes not needing the # prefix, so I had continued using them until now but have just edited my file to remove them and all still works as that link said it would.
I thought hex colour codes always used # as prefix and everywhere else that I see them used still has them showing.

---

### Post by shmu26 on 2021-03-05
I tried fixing the instances of "yes", and I still got a similar error. I further tried fixing the config manually and automated, and still haven't succeeded.
So this brings me to my next question: is there a way I can install the old, deprecated version of conky on my Ubuntu 20.10 system? It worked fine on 20.04...

---

### Post by ajgreeny on 2021-03-05
I don't use 20.10 so have no idea about using an old version of conky but would say that if you really want to try it it should not be too difficult to find the .deb of that version somewhere and then install it simply to try it out.

However, it may be better in many ways to try to figure out what is wrong with your current .conkyrc file.
Can you post it here as an attachment (just name it conky.txt to attach it) or just paste it in a post using code tags, so we can investigate further; at present we are just shooting in the dark, not knowing what more to suggest.

---

### Post by shmu26 on 2021-03-05
The config is posted in the OP
I tried unsuccessfully to install the old version: I uninstalled the new, downloaded the deb of the old, installed a dependency, and for some reason, conky STILL complained that I was using the old format. I can't figure it out.

---

### Post by Frogs Hair on 2021-03-05
I attempted to update using my own working .rc by adding the brackets  and text but still getting an old syntax and other errors. 

Edit: I see that the syntax is  missing required elements. I'll try again.

Edit: After many tries to update the syntax still getting errors. There are some values I'm not familiar with so  I can't update correctly. 

```
own_window_argb_value 0
own_window_colour 000000
own_window_argb_visual yes 
```

---

### Post by deadflowr on 2021-03-05
I copied the OP conky, ran the convert.lua on it and it loads for me.
Here's the converted conkyrc
```
conky.config = {
	background = true,
	use_xft = true,
	font = 'Liberation Sans:size=9',
	xftalpha = 1,
	update_interval = 1.0,
	total_run_times = 0,
	own_window = true,
	own_window_transparent = true,
	own_window_type = 'normal',

	own_window_hints = 'undecorated,below,skip_taskbar,skip_pager',
	double_buffer = true,
	minimum_width = 700, minimum_height = 150,
	maximum_width = 500,
	draw_shades = false,
	draw_outline = false,
	draw_borders = false,
	draw_graph_borders = false,

	default_shade_color = '#000000',
	default_outline_color = '#828282',
	alignment = 'top_right',
	gap_x = -1100,
	gap_y = 60,
	no_buffers = true,
	uppercase = false,
	cpu_avg_samples = 2,
	override_utf8_locale = true,

	default_color = '#edf1f6',
	color1 = '#2da83b',
	color2 = '#2da73b',
	color3 = '#db303e',

	own_window_argb_value = 0,
	own_window_colour = '#000000',


	own_window_argb_visual = true,
};

conky.text = [[
#time
${offset 170}${color}${font Quicksand - U:pixelsize=70}${if_match "pmfix${time %p}" == "pmfix"}${time %k:%M}${else}${time %I:%M}${endif}${font}${font}${voffset -45}${offset 10}${font Roboto-Light - U:pixelsize=35}${time %P}${font}



#date
${voffset 5}${offset 100}${color2}${font Droid:pixelsize=30}${time %A}${font}${goto 275}${voffset -18}${color2}${font Droid:pixelsize=30}  ${time %x}${font}

#sys
${offset 130}${font Roboto-Light:pixelsize=20}${offset 9}${offset 9}${color1}hdd ${color}${offset 9}$color${fs_used_perc /}%${offset 9}${color1}mem ${offset 9}${color}${memperc}%${offset 9}${offset 9}${color1}cpu${offset 9}${color}${cpu}%${font}
]]
```

Edit: I'm used to testing/running various conky configs so i forget that most users don't know they can test conkys that are not the conkyrc file by running the conky command with the -c option.
That option allows it to run any conky config file regardless if it's the conkyrc or not.
So you can copy the config I posted and save under a new/different name and run the conky command with
```
conky -c new-conky--here
```
replace new-conky-here with whatever name you give.
This helps so you don't lose the original.

---

### Post by ajgreeny on 2021-03-06
I tried the conversion as well but did not have lua installed and did not know exactly what I should install; there are so many lua packages!

I tried it manually and got the display working eventually simply using "find and replace" in mousepad but didn't have time to test it properly so didn't post last night.

---

### Post by deadflowr on 2021-03-06
Should only need to install lua5.1.
Note, I copied the lua script from the /usr directory to my home directory and then needed to set it as executable
(chmod +x convert.lua)
I find it makes it easier for me.
The nice thing about the script is it's not overwriting the existing file but creates a brand new one.
So if it fails or creates a file with issues, the original is still there, unharmed.

---

### Post by shmu26 on 2021-03-06
> **deadflowr said:**
> I copied the OP conky, ran the convert.lua on it and it loads for me.
Here's the converted conkyrc
```
conky.config = {
    background = true,
    use_xft = true,
    font = 'Liberation Sans:size=9',
    xftalpha = 1,
    update_interval = 1.0,
    total_run_times = 0,
    own_window = true,
    own_window_transparent = true,
    own_window_type = 'normal',

    own_window_hints = 'undecorated,below,skip_taskbar,skip_pager',
    double_buffer = true,
    minimum_width = 700, minimum_height = 150,
    maximum_width = 500,
    draw_shades = false,
    draw_outline = false,
    draw_borders = false,
    draw_graph_borders = false,

    default_shade_color = '#000000',
    default_outline_color = '#828282',
    alignment = 'top_right',
    gap_x = -1100,
    gap_y = 60,
    no_buffers = true,
    uppercase = false,
    cpu_avg_samples = 2,
    override_utf8_locale = true,

    default_color = '#edf1f6',
    color1 = '#2da83b',
    color2 = '#2da73b',
    color3 = '#db303e',

    own_window_argb_value = 0,
    own_window_colour = '#000000',


    own_window_argb_visual = true,
};

conky.text = [[
#time
${offset 170}${color}${font Quicksand - U:pixelsize=70}${if_match "pmfix${time %p}" == "pmfix"}${time %k:%M}${else}${time %I:%M}${endif}${font}${font}${voffset -45}${offset 10}${font Roboto-Light - U:pixelsize=35}${time %P}${font}



#date
${voffset 5}${offset 100}${color2}${font Droid:pixelsize=30}${time %A}${font}${goto 275}${voffset -18}${color2}${font Droid:pixelsize=30}  ${time %x}${font}

#sys
${offset 130}${font Roboto-Light:pixelsize=20}${offset 9}${offset 9}${color1}hdd ${color}${offset 9}$color${fs_used_perc /}%${offset 9}${color1}mem ${offset 9}${color}${memperc}%${offset 9}${offset 9}${color1}cpu${offset 9}${color}${cpu}%${font}
]]
```

Edit: I'm used to testing/running various conky configs so i forget that most users don't know they can test conkys that are not the conkyrc file by running the conky command with the -c option.
That option allows it to run any conky config file regardless if it's the conkyrc or not.
So you can copy the config I posted and save under a new/different name and run the conky command with
```
conky -c new-conky--here
```
replace new-conky-here with whatever name you give.
This helps so you don't lose the original.
@deadflowr you get the prize. That works.

---

