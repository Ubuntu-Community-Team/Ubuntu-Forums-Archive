---
title: "Need some help with conky and setting a font/font size."
date: 2023-10-14
forum: General Help
---

### Post by ayesc0tty89 on 2023-10-14
My config:

```
conky.config = {
    double_buffer = true,
    no_buffers = true,

    own_window = false,
    own_window_type = 'desktop',
    own_window_transparent = true,
    own_window_hints = 'undecorated,sticky,skip_taskbar,skip_pager,below',

    update_interval = 1.0,
    net_avg_samples = 2,
    cpu_avg_samples = 2,

    alignment = 'top_right',
    gap_x = 30,
    gap_y = 30,
    
    default_color = 'white',
    default_outline_color = 'white',
    default_shade_color = 'black',
    color0 = 'ffffff',
    color1 = 'b3e5fc',
    color2 = '4783fc'
}

conky.text = [[
${font :size=36}
${font}${voffset -20}${alignc}${time %A %d %B %Y}
${alignc}${nodename}@${top user 1}
${color2}${hr 2}
${color}Kernel: ${alignr}${kernel}
Distro: ${alignr}${execi 6000 lsb_release -d | grep 'Descr'|awk {'print $2 " " $3" " $4"" $5'}}
Battery: ${alignr}${battery_bar 5, 50} ${battery_percent}%
#------------+
#TEMPS
#------------+
${color2}TEMPS ${hr 2}
${color0}${voffset 5}CPU: ${alignr}${execi 5 sensors | grep Tctl: | cut -c 16-19}°C
${color0}${voffset 5}SSD: ${alignr}${execi 5 sensors | grep Composite: | cut -c 16-19}°C
${color0}${voffset 5}GPU: ${alignr}${execi 5 sensors | grep edge: | cut -c 16-19}°C
${color0}${voffset 5}GPUJunction: ${alignr}${execi 5 sensors | grep junction: | cut -c 16-19}°C
${color0}${voffset 5}GPUMem: ${alignr}${execi 5 sensors | grep mem: | cut -c 16-19}°C
#------------+
#CPU
#------------+
${color2}Ryzen 5600X SixCore 4.65GHZ ${hr 2}
${color0}${voffset 5}Name: $alignr${execi 6000 cat /proc/cpuinfo | grep 'model name' | sed -e 's/model name.*: //'| uniq | cut -c 1-16}
Freq: ${alignr}${freq_g} GHz
Usage: ${alignr}${cpu}%
${cpugraph 32}
#------------+
#GPU
#------------+
${color2}MSI Gaming X 6650XT 8GB ${hr 2}
${color0}Name: Navi23 ${alignr}${exec nvidia-smi --query-gpu=gpu_name --format=csv,noheader,nounits}
Usage: ${alignr}${execi 5 radeontop -d- -l1 | grep -o 'gpu [0-9]\{1,3\}' | cut -c 5-7 }
Fan Speed: ${alignr}${execi 5 sensors | grep fan1 | cut -c 16-19 }PM
#------------+
#MEMORY
#------------+
${color2}MEMORY 16GB DDR4 3200MHZ ${hr 2}
${color0}${voffset 5}Used: ${mem} ($memperc%)${alignr}Free: ${memeasyfree}
#------------+
#NETWORK
#------------+
${color2}NETWORK ${hr 2}
${color0}${voffset 5}${addr enp5s0}${alignr}${if_existing /sys/class/net/enp5s0/operstate up}ONLINE${else}OFFLINE${endif}
Established: ${goto 345}${execi 5 netstat -tuapn | grep -iE 'established' | wc -l}
Signal: ${alignr}${color lightgrey}${wireless_link_bar 4,140 wlan0}  ${wireless_link_qual wlan0}%
Down: ${downspeed wlan0}/s  ${alignr} Total: ${totaldown wlan0}
${downspeedgraph wlan0 30}
Up: ${upspeed wlan0}/s      ${alignr} Total: ${totalup wlan0}
${upspeedgraph wlan0 30 }
#------------+
#FS
#------------+
${color2}Kingston A400 960GB Sata SSD ${hr 2}
${color0}${voffset 5}/dev/nvme0n1p6:${alignr}${fs_used /} / ${fs_size /}
${fs_bar  /}
Read: ${alignr}${diskio_read /dev/nvme0n1p6}
Write: ${alignr}${diskio_write /dev/nvme0n1p6}
#------------+
#PROCESSES
#------------+
${color2}PROCESS ${hr 2}
${color0}Name${goto 215}MEM%${alignr}CPU%
${color1}${top name 1}${goto 200}${top mem 1}${alignr}${top cpu 1}
${color1}${top name 2}${goto 200}${top mem 2}${alignr}${top cpu 2}
${color1}${top name 3}${goto 200}${top mem 3}${alignr}${top cpu 3}
${color1}${top name 4}${goto 200}${top mem 4}${alignr}${top cpu 4}
${color1}${top name 5}${goto 200}${top mem 5}${alignr}${top cpu 5}
${color1}${top name 6}${goto 200}${top mem 6}${alignr}${top cpu 6}${voffset 10}
${color0}Processes: ${alignr}${processes} (${running_processes})
${color0}Threads: ${alignr}${threads} (${running_threads})
#------------+
#DEVICES
#------------+
${color2}DEVICES ${hr 2}
${color1}${execi 1800 sudo nmap -sP 192.168.1.1/24 | grep  "Nmap scan report for" | awk -F ' '  '{print $5, $6}'} 
]]
```

