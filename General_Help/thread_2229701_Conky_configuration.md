---
title: "Conky configuration"
date: 2014-06-14
forum: General Help
---

### Post by b-12-3838 on 2014-06-14
Hello everybody,  
i'm still configuring my new Ubuntu-14-04 Unity OS for my own needs. Right at the moment im searching for a .conkyrc script that is working well.

    In this thread [http://ubuntuforums.org/showthread.php?t=281865&page=2278](http://ubuntuforums.org/showthread.php?t=281865&page=2278) the user Frogs Hair posted a conkyrc that i really like. 
But for some reason it does not work for my notebook.  

He wrote for the window specs:
  # Window specifications 
# gap_x 1040 
gap_y 70  

When i do the original script, then the conky display is cropped.
 When i change the gap_y70 to gap_y670 then the display of the conky manager is correctly. But then my tabs in firefox disappear as long as i terminate conky.   

To give you a better understanding i recorded everything with kazam and uploaded the video so you can better understand what i mean: [https://www.youtube.com/watch?v=ltQkpXHT97c](https://www.youtube.com/watch?v=ltQkpXHT97c) 
The problem with firefox starts from 1:10min  

Thanks in advance

---

### Post by ajgreeny on 2014-06-14
It will probably help if you show us all the config lines that relate to the positioning of the conky window on your screen.
As an example, here are mine:-
```
# Text alignment, other possible values are commented out with #
#alignment top_left
#alignment top_right
#alignment bottom_left
alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 25
gap_y 50

```which puts my conky window bottom right and 25px from the right edge and 50px from the bottom edge.
I also have min and max size for text area:-
```
# Minimum size of text area
minimum_size 320

# Maximum width
maximum_width 320
```
which means I need to set that width for some of the items which show in my window, eg
```
${cpugraph 20,320}${color #FFFFFF}
```

---

### Post by b-12-3838 on 2014-06-14
Ok thank you for your explanations.

> if you show us all the config lines that relate to the positioning of the conky window on your screen.

I dont know how to find that out :(

---

### Post by Frogs Hair on 2014-06-15
Does conky change position when the terminal is closed ? I ask because I see this behavior in Unity, but not Gnome. After the terminal is closed conky moves to my intended position. My display resolution is 1366 x 768 . I have instructions to change the weather location , but the weather conditions icons are too large of a package to be uploaded here on the forum.

---

### Post by ajgreeny on 2014-06-15
> **b-12-3838 said:**
> I dont know how to find that out :(
OK, so show us the whole of your .conkyrc, either as an attachment to your reply, or by copying the whole of the file content using code-tags,  ie, by pasting it in your reply then highlight the pasted text and click on the # icon in the toolbar.

---

### Post by b-12-3838 on 2014-06-19
Hello, sorry for my late response. 

Right at the moment im using this on my Ubuntu 14.04 unity on my desktop computer with a widescreen monitor. But the problems still exists.

The conkyrc script is from the user "Frogs Hair" and looks like this: 

```
[# Conky settings #
background no
update_interval 1
double_buffer yes
no_buffers yes
imlib_cache_size 10

# Window specifications #
gap_x 1040
gap_y 70
minimum_size 268 153
maximum_width 268
own_window yes
own_window_type panel  # other options are: override/dock/desktop/panel
own_window_transparent yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below
border_inner_margin 0
border_outer_margin 0
#alignment top_right
#own_window_argb_visual yes
#own_window_argb_value 0

# Graphics settings #
draw_shades no
default_shade_color AAAAAA
draw_outline no
default_outline_color AAAAAA
draw_borders no
draw_graph_borders no

# Text settings #
use_xft yes
xftalpha 0
xftfont telemarines:size=10
text_buffer_size 256
override_utf8_locale yes
override_utf8_locale yes
imlib_cache_size 0

# Color scheme #
default_color FFFFFF
color1 FFFFFF
color2 FFFFFF
color3 D64937

TEXT
# Various images #
${execi 300 curl -s "http://weather.yahooapis.com/forecastrss?w=12781634&u=f" -o ~/.cache/weather.xml}
\
# The name of the days #
\
${color1}${voffset 20}${alignc 90}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "day=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==1' | tr '[a-z]' '[A-Z]'}${color}
${color1}${voffset -17}${alignc}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "day=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==2' | tr '[a-z]' '[A-Z]'}${color}
${color1}${voffset -17}${alignc -90}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "day=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==3' | tr '[a-z]' '[A-Z]'}${color}
\
# The temperatures #
\
${color2}${voffset 51}${font Droid Sans :size=12}${alignc 90}${execi 300 grep "yweather:condition" ~/.cache/weather.xml | grep -o "temp=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"}°${font}${color}
${voffset -17}${color2}${alignc}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "low=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==2'}°/${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "high=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==2'}°${color}
${voffset -17}${color2}${alignc -90}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "low=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==3'}°/${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "high=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==3'}°${color}
\
# The icons of the forecast and condition #
\
${execi 300 cp -f ~/.conky-weather/icons/weather-icons-light3/$(grep "yweather:condition" ~/.cache/weather.xml | grep -o "code=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*").png ~/.cache/weather.png}${image ~/.cache/weather.png -p 27,65 -s 32x32}\
${execi 300 cp -f ~/.conky-weather/icons/weather-icons-light3/$(grep "yweather:forecast" ~/.cache/weather.xml | grep -o "code=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==2').png ~/.cache/weather-2.png}${image ~/.cache/weather-2.png -p 118,65 -s 32x32}\
${execi 300 cp -f ~/.conky-weather/icons/weather-icons-light3/$(grep "yweather:forecast" ~/.cache/weather.xml | grep -o "code=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==3').png ~/.cache/weather-3.png}${image ~/.cache/weather-3.png -p 209,65 -s 32x32}${font}\
${hr}
Uptime $alignr $uptime
Load $alignr $loadavg
Hostname $alignr $nodename

NETWORK & SYSTEM
${hr}
ESSID: $alignr ${wireless_essid wlan0}
Signal:$alignr ${wireless_link_qual wlan0}%
Download: $alignr ${downspeed wlan0}/s
Total: $alignr ${totaldown wlan0}
Upload: $alignr ${upspeed wlan0}/s
Total: $alignr ${totalup wlan0}
${hr}
CPU1: ${cpu cpu1}% $alignr  ${cpubar cpu1 8,60}
CPU2: ${cpu cpu2}% $alignr  ${cpubar cpu2 8,60}
CPU3: ${cpu cpu3}% $alignr  ${cpubar cpu3 8,60}
CPU4: ${cpu cpu4}% $alignr  ${cpubar cpu4 8,60}
${hr}
MEM $alignc $mem / $memmax $alignr $memperc%
${membar}
HOME $alignc ${fs_used /home} / ${fs_size /home}$alignr ${fs_free_perc /home}%
${fs_bar /home}
BATTERY
${battery_bar}${battery_percent BAT0}
ACPI $alignr ${acpiacadapter}

TOP
${hr}
${top_mem name 1} $alignr ${top_mem pid 1}$alignr    ${top_mem mem 1}
${top_mem name 2} $alignr ${top_mem pid 2}$alignr    ${top_mem mem 2}
${top_mem name 3}$alignr  ${top_mem pid 3} $alignr   ${top_mem mem 3}
${top_mem name 4} $alignr ${top_mem pid 4} $alignr   ${top_mem mem 4}
${top_mem name 5} $alignr ${top_mem pid 5}$alignr    ${top_mem mem 5}
```

On the video you can see the problems:
1) I cant place a windows on top of the conky bar, because it seems like there are some "hard" borders aroung the conky bar
2) The conky bar is not placed on the right side of my desktop screen
3) When i open firefox my opened tabs are hiding beyond my screen resolution
4) Im connected with LAN and the conky network & system bar is not responding

