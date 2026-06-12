---
title: "Conky Help (lagging)"
date: 2014-01-07
forum: General Help
---

### Post by nonothing on 2014-01-07
Okay, so I got a shiny new Ubuntu 13.10 install going after going away from Ubuntu for a little while. I got everything going well, including Conky.

Suddenly, though, I'm noticing that the conky I'm running is lagging pretty bad. Rather than updating every second, it's updating at random intervals between 2 and 20 seconds, as though it's getting bogged down. 

I'm using a conky from the Conky Manager app, called "Clock and stats". I modified it a little bit, to get my CPU temps to show up correctly and to get my UL/DL information to show up correctly. 

But I don't know why it's lagging. It didn't seem to lag at first, and then I noticed it had frozen. Maybe it was lagging before and I just didn't see it, or maybe it started randomly. I noticed it after I installed pyRoom and had it lock my windows up (though my Unity wasn't locked up so I rebooted through that and all was well). Right now nothing's running but a couple Terminal windows, this Chrome window, and my background processes (dropbox, and a program called AlienwareFX light). 

Can anybody help me figure out why it's lagging?

The most recent change was the upload/download fix, and I thought it was working fine after I made that change, but I took the whole section out just to see and it was still lagging. 

The conky rc is:


```
# Conky settings #
background yes
update_interval 1
cpu_avg_samples 2
net_avg_samples 2

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
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

border_inner_margin 0
border_outer_margin 0

minimum_size 1800 800
maximum_width 1920

alignment top_right
gap_x 90
gap_y 55

# Graphics settings #
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no

# Text settings #
use_xft yes
override_utf8_locale yes
xftfont Ubuntu:size=10
xftalpha 0.8
uppercase no

temperature_unit celsius

default_color FFFFFF
color1 DD4814
color2 444444

# Lua Load  #
lua_load ~/.conky/rings0-v1.2.1.lua
lua_draw_hook_pre ring_stats

own_window_argb_visual no
own_window_colour 000000
TEXT
${voffset 80}${alignr 130}$color1 ${font Ubuntu:size=28}${time %d}$color , ${time %B}
${goto 290}$color2 ${hr 2}$color2
${alignr 15}$color1 ${font Ubuntu:size=33}${time %G}${font}

${color}${voffset 30}${alignr}${nodename}
${alignr 10}$color1 Uptime $color ${uptime_short}
${alignr 20}${pre_exec cat /etc/issue.net}, ${kernel}

${alignr 30}Root $color1 ${fs_used /} $color/ ${fs_size /}
${alignr 40}Home $color1${fs_used /home/} $color/ ${fs_size /home/}

${alignr 50}$color1 ${voffset 30}${pre_exec cat /proc/cpuinfo | grep 'model name' | sort -u | cut -c14-33,44-60}
${alignr 60}$color1 Temperature $color ${exec sensors | grep 'Core 0' | awk '{print $3}' | cut -c2-9} / ${exec sensors | grep 'Core 1' | awk '{print $3}' | cut -c2-9},$color1 CPU $color ${cpu cpu0}%

${alignr 60}$color1 Critical Temperature $color ${exec sensors | grep 'Core 0' | awk '{print $6}' | cut -c2-9}

${alignr 80}${voffset 45}$color1 RAM $color ${memperc}%
${alignr 90}Processes ${processes}, Running ${running_processes}

${alignr 120}${voffset 45}$color1 ${upspeed eth0}$color Upload / $color1 ${upspeed eth0}$color Upload
${alignr 130}$color1 ${downspeed eth0}$color Download / $color1 ${downspeed eth0}$color Download

${alignr 140}Public IP $color1 ${exec wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]|.]//g'}$color
```

---

### Post by stinkeye on 2014-01-08
Last line in your config.
```
${alignr 140}Public IP $color1 ${**[COLOR="#FF0000"]exec[/COLOR]** wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]|.]//g'}$color
```

Your running the wget command every second.
Run each hour...
```
${alignr 140}Public IP $color1 ${**[COLOR="#FF0000"]execi 3600[/COLOR]** wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]|.]//g'}$color
```

Appears to be a fault in the original config.
You probably just didn't notice the cpu hogging before.

---

### Post by Habitual on 2014-01-08
> **stinkeye said:**
> Last line in your config.
```
${alignr 140}Public IP $color1 ${**[COLOR=#FF0000]exec[/COLOR]** wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]|.]//g'}$color
```

Your running the wget command every second.
Run each hour...
```
${alignr 140}Public IP $color1 ${**[COLOR=#FF0000]execi 3600[/COLOR]** wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]|.]//g'}$color
```

Appears to be a fault in the original config.
You probably just didn't notice the cpu hogging before.

If you just need your IP, try
```
curl icanhazip.com
```

---

### Post by stinkeye on 2014-01-08
> **Habitual said:**
> If you just need your IP, try
```
curl icanhazip.com
```
I like that one. Seems faster than "ifconfig.me".....
I also like the fact the creator of the site has a man page as his resume.
[http://majorhayden.com/](http://majorhayden.com/)

---

### Post by nonothing on 2014-01-08
You guys are awesome! Thank you so much. Honestly, I probably don't even need my IP--it was just a neat thing that was in the original and it looks cool. CPU temperature, UL/DL, and processes are the only important parts. Changing that update interval made it run perfect!

Not to be dumb, but where would I insert that curl command? Just replace the whole line? Also, do you think it would be of any benefit in general to change any of the other intervals, like the CPU temp? I want to clock to not jump around, but honestly most of the data doesn't really need to be to-the-second.

Anyway, thanks again I super appreciate it!

---

### Post by stinkeye on 2014-01-08
To use Habitual's curl command replace your last line with...
```
${alignr 140}Public IP $color1 ${[COLOR="#FF0000"]execi 3600 curl icanhazip.com[/COLOR]}$color
```

Test the command in terminal to check curl is installed (not included by default)...
```
curl icanhazip.com
```

To install curl via terminal....
```
sudo apt-get install curl
```

You only need to limit the **exec** commands as they use a lot more resources than the inbuilt conky variables.
You need the 1 second update_interval for the clock,cpu and net activity.

---

### Post by Habitual on 2014-01-09
Glad it worked out!

---

