---
title: "beryl and conky, no go"
date: 2007-08-29
forum: General Help
---

### Post by tronica on 2007-08-29
I have beryl running along with conky, I add stuff to make it not flicker and smudge, But now it will be on for 20 seconds, and then go off for 20 seconds, over and over. is there anything i can do to stop that. heres my conkyrc

> background yes
use_xft yes
xftfont HandelGotD:size=2
xftalpha 0.1
font Sans:size=8
update_interval 1.5
total_run_times 0
own_window no
own_window_type override
own_window_transparent 1
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 210 5
maximum_width 210
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders yes
default_color white
default_shade_color red
default_outline_color green
alignment bottom_right
gap_x 18
gap_y 48
no_buffers yes
uppercase no
cpu_avg_samples 2
net_avg_samples 1
override_utf8_locale no
use_spacer yes

TEXT
${font Sans:bold:size=8}${color #0077ff}CPU$font$color  ${hr 1}
   $alignc ${color #0077ff}AMD 5200+ X2$color
   ${freq_g 1}GHz ${cpu cpu1}% ${cpubar cpu1}
   ${freq_g 2}GHz ${cpu cpu2}% ${cpubar cpu2}
   ${color #0077ff}Top Processes$alignr -PID-     CPU     MEM$color
   ${top name 1}$alignr${top pid 1}${top cpu 1}   ${top mem 1}
   ${top name 2}$alignr${top pid 2}${top cpu 2}   ${top mem 2}
   ${top name 3}$alignr${top pid 3}${top cpu 3}   ${top mem 3}

${font Sans:bold:size=8}${color #0077ff}RAM / HD$font  $color${hr 1}
   ${color #0077ff}RAM$color $alignc $mem / $memmax $alignr$memperc%
   $membar
   ${color #0077ff}Disk Space$color $alignc ${fs_used /} / ${fs_size /} $alignr${fs_free_perc /} %
   ${fs_bar /}
   ${color #0077ff}Disk Space$color $alignc ${fs_used /media/Storage} / ${fs_size /media/Storage} $alignr${fs_free_perc /media/Storage} %
   ${fs_bar /media/Storage}	
   ${color #0077ff}HD I/O $color  ${diskiograph 19}
${font Sans:bold:size=8}${color #0077ff}Network$font  $color${hr 1}
   ${color #0077ff}IP: $color${addr eth0}
   ${color #0077ff}Down: ${color white}${downspeed eth0}k/s ${alignr}${color #0077ff}Up: ${color white}${upspeed eth0}k/s
   ${downspeedgraph eth0 25,100} ${alignr}${upspeedgraph ath0 
25,100}
   ${color #0077ff}Total: ${color white}${totaldown eth0} ${alignr}${color #0077ff}Total:  ${color white}${totalup eth0}
   ${color #0077ff}Inbound: ${color white}${tcp_portmon 1 32767 count}$alignr${color #0077ff}Outbound: ${color white}${tcp_portmon 32768 
61000 count}
${tcp_portmon 32768 61000 rhost 0} ${alignr} ${tcp_portmon 32768 61000 rservice 0}
${tcp_portmon 32768 61000 rhost 1} ${alignr} ${tcp_portmon 32768 61000 rservice 1}
${tcp_portmon 32768 61000 rhost 2} ${alignr} ${tcp_portmon 32768 61000 rservice 2}
${tcp_portmon 32768 61000 rhost 3} ${alignr} ${tcp_portmon 32768 61000 rservice 3}
${tcp_portmon 32768 61000 rhost 4} ${alignr} ${tcp_portmon 32768 61000 rservice 4}
${tcp_portmon 32768 61000 rhost 5} ${alignr} ${tcp_portmon 32768 61000 rservice 5}

---

### Post by por100pre1 on 2007-08-29
Did you try [this]("http://conky.sourceforge.net/faq.html")?

> 
Q: Conky won't stop flickering

A: Conky is designed to draw to the root desktop window. However, there are several other applications which like drawing to the root desktop window. Because of this, Conky has two options available to get around this problem:

    * You can try enabling double-buffer. Conky's double-buffer option uses the X double-buffer extension to provide a flicker-free Conky. This can be done by running Conky with the '-b' parameter, or adding this to your conkyrc:double_buffer yes
    * Conky can run in windowed mode, meaning that instead of drawing the the root window it draws to it's own window. You can move this window around and resize it by right-clicking or left-clicking on the window while holding down the Alt key. This can be accomplished by running Conky with the '-o' parameter, or by adding the following to your conkyrc: own_window yes


Q: Double buffer isn't working!

A: More than likely you aren't loading the double buffer extension when Xorg starts. Luckily, its easy to fix. Open up the Xorg configuration file (usually /etc/X11/xorg.conf) with your favourite text editor, and find the line that says:
Section "Module"
Then, after that line, add:
Load "dbe"
Restart Xorg (my preferred method is the good-ole control + alt + backspace) and enjoy.



---

### Post by tronica on 2007-08-29
i added dbe, and now my desktop icons disappear, but conky works fine.

---

### Post by orb9220 on 2007-08-29
Same problem for me ended with:

> own_window yes
own_window_transparent yes
own_window_type root
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer Yes

Now works on mine fine.

---

### Post by tronica on 2007-08-29
orb9220, that worked perfectly, thanks for the help.

---