Problem: When I try and set a font, it says it can't detect it. No such location. So I add: use_xft = true and I get a "mem" on the left side of my screen when there's nothing there.

Please help! I'm pulling my hair out!!!!!!!

edit: For anyone else: My MEM was wrong. Edited and now:

```
conky.config = {
    double_buffer = true,
    no_buffers = true,
    use_xft = true,
    uppercase = true,
    font = 'feather:size=10',

    own_window = false,
    own_window_type = 'desktop',
    own_window_transparent = true,
    own_window_hints = 'undecorated,sticky,skip_taskbar,skip_pager,below',

    update_interval = 1.0,
    net_avg_samples = 2,
    cpu_avg_samples = 2,

    alignment = 'top_right',
    gap_x = 30,
    gap_y = 30,
    
    default_color = 'white',
    default_outline_color = 'white',
    default_shade_color = 'black',
    color0 = 'ffffff',
    color1 = 'b3e5fc',
    color2 = '4783fc'
};

conky.text = [[
${font}${voffset -20}${alignc}${time %A %d %B %Y}
${alignc}${nodename}@${top user 1}
${color2}${hr 2}
${color}Kernel: ${alignr}${kernel}
Distro: ${alignr}${execi 6000 lsb_release -d | grep 'Descr'|awk {'print $2 " " $3" " $4"" $5'}}
Battery: ${alignr}${battery_bar 5, 50} ${battery_percent}%
#------------+
#MyCPU
#------------+
${color2}CPU: Ryzen 5600X 4.65GHz ${hr 2}
${color0}${voffset 5}Name: $alignr${execi 6000 cat /proc/cpuinfo | grep 'model name' | sed -e 's/model name.*: //'| uniq | cut -c 1-16}
Freq: ${alignr}${freq_g} GHz
Usage: ${alignr}${cpu}%
${cpugraph 32}
#------------+
#MyGPU
#------------+
${color2}GPU: MSI 6650XT 8GB GDRR6 ${hr 2}
${color0}Name: GamingPC ${alignr}${exec nvidia-smi --query-gpu=gpu_name --format=csv,noheader,nounits}
Usage: ${alignr}${execi 5 radeontop -d- -l1 | grep -o 'gpu [0-9]\{1,3\}' | cut -c 5-7 }
Fan Speed: ${alignr}${execi 5 sensors | grep fan1 | cut -c 16-19 }PM
#------------+
#MyRAM
#------------+
${color2}RAM: 16GB DDR4 3200MHZ ${hr 2}
${color0}${voffset 5}Used: ${mem} ($memperc%)${alignr}Free: ${memeasyfree}
$processes processes ($running_processes running)
#------------+
#FileSystem
#------------+
${color2}SSD: Kingston A400 960GB SATA ${hr 2}
${color0}${voffset 5}/dev/sda3:${alignr}${fs_used /} / ${fs_size /}
${fs_bar  /}
Read: ${alignr}${diskio_read /dev/nvme0n1p6}
Write: ${alignr}${diskio_write /dev/nvme0n1p6}
#------------+
#MyNETWORK
#------------+
${color2}MyNetworkAddress ${hr 2}
${color0}${voffset 5}${addr enp5s0}${alignr}${if_existing /sys/class/net/enp5s0/operstate up}ONLINE${else}OFFLINE${endif}
Established: ${goto 345}${execi 5 netstat -tuapn | grep -iE 'established' | wc -l}
Signal: ${alignr}${color lightgrey}${wireless_link_bar 4,140 wlan0}  ${wireless_link_qual wlan0}%
Down: ${downspeed wlan0}/s  ${alignr} Total: ${totaldown wlan0}
${downspeedgraph wlan0 30}
Up: ${upspeed wlan0}/s      ${alignr} Total: ${totalup wlan0}
${upspeedgraph wlan0 30 }
#------------+
#MyTemps
#------------+
${color2}MyTemps ${hr 2}
${color0}${voffset 5}CPU: ${alignr}${execi 5 sensors | grep Tctl: | cut -c 16-19}°C
${color0}${voffset 5}SSD: ${alignr}${execi 5 sensors | grep Composite: | cut -c 16-19}°C
${color0}${voffset 5}GPU: ${alignr}${execi 5 sensors | grep edge: | cut -c 16-19}°C
${color0}${voffset 5}GPUJunction: ${alignr}${execi 5 sensors | grep junction: | cut -c 16-19}°C
${color0}${voffset 5}GPUMem: ${alignr}${execi 5 sensors | grep mem: | cut -c 16-19}°C
#------------+
#Devices
#------------+
${color2}MyDevices ${hr 2}
${color1}${execi 1800 sudo nmap -sP 192.168.1.1/24 | grep  "Nmap scan report for" | awk -F ' '  '{print $5, $6}'} 
]]
```

It works!

---

