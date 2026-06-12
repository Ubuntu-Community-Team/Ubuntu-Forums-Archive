---
title: "How can I auto-stop conky at shut down?"
date: 2014-10-10
forum: General Help
---

### Post by Al1000 on 2014-10-10
Hi,

I have conky on auto-start, but sometimes when I reboot my computer I find that I end up with more than one conky running. This seems to be down to conky not stopping properly when the computer is shutting down, because if I open a terminal and kill conky before restarting, this doesn't happen.

I have got around this problem by editing the script in the conky start file in ~/.config/autostart to:

```
sleep 10 && killall conky && sleep 1 && conky
```

...but would ideally like to ensure it shuts down properly when the computer shuts down, without having to do so manually.

Is this possible to do, and if so, how would I go about it?

---

### Post by vasa1 on 2014-10-10
I had this happen to me recently. I thought a reboot would take care of things but it didn't. Anyway, once I fixed my conky script that stopped happening so maybe you could share your script so that experts here could help you troubleshoot it.

---

### Post by Al1000 on 2014-10-10
Certainly. 

This is /etc/conky/conky.conf

```
alignment top_right
background true
border_width 1
cpu_avg_samples 2
default_color green
default_outline_color white
default_shade_color white
draw_borders no
draw_graph_borders no
draw_outline no
draw_shades no
use_xft yes
xftfont Bitstream Vera Sans Mono:size=10
gap_x 5
gap_y 110
minimum_size 5 5
net_avg_samples 2
double_buffer yes
out_to_console no
own_window yes
own_window_argb_visual yes
own_window_argb_value 100
own_window_transparent yes
own_window_type normal
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
stippled_borders 0
update_interval 03.0
uppercase no
use_spacer none
show_graph_scale no
show_graph_range no

TEXT
${color}${scroll 16 $nodename - $sysname $kernel on $machine | }
${color white}$hr
${color}Uptime:$uptime
${color white}$hr
${color}RAM Usage:$mem/$memmax - $memperc% ${membar 7}
Swap Usage:$swap/$swapmax - $swapperc% ${swapbar 7}
${color white}$hr
${color}CPU 1: ${cpu cpu1}% ${cpubar cpu1}
CPU 2: ${cpu cpu2}% ${cpubar cpu2}
Frequency: ${freq}MHz
CPU 1 Temp: ${hwmon 1 temp 1}C    CPU 2 Temp: ${hwmon 2 temp 1}C
${color white}$hr
${color}File systems: ${fs_free /}/${fs_size /} ${fs_bar 6 /}
${color white}$hr
${color}Networking:
Up:${upspeed eth1}k/s       Down:${downspeed eth1}k/s
${color white}$hr
${color}Processes:$processes     Running:$running_processes
${color white}$hr
${color}Name              PID    CPU%   MEM%
${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}
${top name 5} ${top pid 5} ${top cpu 5} ${top mem 5}

```

---

### Post by ajgreeny on 2014-10-10
In your startup applications listing rather than simply ```
conky
```in the command box, if that's what you are using, try ```
conky -p 10
```to delay start by 10 seconds.

I don't really know KDE very well but also check that the previous session is not saved for use when restarting as that may give you the two running versions; the first from previous session and the second from your startup applications list.

---

### Post by Al1000 on 2014-10-10
Thanks for the response. I am now using the code I posted in the OP to start conky, and I had previously tried using the pause argument instead of the sleep command to delay conky starting, but it didn't make any difference.

> also check that the previous session is not saved for use when restarting

How would I go about doing that?

Just in case it matters, here is the auto-start file, which was created by the system - I have only edited the command.

```
al@my_desktop_pc:~/.config/autostart$ cat conky.desktop 
[Desktop Entry]
Comment[en_GB]=
Comment=
Exec=sleep 10 && killall conky && sleep 1 && conky
GenericName[en_GB]=
GenericName=
Icon=system-run
MimeType=
Name[en_GB]=
Name=
Path=
StartupNotify=true
Terminal=false
TerminalOptions=
Type=Application
X-DBUS-ServiceName=
X-DBUS-StartupType=
X-KDE-SubstituteUID=false
X-KDE-Username=

```

This is all on my desktop pc running Kubuntu 14.04

I also have conky autostarting on Kubuntu 12.04 on my laptop, and use a much simpler file to start it that I created manually, at ~/.config/autostart/conky.sh

```
#!/bin/bash
sleep 10 && conky;
```

...which I tried on Kubuntu 14.04 on my desktop pc, but for some reason it didn't work on it, so I just went with the file that the system created instead.

---

### Post by deadflowr on 2014-10-10
If KDE, it might be set to restore session.
I would dig through the system settings to see.
More, maybe
[https://userbase.kde.org/System_Settings/Startup_and_Shutdown](https://userbase.kde.org/System_Settings/Startup_and_Shutdown)

---

### Post by Al1000 on 2014-10-10
> If KDE, it might be set to restore session.

That did the trick! I hadn't imagined that such a setting would exist.

I found 'session management' in system settings, and an option that was set to 'restore previous session' on log-in, which I changed to 'start with an empty session.'

Many thanks for your help.

---

### Post by ajgreeny on 2014-10-10
> **Al1000 said:**
> That did the trick! I hadn't imagined that such a setting would exist.

I found 'session management' in system settings, and an option that was set to 'restore previous session' on log-in, which I changed to 'start with an empty session.'

Many thanks for your help.
Great!

That was precisely what I was suggesting but I didn't know how to get to the startup applications in KDE.

---

### Post by Al1000 on 2014-10-11
Yep, I can now see that you were suggesting the same thing; it's just that I didn't know anything about sessions being saved to restart again. I am relatively new to Linux so still have much to learn.

I checked Kubuntu 12.04 on my (old and slow) laptop as well, and found that it was also set to restore the previous session (although for some reason I didn't have the same problem on it with conky), so I take it that this must be the default setting on Kubuntu. It certainly shuts down a lot faster now that I've also set it to 'start with an empty session,' as it's presumably no longer saving the previous one at shutdown.

---

