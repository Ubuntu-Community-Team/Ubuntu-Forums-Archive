---
title: "[SOLVED] conky configuration"
date: 2007-10-05
forum: General Help
---

### Post by AnLGP on 2007-10-05
I see all these conky configurations.  I enjoy a lot of the ones I've seen yet I would *much rather* configure one myself from scratch to make it just the way I want it.  Can someone give me a few tips, point me in the right direction, etc.?  I've google searched 'conky configuration', 'how to configure conky', etc. all and it seems to come back to the 'post your .conkyrc files w/screenshots'.  Which is fine if you just want to go through and pick one.

I have [this]("http://www.gnome-look.org/CONTENT/content-pre1/21957-1.jpg") as my background and would like it to look nice with that.

I'm running Ubuntu 7.04 and installed conky via the synaptic package manager if that gives you any idea what version I am running.

Thanks.

---

### Post by matthew on 2007-10-05
Start here: [http://conky.sourceforge.net/](http://conky.sourceforge.net/)

These sub-pages will be helpful:
[http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)
[http://conky.sourceforge.net/config_settings.html](http://conky.sourceforge.net/config_settings.html)

---

### Post by AnLGP on 2007-10-05
Thanks.  

Can one configure these in any order one wants?

---

### Post by AnLGP on 2007-10-05
Double post.

---

### Post by matthew on 2007-10-05
> **AnLGP said:**
> Thanks.  

Can one configure these in any order one wants?Yes.

---

### Post by AnLGP on 2007-10-05
[screenshot]("http://i65.photobucket.com/albums/h235/themangoduck/Screenshot-3.png")

how do I change the window to be transparent and get the font so not messed up at the bottom?

here's my conkyrc

# set to yes if you want Conky to be forked in the background
background yes

# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
font 9x15
#font *mintsmild.se*
#font -*-*-*-*-*-*-35-*-*-*-*-*-*-*

# Use Xft?
use_xft no

# Set conky on the bottom of all other applications
#on_bottom yes

# Xft font when Xft is enabled
#xftfont Bitstream Vera Sans Mono:size=10

# Text alpha when using Xft
#xftalpha 0.15

# Print everything to stdout?
# out_to_console no

# MPD host/port
# mpd_host localhost
# mpd_port 6600
# mpd_password tinker_bell

# Print everything to console?
# out_to_console no

# mail spool
#mail_spool $MAIL

# Update interval in seconds
update_interval 5.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes

# If own_window is yes, you may use type normal, desktop or overide
own_window_type desktop

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window is yes, these window manager hints may be used
own_window_hints undecorated,below,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer no

# Minimum size of text area
minimum_size 280 5

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 8 no

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color white

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
#alignment bottom_left
alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 12
gap_y 28

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase yes

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no


# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer no

#   mldonkey_hostname     Hostname for mldonkey stuff, defaults to localhost
#   mldonkey_port         Mldonkey port, 4001 default
#   mldonkey_login        Mldonkey login, default none
#   mldonkey_password     Mldonkey password, default none

# boinc (seti) dir
# seti_dir /opt/seti
machine

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen

TEXT
           $sysname $kernel on $machine

${color}Uptime:$color $uptime ${color}- Load:$color $loadavg
${color}CPU Usage:${color} $cpu% ${cpubar}
${color}${cpugraph 88aadd 88aaee}



${color}RAM Usage:$color $mem/$memmax - $memperc% ${membar}
${color}Swap Usage:$color $swap/$swapmax - $swapperc% ${swapbar}
${color}Processes:$color $processes  ${color}Running:$color $running_processes

${color}Networking:
 Down:${color} ${downspeed eth0} k/s${color} ${offset 80}Up:${color} ${upspeed eth0} k/s
${color}${downspeedgraph eth0 32,150 88aadd 88aaee} ${color}${upspeedgraph eth0 32,150 88aadd 88aaee}

${color}File systems:
 / $color${fs_used /}/${fs_size /} ${fs_bar /}
 /home $color${fs_used /home}/${fs_size /home} ${fs_bar /home}

${color}Name             PID     CPU%   MEM%
${color lightgrey} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}
${color}Mem usage
${color lightgrey} ${top_mem name 1} ${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
${color} ${top_mem name 2} ${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
${color} ${top_mem name 3} ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}

---

### Post by matthew on 2007-10-06
I'm not a conky expert, but I like to play with it. Try changing this:

```
 # Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer no
```to this
```
 # Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer yes
```and see if that helps.

---

### Post by AnLGP on 2007-10-07
Thanks, that made it look nice!

---

### Post by jolly79 on 2007-10-11
Hi

Your conky looks kinda like the one i piecede together... (stole alittle bit from some configs here on the forum)

Your welcome to steal some of the code if you can use it ;-)

Follow this link: [http://www.superchristensen.com/modules/tinycontent/index.php?id=3](http://www.superchristensen.com/modules/tinycontent/index.php?id=3)


Cheers 

From Gustav

---

### Post by rjmdomingo2003 on 2007-10-11
> **AnLGP said:**
> [screenshot]("http://i65.photobucket.com/albums/h235/themangoduck/Screenshot-3.png")

how do I change the window to be transparent..

# Create own window instead of using desktop (required in nautilus)
own_window yes

Change to:
```
own_window no
```
for a transparent window.

Try changing the default font color to ABABAB if you like a good contrast. For good-looking fonts: dafont.com.

---

