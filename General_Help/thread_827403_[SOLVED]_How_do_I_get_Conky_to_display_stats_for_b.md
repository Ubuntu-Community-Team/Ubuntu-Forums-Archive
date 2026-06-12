---
title: "[SOLVED] How do I get Conky to display stats for both my CPU cores?"
date: 2008-06-12
forum: General Help
---

### Post by ChildOfMana on 2008-06-12
I'm running an Intel Pentium Dual Core E2180 CPU in my new rig. I've installed conky but it doesn't seem to be picking up on my CPU's second core. Anyone know how I can make it do this?

This isn't exactly a major problem but it is an annoyance.

Here's my conkyrc file:

> background yes
use_xft no
update_interval 1.0
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 250 5
maximum_width 250
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color white
default_shade_color red
default_outline_color green
alignment top_right
gap_x 12
gap_y 48
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no
use_spacer yes

TEXT
$alignc ${time %H:%M.%S} / ${utime %R} (UTC)
$alignc ${time %a, %d %b %Y}
${color orange}${hr 2}$color
$alignc $sysname $kernel on $machine
$alignc Uptime: $uptime

${color orange}Processor ${hr 2}${color }
${tab 20}Intel Pentium DualCore E2180
${color lightgrey}${tab 20}Load: ${color #ddaa00}${cpu cpu0}% ${color }${cpubar cpu0 6}
${cpugraph cpu0 10,150 000F83 B0B6E3}   ${freq_g cpu0}Ghz
	
${color orange}${tab 20}Top CPU: $alignr PID   CPU%
${color #ddaa00}${tab 40}${top name 1}$alignr${top pid 1} ${top cpu 1}
${color }${tab 40}${top name 2}$alignr${top pid 2} ${top cpu 2}
${color }${tab 40}${top name 3}$alignr${top pid 3} ${top cpu 3}
${color }${tab 40}${top name 4}$alignr${top pid 4} ${top cpu 4}
${color }${tab 40}${top name 5}$alignr${top pid 5} ${top cpu 5}
${color }${tab 40}${top name 6}$alignr${top pid 6} ${top cpu 6}

${color orange}Memory ${hr 2}
${color }${tab 20}Ram:  ${mem} / ${memmax} 
${color lightgrey}${tab 30}Used: ${color #ddaa00}${memperc}%${alignr}${color }${membar 6, 150}
${color }${tab 20}Swap:  ${swap} / ${swapmax}
${color lightgrey}${tab 30}Used:  ${color #ddaa00}${swapperc}%${alignr}${color }${swapbar 6, 150}

${color orange}${tab 20}Top Memory: $color $alignr PID   MEM%
${color #ddaa00}${tab 40}${top_mem name 1}$alignr${top_mem pid 1}  ${top_mem mem 1}
${color }${tab 40}${top_mem name 2}$alignr${top_mem pid 2}  ${top_mem mem 2}
${color }${tab 40}${top_mem name 3}$alignr${top_mem pid 3}  ${top_mem mem 3}
${color }${tab 40}${top_mem name 4}$alignr${top_mem pid 4}  ${top_mem mem 4}
${color }${tab 40}${top_mem name 5}$alignr${top_mem pid 5}  ${top_mem mem 5}
${color }${tab 40}${top_mem name 6}$alignr${top_mem pid 6}  ${top_mem mem 6}

${color orange}Linux Space ${hr 2}$color
/ $alignc ${fs_used /} / ${fs_size /} $alignr Free: ${fs_free_perc /}%
${fs_bar /}
/home $alignc ${fs_used /home} / ${fs_size /home} $alignr Free: ${fs_free_perc /home}%
${fs_bar /home}

${color orange}Network (${addr eth0}) ${hr 2}$color
Down: ${color #ddaa00}${downspeedf eth0}k/s ${color }${alignr}Up: ${color #ddaa00}${upspeedf eth0}k/s$color
${color dark green}${downspeedgraph eth0 9,125 000000 000000} ${alignr}${color dark red}${upspeedgraph eth0 9,125 000000 000000}$color
${tab 20}Total: ${totaldown eth0}          Total: ${totalup eth0}

${color orange}Messages Log ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | fold -w50}

${color orange}Auth log ${hr 2}$color
${execi 30 tail -n3 /var/log/auth.log | fold -w50}

Thanks.

---

### Post by cammin on 2008-06-12
cpu1 should be core 2
So copy what you have for the first core, then change the instances of **cpu0** to **cpu1** for that section.

---

### Post by ChildOfMana on 2008-06-13
Awesome, it worked.

Thank you. :)

---

