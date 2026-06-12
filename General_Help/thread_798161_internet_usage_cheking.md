---
title: "internet usage cheking"
date: 2008-05-17
forum: General Help
---

### Post by chaitu407 on 2008-05-17
hi iam new to ubuntu my broadband connect has limited usage 2.5 gb per month i want to check how much data is transfered in both downstream and upstreams in a session so plsss any one help me how to check the usageee

more over also tell me how to estabish and disconnet the connection    with userid and password

---

### Post by empthollow on 2008-05-17
I am not super familiar with this but netstat should give you that info.  netstat has a very large amount of options so it may require a bit of research.  A good place to start would be 
```
netstat -s
```
that will probably give you more than you wanted to know but your info should be in there.

An easier option might be the system monitor available in system -> administration -> system monitor.  That will give you current stats although i'm not sure exactly what timeframe it uses.

I'm not sure how to set connectivity with username and password other than giving certain users the privileges to the network card, but that poses a problem for offline work. You can always right click on the network icon and uncheck the enable networking box but that is not password protected.

Hope that info is at least a little useful.  What type of internet service do you have by the way?

---

### Post by chaitu407 on 2008-05-17
> **empthollow said:**
> I am not super familiar with this but netstat should give you that info.  netstat has a very large amount of options so it may require a bit of research.  A good place to start would be 
```
netstat -s
```
that will probably give you more than you wanted to know but your info should be in there.

An easier option might be the system monitor available in system -> administration -> system monitor.  That will give you current stats although i'm not sure exactly what timeframe it uses.

I'm not sure how to set connectivity with username and password other than giving certain users the privileges to the network card, but that poses a problem for offline work. You can always right click on the network icon and uncheck the enable networking box but that is not password protected.

Hope that info is at least a little useful.  What type of internet service do you have by the way?


mine is pppoe connection

---

### Post by chaitu407 on 2008-05-17
the command is for only packets but not no of bytes received please check out

---

### Post by empthollow on 2008-05-18
you can do:
```
netstat -s | grep bytes
```
and it will show number of bytes recieved however i don't know from what time frame.

---

### Post by noremac on 2008-05-18
I would highly recommend setting up a simple conky

Very simple step by step instructions:

First in terminal,

```
sudo apt-get install conky
```

then edit the config file by (and put in your username of course, not "username")

```
gedit /home/"username"/conkyrc
```

Then you just need to copy and paste this into the file:

```

background yes
font Zekton:size=7
xftfont Zekton:size=7
use_xft yes
xftalpha 0.1
update_interval 1.0
total_run_times 0
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
minimum_size 220 5
maximum_width 220
default_color d7d7d7
default_shade_color black
default_outline_color black
alignment top_right
gap_x 2
gap_y 10
no_buffers yes
cpu_avg_samples 2
override_utf8_locale no
uppercase no # set to yes if you want all text to be in uppercase
use_spacer no

TEXT
${font Zekton:style=Bold:pixelsize=42}${alignc}${time %H:%M:%S}${font Zekton:size=7}

Down ${downspeed eth0} k/s ${alignr}Up ${upspeed eth0} k/s
${downspeedgraph eth0 25,107} ${alignr}${upspeedgraph eth0 25,107}
Total ${totaldown eth0} ${alignr}Total ${totalup eth0}

```

Save that, then in terminal, simply type "conky" and you should see the usage since the computer was turned on. Along with that, a clock which you can easily get rid of and a graph of your recent history, which you could also get rid of. But with such strict bandwidth, it might be nice to be able to keep track of your network incase something is using it without you knowing.

-C

---