Video: [URL="https://www.youtube.com/watch?v=s_bUcrfYieE&feature=youtu.be"]https://www.youtube.com/watch?v=s_bUcrfYieE&feature=youtu.be
[/URL]
My perfect conky bar would look like the configured conkyscript from the user "Frogs Hair" but with the following infos about my system:


[LIST=1]
[*]Weather with icons 
[*]Uptime 
[*]Linux Kernel 
[*]Hostname 
[*]Network: current upload and download 
[*]CPU % 1-4 
[*]CPU temperature in degrees 
[*]Memory usage 
[*]Home folder disk space 
[*]Disk space of all connected drives 
[/LIST]

Maybe somebody could help me to create such script for conky. It would be great.

Thanks in advance for any help

---

### Post by Frogs Hair on 2014-06-19
The script you posted began with an already completed 3 day forecast configuration made by another user. Many of the elements you would like to add can be found in configurations on the Conky screen shot thread. You can also write them from scratch and there are various resources available. When specific examples where needed I found searching worked well.

Example. ```
 ${kernel} 				
```
Uptime: ```
$uptime
```
Host Name:```
 $nodename
```

[http://conky.sourceforge.net/docs.html](http://conky.sourceforge.net/docs.html)
[http://manpages.ubuntu.com/manpages/dapper/man1/conky.1.html](http://manpages.ubuntu.com/manpages/dapper/man1/conky.1.html)
[http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)

---

### Post by b-12-3838 on 2014-06-19
The problems are for me:

1) I dont speak perfectly English, so I need to look up many words in the dictionary that I dont know (especially when it comes to scripting or programming terms)
2) I dont know any programming language and I never wrote any scripts or anything similar to it
3)  My first steps with Linux (maybe 15-30 days ago) cost me a lot of  energy and time, because I am reading all the time how to do things in  Linux and how to solve many problems (especially with VM's), so maybe one day I will finally get familiar with the new OS.

So  all in all my change to the new OS already costs me a lot of time and I  dont want to spend much time writing not so much important conky  scripts.
I thought that there might be something that comes out of the box ;)
Conky-Manager  did not help me much. It does not give me the configuration I am  searching for and its been installed as a PPA that might endanger  endanger my system so I dont want to use conky-manager at all.

