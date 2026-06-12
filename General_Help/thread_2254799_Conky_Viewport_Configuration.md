---
title: "Conky Viewport Configuration"
date: 2014-11-30
forum: General Help
---

### Post by prusakjakub on 2014-11-30
Hello,

I am looking for a way to display different Conky layouts on different viewports, I am using Compiz. I have found this tutorial but I dont understand it well : [http://ubuntuforums.org/showthread.php?t=1797174](http://ubuntuforums.org/showthread.php?t=1797174) .
I have no idea how to do this and I'm a noob at this type of stuff.

Thanks

---

### Post by CantankRus on 2014-11-30
How many workspaces are you using?
...and are they (HorizontalxVertical) 4x1 or 2x2 or.......
What is your screen resolution?

When using compiz you really only have 1 desktop regardless of the amount of virtual desktops you have configured.
Install wmctrl for a better understanding....
```
sudo apt-get install wmctrl
```
Running in the terminal ....
```
wmctrl -d
```
Will show something like this...
```
[COLOR="#008000"]glen@Trusty:~$[/COLOR] **wmctrl -d**
0  * [COLOR="#FF0000"]**DG: 6720x1050**[/COLOR]  [COLOR="#FF8C00"]**VP: 0,0**[/COLOR]  WA: 49,24 1631x1026  N/A
```
My monitor resolution is **1680x1050** and I have **4x1** virtual workspaces.
[COLOR="#FF0000"]**DG: 6720x1050**[/COLOR] shows my desktop geometry is now 6720x1050  (ie my x resolution is now 4 x 1680)
[COLOR="#FF8C00"]**VP: 0,0**[/COLOR] shows the viewport position of the current workspace.

In conky you position windows with the settings in your config....
```
alignment top_left
gap_x 1780
gap_y 56
```
This will position a conky window at a distance of 1780 pixels from the lefthand side of your desktop.
So effectively it's positioned 100 pixels from the left on my second virtual workpace. (1680+100)

Also, in the conky config look for a line that looks like this...
```
own_window_hints undecorated,below,skip_taskbar,skip_pager
```
If this includes a setting "**sticky**", remove it as sticky windows appear on all worspaces.

Any problems, post your config.

---

### Post by prusakjakub on 2014-11-30
I am running 1366 x 768. I have 8 horizontal viewports on a cube using Compiz.

---

### Post by CantankRus on 2014-11-30
Okay.
Run in the terminal on each workspace...
```
wmctrl -d | awk '{print $6}'
```
This will give you the **x,y** coordinates of the top left of each workspace.
Then adjust the **gap_x** value in your config to position the conky window horizontally.
eg This will position conky on the second workspace 100 from left and 50 from top.
```
gap_x 1466
gap_y 50
```
Also make sure you're using this setting in the config...
```
own_window_type **normal**
```

---

### Post by prusakjakub on 2014-11-30
Can you tell me what file I need to modify. Do I need to have multiple conky windows? Sorry that Im such a noob at this, but I kinda need a more thorough tutorial/explanation.

Thanks :)

---

### Post by CantankRus on 2014-11-30
The application conky needs a config file to tell it what to display on screen.
If you run "conky" it will use any config named **.conkyrc** and placed in your home folder. The preceding dot makes it hidden.
Installing conky does not install a ~/.conkyrc config.
If there is no **~/.conkyrc** file conky will use the included sample config from **/etc/conky/conky.conf**

If you want to run multiple instances of conky you need to specify the path to a config with the **-c** option.
When starting with the **-c** option a config can be named whatever you like.
eg
```
conky -c /home/glen/conky/configs/gmail.conkyrc
conky -c /home/glen/conky/configs/clock.conkyrc
```
Anything in particular you want to display on the different workspaces?

Thread where members post their configs.
[**_[COLOR="#B22222"]Post your .conkyrc files w/ screenshots[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=281865&page=2299")
When using other peoples configs you may need to modify for your hardware and computing environment
as well as having any scripts or fonts used in the config.

There is also an application[**_[COLOR="#B22222"] conky-manager[/COLOR]_**]("http://www.teejeetech.in/p/conky-manager.html") which includes various different conky configs.

---

### Post by prusakjakub on 2014-12-01
Yes, I do use conky-manager. So let me get this straight I need a separate conky file for each viewport, (for any viewport apart from the 1st one I need to modify the gap x and y). Then I need to reference the separate conky files in the main .conkyrc file. And no, I just want to modify the position because the white parts of the conky windows overlap white parts of the wallpapers (I have different wallpapers on each desktop) and make them less readable.

Thanks :)

---

### Post by CantankRus on 2014-12-01
You would need to copy the config you are using from the ~/.conky folder
and start 8 conky configs because you can only specify conky to display on 1 workspace or all workspaces.

Probably better off modifying the config you are using to make it readable on all desktops. 
eg
You can add a semi-transparent background using a lua script, as in attached pic.
Which config in conky-manager are you using?

---

### Post by prusakjakub on 2014-12-02
If I was to modify the config that I am using, how would I change the values for each window (the windows on the othere viewport) without changing the original values (for the 1st viewport). What do you mean about the config. I'm using Conky Manager v2.0.2. Also in Conky Manager there is an option for a semi-transparent background.

---

### Post by CantankRus on 2014-12-02
> **prusakjakub said:**
> If I was to modify the config that I am using, how would I change the values for each window (the windows on the othere viewport) without changing the original values (for the 1st viewport). What do you mean about the config. I'm using Conky Manager v2.0.2. Also in Conky Manager there is an option for a semi-transparent background.
You can't.
The idea is to change the overall look of the conky so it wiil be readable against all wallpapers.
The "config" is whichever one conky-manager shows you are using.

The transparency in conky-manager will do the same as the lua script but will not have rounded corners.
You may also need to adjust the window size to make it look right.
Which config are you using?

---

### Post by prusakjakub on 2014-12-02
I've attached the conky config. So do I need to modify all of the 3 conky files?

---

### Post by CantankRus on 2014-12-02
Yes, conky manager is running 3 configs.
Before you start playing with the configs you may want to copy the **~/.conky/TransparentTiles2dayweather** folder to your desktop as a backup.
So you can replace if necessary.

Can you post a pic of the desktop where your conky is hard to see?

---

### Post by prusakjakub on 2014-12-02
Some of the text is over a white background so I want to move it (btw I changed the theme). Here is the code from the conky file I want to modify:

```
# Conky Metro Clock - http://fav.me/d424h9d

# Conky settings
background no
update_interval 1


override_utf8_locale yes


double_buffer yes
no_buffers yes


text_buffer_size 2048


# Window specifications
own_window yes
own_window_class conky
own_window_transparent yes
own_window_hints undecorate,below,sticky,skip_taskbar,skip_pager


border_inner_margin 0
border_outer_margin 0


alignment top_left
gap_x 100
gap_y 50


# Graphics settings
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no


# Text settings
use_xft yes
xftalpha 0
text_buffer_size 2048


uppercase no


default_color FFFFFF


own_window_argb_value 0
own_window_argb_visual yes
own_window_colour BABDB6
minimum_size 0 0
TEXT
${voffset 10}${font Open Sans Light:size=50}${time %A}${font}${voffset -10}
${voffset 10}${font Open Sans Light:size=50}${time %B} ${time %e}${font}${voffset -10}
${voffset 10}${font Open Sans Light:size=100}${time %H:%M %p}${font}${voffset -10}
```

What exactly do I need to modify/copy to change the position on another viewport.

Thanks :)

---

### Post by CantankRus on 2014-12-02
Can you run this in terminal so I can see which configs you are running.
I have conky-manager installed here and want to test.
```
ps aux | grep -i [c]onky | awk '{print $NF}'
```

To change the position of a conky use "edit widget" location tab.
or edit these settings in the config...
```
alignment top_left
gap_x 100
gap_y 50
```
As I said before this will change the location on all workspaces.

May want to look at using a smaller date/time config. Conky-manager has a few.

---

### Post by prusakjakub on 2014-12-02
This is what it returned

/tmp/conky-manager/1417547208375441291.sh
Clock/.conkyrc
Seamod/conky_seamod

---

### Post by CantankRus on 2014-12-02
Pic shows Gotham and Seamod conky configs.
I used conky-manager to add semi-transparency and change position.

---

### Post by prusakjakub on 2014-12-02
OK, I finally understand what I need to do, and it works as I wanted it to.

Thank You very much for your help :)

---

### Post by CantankRus on 2014-12-02
> **prusakjakub said:**
> OK, I finally understand what I need to do, and it works as I wanted it to.

Thank You very much for your help :)
 OK, no problem.
Just remember conky-manager is just an application to run different configs and to
easily edit some config settings for those not familiar with conky.
It uses scripts to run  "conky -c [COLOR="#808080"]/path/to/config[/COLOR]" and also edit the configs it installed to the **~/.conky** directory.
Goodluck.

---