Furthermore  I have tested many pre-configured conky scripts. But in many cases I am  afraid not to use a script that may contain some malicious code,  because I cant understand any of the conky scripts I am using. So I  first need to search for a script from a user that I can trust. And  secondly I need to find a script that offers me the configuration I  like and one that is working out of the box ony my system. 

So at the end your script was the only one I liked and I trusted.  When I make the script work properly and add some information about the  CPU temps then it would be ok for me. 
When I finish all my  troubleshooting with my new Linux based OS then maybe I will start  adding some things to the conky script I would like.

So you would  help me a lot if you could make the script I have posted  work properly on my notebook and on my desktop pc =)

Thanks in advance

---

### Post by Frogs Hair on 2014-06-19
I am not a programmer either , I learned from looking at what others have done but I understand there is a language barrier. As wrote in an  earlier post the script starts in the wrong position for me in Unity an moves to the proper position when the terminal is closed. 

I also wrote that I am not able to upload the weather icons to the forum due to package size.The script was compiled for a Netbook running wireless. The following site has proven safe for me and I have downloaded and used different Conky scripts without any problems. Search Conky

[http://gnome-look.org/](http://gnome-look.org/)

---

### Post by grumblebum2 on 2014-06-19
As a learning experience download  [**_[COLOR="#B22222"]Conky-Harmattan[/COLOR]_**]("http://zagortenay333.deviantart.com/art/Conky-Harmattan-426662366")

It contains weather icons which are used for your conky and has a read me explaining how to change your
weather location.
Download and extract and look in **Harmattan/README/Installation+Description** for info.
You can just use the readme to install the icons and use Frogs Hair's config or try running the Harmattan config.

A conky config consists of two parts divided by a line which contains just the word "**TEXT**"
Above "**TEXT**" sets how conky is displayed......**CONFIGURATION SETTINGS**
Below "**TEXT**" is what conky displays......**OBJECTS/VARIABLES**

See the manual page for conky...
```
man conky
```
You can also view the manual online which I find easier to browse through...
[http://conky.sourceforge.net/docs.html](http://conky.sourceforge.net/docs.html)

As Frogs Hair said many of us have no scripting background and learnt from reading and each other.
Most conky configs have to be personalized and to do this you need to put in a bit of effort to understand how things work if 
you want to use all but a basic config.

Here is your config with a few changes I made.
Install the icons from Conky-Harmattan and test it. 
```
# Conky settings #
background no
update_interval 1
double_buffer yes
no_buffers yes
imlib_cache_size 10

# Window specifications #
[COLOR="#FF0000"]gap_x 15
gap_y 40[/COLOR]
minimum_size 268 153
maximum_width 268
own_window yes
own_window_type [COLOR="#FF0000"]normal[/COLOR]  # other options are: override/dock/desktop/panel
own_window_transparent yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below
border_inner_margin 0
border_outer_margin 0
[COLOR="#FF0000"]alignment top_right[/COLOR]
#own_window_argb_visual yes
#own_window_argb_value 0

# Graphics settings #
draw_shades no
default_shade_color AAAAAA
draw_outline no
default_outline_color AAAAAA
draw_borders no
draw_graph_borders no

# Text settings #
use_xft yes
xftalpha 0
xftfont telemarines:size=10
text_buffer_size 256
override_utf8_locale yes
override_utf8_locale yes
imlib_cache_size 0

# Color scheme #
default_color FFFFFF
color1 FFFFFF
color2 FFFFFF
color3 D64937

**TEXT**
# Various images #
${execi 300 curl -s "http://weather.yahooapis.com/forecastrss?w=12781634&u=f" -o ~/.cache/weather.xml}
\
# The name of the days #
\
${color1}${voffset 20}${alignc 90}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "day=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==1' | tr '[a-z]' '[A-Z]'}${color}
${color1}${voffset -17}${alignc}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "day=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==2' | tr '[a-z]' '[A-Z]'}${color}
${color1}${voffset -17}${alignc -90}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "day=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==3' | tr '[a-z]' '[A-Z]'}${color}
\
# The temperatures #
\
${color2}${voffset 51}${font Droid Sans :size=12}${alignc 90}${execi 300 grep "yweather:condition" ~/.cache/weather.xml | grep -o "temp=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"}°${font}${color}
${voffset -17}${color2}${alignc}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "low=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==2'}°/${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "high=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==2'}°${color}
${voffset -17}${color2}${alignc -90}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "low=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==3'}°/${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "high=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==3'}°${color}
\
# The icons of the forecast and condition #
\
${execi 300 cp -f ~/.conky-weather/icons/weather-icons-light3/$(grep "yweather:condition" ~/.cache/weather.xml | grep -o "code=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*").png ~/.cache/weather.png}${image ~/.cache/weather.png -p 27,65 -s 32x32}\
${execi 300 cp -f ~/.conky-weather/icons/weather-icons-light3/$(grep "yweather:forecast" ~/.cache/weather.xml | grep -o "code=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==2').png ~/.cache/weather-2.png}${image ~/.cache/weather-2.png -p 118,65 -s 32x32}\
${execi 300 cp -f ~/.conky-weather/icons/weather-icons-light3/$(grep "yweather:forecast" ~/.cache/weather.xml | grep -o "code=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==3').png ~/.cache/weather-3.png}${image ~/.cache/weather-3.png -p 209,65 -s 32x32}${font}\
${hr}
Uptime $alignr $uptime
Load $alignr $loadavg
Hostname $alignr $nodename

NETWORK & SYSTEM
${hr}
ESSID: $alignr ${wireless_essid wlan0}
Signal:$alignr ${wireless_link_qual wlan0}%
Download: $alignr ${downspeed wlan0}/s
Total: $alignr ${totaldown wlan0}
Upload: $alignr ${upspeed wlan0}/s
Total: $alignr ${totalup wlan0}
${hr}
CPU1: ${cpu cpu1}% $alignr  ${cpubar cpu1 8,60}
CPU2: ${cpu cpu2}% $alignr  ${cpubar cpu2 8,60}
CPU3: ${cpu cpu3}% $alignr  ${cpubar cpu3 8,60}
CPU4: ${cpu cpu4}% $alignr  ${cpubar cpu4 8,60}
${hr}
MEM $alignc $mem / $memmax $alignr $memperc%
${membar}
HOME $alignc ${fs_used /home} / ${fs_size /home}$alignr ${fs_free_perc /home}%
${fs_bar /home}
BATTERY
${battery_bar}${battery_percent BAT0}
ACPI $alignr ${acpiacadapter}

TOP
${hr}
${top_mem name 1} $alignr ${top_mem pid 1}$alignr    ${top_mem mem 1}
${top_mem name 2} $alignr ${top_mem pid 2}$alignr    ${top_mem mem 2}
${top_mem name 3}$alignr  ${top_mem pid 3} $alignr   ${top_mem mem 3}
${top_mem name 4} $alignr ${top_mem pid 4} $alignr   ${top_mem mem 4}
${top_mem name 5} $alignr ${top_mem pid 5}$alignr    ${top_mem mem 5}
```

If needing help with specific output, run conky in terminal and post the output.
To get CPU and hard drive temperatures you need to install lm-sensors and hddtemp.
Then there are certain steps you need to follow to configure these.
You then need to add lines to your conky to display these temps. 
The lines added depends on your hardware and output from sensors.

So as you see we can't write a config for you but are willing to help and guide you if you are willing to take the time to learn a few things.

---

### Post by Habitual on 2014-06-20
very first error message in that video is "sh 1: curl: not found".
Line [48 ]("http://ubuntuforums.org/showthread.php?t=281865&p=13020998#post13020998")
```
${execi 300 curl -s "http://weather.yahooapis.com/forecastrss?w=12781634&u=f" -o ~/.cache/weather.xml}
```
install curl.
And unless you want the weather for Neenah, WI. USA
I'd remark line 48 out for the time being while you debug the layout.
After that, visit [RSS Request]("https://developer.yahoo.com/weather/#request") and study how, and **if** you can get weather using yahoo's weather api.

I'm guessing the the weather-related stuff is missing also, or this is a result of not having curl installed.
```
# alignment top-right
``` is clearly remarked out so it has **zero** effect on your layout.
Unremark it and try ```
alignment tr
``` or ```
alignment top-right
```

It's a good point to bring up that unless you are an *experienced* conky user, that using other people's code off the 'net is a recipe for disaster.

---

### Post by Frogs Hair on 2014-06-20
> [COLOR=#000000]As a learning experience download [/COLOR][**_[COLOR=#B22222]Conky-Harmattan[/COLOR]_**]("http://zagortenay333.deviantart.com/art/Conky-Harmattan-426662366") The simple three day forecast script was used as the basis for my script and the package includes the needed icons. The other features were added based what I wanted to see and screen space. :wink:

---

### Post by NM5TF on 2014-06-20
if you really want something that will work "out of the box", then consider the most xclnt Conkywx

first you must install conky....

```
sudo apt-get install conky-all
```

.....and then go here to download the program:

[http://foreverquest.blogspot.in/search/label/conkywx](http://foreverquest.blogspot.in/search/label/conkywx)

then go to the wiki to read about config/set up files here:

[https://bitbucket.org/plikhari/conkywx_pub/wiki/Home](https://bitbucket.org/plikhari/conkywx_pub/wiki/Home)

then go to this forum to ask any questions you may have...and the Author
of the program is a regular there also.....go here:

[http://ubuntuforums.org/showthread.php?t=1771033&page=177](http://ubuntuforums.org/showthread.php?t=1771033&page=177)

here is a screenie of what is possible with the app.....

tommy

---

### Post by b-12-3838 on 2014-06-22
@grumblebum2:

Thank you a lot for this detailed explanation. It helped me a lot at understanding the basics of it.

Meanwhile i have tried out the "out of the box" conky Harmattan scripts and they are just great. But i just can figure out how to add cpu temps beneath the cpu usage bar.

To make it simple i only would like to add the cpu temp and not the hdd temp.
I have already installed "sudo lm-sensors" and used "sudo sensors-detect". Everything works fine in the terminal.

The harmattan conky script looks like this:

```
# Conky settings #
background yes
update_interval 1
double_buffer yes
no_buffers yes
imlib_cache_size 10

# Window specifications #
gap_x 20
gap_y 100
minimum_size 268 620
maximum_width 268
own_window yes
own_window_type normal  # other options are: override/dock/desktop/panel
own_window_transparent yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below
border_inner_margin 0
border_outer_margin 0
alignment top_right
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
default_color 333333
color1 FFFFFF
color2 777777
color3 777777
color4 AAAAAA
color5 A0D468
color6 AC92EC
color7 FC6E51
color8 4FC0E9

TEXT
# Various images #
${execi 300 curl -s "http://weather.yahooapis.com/forecastrss?w=44418&u=c" -o ~/.cache/weather.xml}
${image ~/.conky-weather/assets/Flatts/God-Mode/top-bg.png -p 20,25 -s 228x66}\
${image ~/.conky-weather/assets/Flatts/God-Mode/shadow.png -p 20,591 -s 228x3}\
${image ~/.conky-weather/assets/Flatts/God-Mode/bottom-bg.png -p 20,473 -s 228x119}\
${execi 300 cp -f ~/.conky-weather/icons/weather-photos-7/$(grep "yweather:condition" ~/.cache/weather.xml | grep -o "code=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*").png ~/.cache/weather.png}${image ~/.cache/weather.png -p 20,91 -s 228x86}\
${image ~/.conky-weather/assets/Flatts/God-Mode/bg-1.png -p 20,177 -s 228x86}\
${image ~/.conky-weather/assets/Flatts/God-Mode/bg-2.png -p 20,263 -s 228x105}\
${image ~/.conky-weather/assets/Flatts/God-Mode/bg-3.png -p 20,368 -s 228x105}\
${image ~/.conky-weather/assets/Flatts/God-Mode/bg-4.png -p 20,478 -s 228x14}\
${image ~/.conky-weather/assets/Flatts/God-Mode/separator-v.png -p 95,185 -s 1x76}\
${image ~/.conky-weather/assets/Flatts/God-Mode/separator-v.png -p 172,185 -s 1x76}\
${image ~/.conky-weather/assets/Flatts/God-Mode/separator-h.png -p 33,369 -s 202x1}\
${image ~/.conky-weather/assets/Flatts/God-Mode/separator-h.png -p 33,269 -s 202x1}\
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
${goto 36}${voffset -172}${font Droid Sans :size=36}${color1}${execi 300 grep "yweather:condition" ~/.cache/weather.xml | grep -o "temp=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"}°${font}${color}
${goto 46}${voffset 14}${font Droid Sans :size=12}${color1}${execi 300 grep "yweather:condition" ~/.cache/weather.xml | grep -o "text=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"}${font}${color}
${color1}${alignr 52}${voffset -73}${execi 300 grep "yweather:atmosphere" ~/.cache/weather.xml | grep -o "pressure=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"} ${execi 300 grep "yweather:units" ~/.cache/weather.xml | grep -o "pressure=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"}
${color1}${alignr 52}${voffset 7}${execi 300 grep "yweather:atmosphere" ~/.cache/weather.xml | grep -o "humidity=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"} %${color}
${color1}${alignr 52}${voffset 7}${execi 300 grep "yweather:wind" ~/.cache/weather.xml | grep -o "speed=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"} ${execi 300 grep "yweather:units" ~/.cache/weather.xml | grep -o "speed=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"}${color}
\
# Clock + calendar #
\
${voffset -117}${font Droid Sans Mono :size=22}${alignc}${color2}${time %H:%M}${font}${color}
${voffset 4}${font Droid Sans :size=10}${alignc}${color4}${time %A, %B %d}${font}${color}
\
# Cpu, memory, uptime, and load graph #
\
${voffset 294}${goto 40}${color8}Cpu:${color}
${voffset 4}${goto 40}${color5}Mem:${color}
${voffset 4}${goto 40}${color6}Uptime:${color}
${voffset -47}${alignr 39}${color2}${cpu cpu0}%${color}
${voffset 4}${alignr 39}${color2}${memperc}%${color}
${voffset 4}${alignr 39}${color2}${uptime_short}${color}
${voffset -47}${alignc}${color8}${cpubar 5,36}${color}
${voffset 4}${alignc}${color5}${membar 5,36}${color}
${voffset 29}${goto 40}${loadgraph 26,190 ac92ec ac92ec -l}
\
# The processes section #
\
${voffset 26}${goto 40}${color2}${top_mem name 1}${color}
${voffset 4}${goto 40}${color2}${top_mem name 2}${color}
${voffset 4}${goto 40}${color2}${top_mem name 3}${color}
${voffset 4}${goto 40}${color2}${top_mem name 4}${color}
${voffset 4}${goto 40}${color2}${top_mem name 5}${color}
${voffset -81}${alignc}${color8}${top_mem mem 1}%${color}
${voffset 4}${alignc}${color8}${top_mem mem 2}%${color}
${voffset 4}${alignc}${color8}${top_mem mem 3}%${color}
${voffset 4}${alignc}${color8}${top_mem mem 4}%${color}
${voffset 4}${alignc}${color8}${top_mem mem 5}%${color}
${voffset -81}${alignr 39}${color6}${top_mem mem_res 1}${color}
${voffset 4}${alignr 39}${color6}${top_mem mem_res 2}${color}
${voffset 4}${alignr 39}${color6}${top_mem mem_res 3}${color}
${voffset 4}${alignr 39}${color6}${top_mem mem_res 4}${color}
${voffset 4}${alignr 39}${color6}${top_mem mem_res 5}${color}
${voffset -104}${goto 40}${color1}Proc${color}
${voffset -13}${alignc}${color1}Mem%${color}
${voffset -13}${alignr 39}${color1}Mem${color}
\
# The network section #
\
${if_existing /proc/net/route ppp0}
${voffset -227}${goto 40}${color5}Up: ${color2}${upspeed ppp0}${color6}${goto 150}Down: ${color2}${downspeed ppp0}
${voffset 10}${goto 40}${upspeedgraph ppp0 26,80 4fc0e9 4fc0e9}${goto 150}${downspeedgraph ppp0 26,80 4fc0e9 4fc0e9}
${voffset 9}${goto 40}${color5}Sent: ${color2}${totalup ppp0}${color6}${goto 150}Received: ${color2}${totaldown ppp0}${image ~/.conky-weather/assets/Flatts/God-Mode/online.png -p 20,25 -s 228x5}
${else}
${if_existing /proc/net/route ppp1}
${voffset -240}${goto 40}${color5}Up: ${color2}${upspeed ppp1}${color6}${goto 150}Down: ${color2}${downspeed ppp1}
${voffset 10}${goto 40}${upspeedgraph ppp1 26,80 4fc0e9 4fc0e9}${goto 150}${downspeedgraph ppp1 26,80 4fc0e9 4fc0e9}
${voffset 9}${goto 40}${color5}Sent: ${color2}${totalup ppp1}${color6}${goto 150}Received: ${color2}${totaldown ppp1}${image ~/.conky-weather/assets/Flatts/God-Mode/online.png -p 20,25 -s 228x5}
${else}
${if_existing /proc/net/route wlp2s1}
${voffset -253}${goto 40}${color5}Up: ${color2}${upspeed wlp2s1}${color6}${goto 150}Down: ${color2}${downspeed wlp2s1}
${voffset 10}${goto 40}${upspeedgraph wlp2s1 26,80 4fc0e9 4fc0e9}${goto 150}${downspeedgraph wlp2s1 26,80 4fc0e9 4fc0e9}
${voffset 9}${goto 40}${color5}Sent: ${color2}${totalup wlp2s1}${color6}${goto 150}Received: ${color2}${totaldown wlp2s1}${image ~/.conky-weather/assets/Flatts/God-Mode/online.png -p 20,25 -s 228x5}
${else}
${if_existing /proc/net/route wlp2s0}
${voffset -266}${goto 40}${color5}Up: ${color2}${upspeed wlp2s0}${color6}${goto 150}Down: ${color2}${downspeed wlp2s0}
${voffset 10}${goto 40}${upspeedgraph wlp2s0 26,80 4fc0e9 4fc0e9}${goto 150}${downspeedgraph wlp2s0 26,80 4fc0e9 4fc0e9}
${voffset 9}${goto 40}${color5}Sent: ${color2}${totalup wlp2s0}${color6}${goto 150}Received: ${color2}${totaldown wlp2s0}${image ~/.conky-weather/assets/Flatts/God-Mode/online.png -p 20,25 -s 228x5}
${else}
${if_existing /proc/net/route wlan0}
${voffset -279}${goto 40}${color5}Up: ${color2}${upspeed wlan0}${color6}${goto 150}Down: ${color2}${downspeed wlan0}
${voffset 8}${goto 40}${upspeedgraph wlan0 26,80 4fc0e9 4fc0e9}${goto 150}${downspeedgraph wlan0 26,80 4fc0e9 4fc0e9}
${voffset 9}${goto 40}${color5}Sent: ${color2}${totalup wlan0}${color6}${goto 150}Received: ${color2}${totaldown wlan0}${image ~/.conky-weather/assets/Flatts/God-Mode/online.png -p 20,25 -s 228x5}
${else}
${if_existing /proc/net/route wlan1}
${voffset -292}${goto 40}${color5}Up: ${color2}${upspeed wlan1}${color6}${goto 150}Down: ${color2}${downspeed wlan1}
${voffset 10}${goto 40}${upspeedgraph wlan1 26,80 4fc0e9 4fc0e9}${goto 150}${downspeedgraph wlan1 26,80 4fc0e9 4fc0e9}
${voffset 9}${goto 40}${color5}Sent: ${color2}${totalup wlan1}${color6}${goto 150}Received: ${color2}${totaldown wlan1}${image ~/.conky-weather/assets/Flatts/God-Mode/online.png -p 20,25 -s 228x5}
${else}
${if_existing /proc/net/route eth1}
${voffset -305}${goto 40}${color5}Up: ${color2}${upspeed eth1}${color6}${goto 150}Down: ${color2}${downspeed eth1}
${voffset 10}${goto 40}${upspeedgraph eth1 26,80 4fc0e9 4fc0e9}${goto 150}${downspeedgraph eth1 26,80 4fc0e9 4fc0e9}
${voffset 9}${goto 40}${color5}Sent: ${color2}${totalup eth1}${color6}${goto 150}Received: ${color2}${totaldown eth1}${image ~/.conky-weather/assets/Flatts/God-Mode/online.png -p 20,25 -s 228x5}
${else}
${if_existing /proc/net/route eth0}
${voffset -318}${goto 40}${color5}Up: ${color2}${upspeed eth0}${color6}${goto 150}Down: ${color2}${downspeed eth0}
${voffset 10}${goto 40}${upspeedgraph eth0 26,80 4fc0e9 4fc0e9}${goto 150}${downspeedgraph eth0 26,80 4fc0e9 4fc0e9}
${voffset 9}${goto 40}${color5}Sent: ${color2}${totalup eth0}${color6}${goto 150}Received: ${color2}${totaldown eth0}${image ~/.conky-weather/assets/Flatts/God-Mode/online.png -p 20,25 -s 228x5}
${else}
${if_existing /proc/net/route enp0s0}
${voffset -331}${goto 40}${color5}Up: ${color2}${upspeed enp0s0}${color6}${goto 150}Down: ${color2}${downspeed enp0s0}
${voffset 10}${goto 40}${upspeedgraph enp0s0 26,80 4fc0e9 4fc0e9}${goto 150}${downspeedgraph enp0s0 26,80 4fc0e9 4fc0e9}
${voffset 9}${goto 40}${color5}Sent: ${color2}${totalup enp0s0}${color6}${goto 150}Received: ${color2}${totaldown enp0s0}${image ~/.conky-weather/assets/Flatts/God-Mode/online.png -p 20,25 -s 228x5}
${else}
${if_existing /proc/net/route enp0s1}
${voffset -344}${goto 40}${color5}Up: ${color2}${upspeed enp0s1}${color6}${goto 150}Down: ${color2}${downspeed enp0s1}
${voffset 10}${goto 40}${upspeedgraph enp0s1 26,80 4fc0e9 4fc0e9}${goto 150}${downspeedgraph enp0s1 26,80 4fc0e9 4fc0e9}
${voffset 9}${goto 40}${color5}Sent: ${color2}${totalup enp0s1}${color6}${goto 150}Received: ${color2}${totaldown enp0s1}${image ~/.conky-weather/assets/Flatts/God-Mode/online.png -p 20,25 -s 228x5}
${else}
${voffset -344}${goto 40}${color7}Network disconnected${color}
${image ~/.conky-weather/assets/Flatts/God-Mode/offline.png -p 20,25 -s 228x5}
${endif}${endif}${endif}${endif}${endif}${endif}${endif}${endif}${endif}${endif}
\
# Various images including the icons of the forecast #
\
${image ~/.conky-weather/assets/Flatts/God-Mode/pressure.png -p 224,95 -s 16x16}\
${image ~/.conky-weather/assets/Flatts/God-Mode/humidity.png -p 224,115 -s 16x16}\
${image ~/.conky-weather/assets/Flatts/God-Mode/wind-2.png -p 224,136 -s 16x16}\
${execi 300 cp -f ~/.conky-weather/icons/weather-icons-dark2/$(grep "yweather:forecast" ~/.cache/weather.xml | grep -o "code=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==1').png ~/.cache/weather-1.png}${image ~/.cache/weather-1.png -p 41,207 -s 32x32}\
${execi 300 cp -f ~/.conky-weather/icons/weather-icons-dark2/$(grep "yweather:forecast" ~/.cache/weather.xml | grep -o "code=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==2').png ~/.cache/weather-2.png}${image ~/.cache/weather-2.png -p 119,207 -s 32x32}\
${execi 300 cp -f ~/.conky-weather/icons/weather-icons-dark2/$(grep "yweather:forecast" ~/.cache/weather.xml | grep -o "code=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==3').png ~/.cache/weather-3.png}${image ~/.cache/weather-3.png -p 195,207 -s 32x32}${font}${voffset -120}\
```

But I cant make the follwing cpu temp script work properly:
```
 Mem: ${offset 9}$color$mem / $memmax${offset 10}
  ${color 111000}CPU 0 ${offset 9}$color${cpu cpu0}% (${execi 8 sensors | grep -A 1 'temp2' | cut -c13-16 | sed '/^$/d'}°C)   
  ${color 111000}CPU 1 ${offset 9}$color${cpu cpu1}% (${execi 8 sensors | grep -A 1 'temp2' | cut -c13-16 | sed '/^$/d'}°C)
```

When i insert it beneath the cpu usage section than there is a disharmony between both scripts. The cpu temp info pops up somewhere between text, images and symbols of the other script.

Is there a way to make it work properly?

Thanks in advance

---

### Post by grumblebum2 on 2014-06-22
This will aid in determining which temp is your cpu.
Install inxi...
```
sudo apt-get install inxi
```

Then run
```
sensors && inxi -s
```
and post your output.


eg my output
```
glen@Trusty:~$ sensors && inxi -s
it8728-isa-0228
Adapter: ISA adapter
in0:          +0.84 V  (min =  +0.00 V, max =  +3.06 V)
in1:          +1.49 V  (min =  +0.00 V, max =  +3.06 V)
in2:          +1.99 V  (min =  +0.00 V, max =  +3.06 V)
+3.3V:        +3.22 V  (min =  +0.00 V, max =  +6.12 V)
in4:          +1.93 V  (min =  +0.00 V, max =  +3.06 V)
in5:          +2.21 V  (min =  +0.00 V, max =  +3.06 V)
in6:          +2.21 V  (min =  +0.00 V, max =  +3.06 V)
3VSB:         +3.26 V  (min =  +0.00 V, max =  +6.12 V)
Vbat:         +3.10 V  
fan1:        1695 RPM  (min =    0 RPM)
fan2:        1123 RPM  (min =    0 RPM)
fan3:           0 RPM  (min =    0 RPM)
temp1:        +25.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
**temp2**:        +[COLOR="#FF0000"]24.0°C[/COLOR]  (low  = +127.0°C, high = +127.0°C)  sensor = thermal diode
temp3:        +17.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = Intel PECI
intrusion0:  ALARM

k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +11.0°C  (high = +70.0°C)
                       (crit = +80.0°C, hyst = +77.0°C)

fam15h_power-pci-00c4
Adapter: PCI adapter
power1:       63.01 W  (crit =  95.06 W)

Sensors:   System Temperatures: [COLOR="#FF0000"]cpu: 24.0C[/COLOR] mobo: 10.9C gpu: 25C 
           Fan Speeds (in rpm): cpu: 1123 fan-1: 1695 fan-3: 0
```

The last 2 lines is my inxi output and shows my **temp2** sensors output is my cpu.

The harmattan config is somewhat unusual in that it uses a number of images.
Adding lines to the config can throw out the positioning of text to the images.
I added the CPU and HDD temps to existing lines so as not to alter text vertical alignment.

---

