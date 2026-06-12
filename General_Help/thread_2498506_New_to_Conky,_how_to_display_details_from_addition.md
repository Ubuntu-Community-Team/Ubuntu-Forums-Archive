---
title: "New to Conky, how to display details from additional hardware?"
date: 2024-06-16
forum: General Help
---

### Post by papriak on 2024-06-16
On Windows I used Rainmeter combined with HWinfo to show hardware loads, temperatures, and other data in real-time and as histograms on a second monitor.

Conky seems to be the app to use for this in Ubuntu, but I'm not familiar with it: nor am I seeing a way for it to be as descriptive on its own.

Will I need to add any other programs for it to display details from hardware such as my GPU, fans, and SSDs?

---

### Post by Frogs Hair on 2024-06-17
The syntax which is written to text document has many variables that can be add to display system information. If you are going to make your own or use a theme from the web to start you'll need two programs to start. ```
sudo apt install conky-all
``` ```
sudo apt install lm-sensors
```

I started with other users themes and modified them and even included weather. Below is a syntax I pieced together with my Nvidia card info. Conky manger is available for those who don't want to create themes .
[https://github.com/zcot/conky-manager2](https://github.com/zcot/conky-manager2)
  

```
--[[
# Theme        : based on Elegance-beam conky by capn-damo 
# Author    : Mixed
# License    : Distributed under the terms of GNU GPL version 2 or later
]]

conky.config = {
    alignment = 'top_right',
    background = false,
    border_inner_margin = 15,
    border_width = 5,
    default_color = 'ffffff',  --ffffff # white ffffff fffff ffffff ffffff ffffff
    double_buffer = true,
    draw_borders = false,
    draw_graph_borders = false,
    draw_outline = false,
    draw_shades = false,
    gap_x = 30,
    gap_y = 25,
    maximum_width = 320,
    double_buffer = true,
    override_utf8_locale = true,
    own_window = true,
    own_window_class = 'Conky',
    own_window_type = 'normal',
    own_window_transparent = true,
    own_window_hints = 'undecorated,below,skip_taskbar,skip_pager,sticky',
    own_window_argb_visual = true,
    own_window_argb_value = 150,
    text_buffer_size = 8000,
    total_run_times = 0,
    update_interval = 1,
    uppercase = false,
    use_xft = true,
    xftalpha = 1,
    short_units = false,
    font = 'sawasdee regular:style=Light:pixelsize=14',
    color1 = 'ffffff',
    color2 = 'ffffff',
    color3 = 'ffffff',
};

conky.text = [[
Time:${alignr}${time %H}${font}${time :%M}
Date:${alignr}${time %m-%d-%Y}${font}
$hr

Zorin:${alignr}17 Core
Linux:${alignr}${kernel}${color}
Uptime:${alignr}$uptime
CPU:${alignr}${cpu cpu}%
Ram: ${alignr}${mem} / ${memmax}
Swap: ${alignr}${swap} / ${swapmax}
Home:  ${alignr}${fs_used_perc /home}% / ${fs_size /home}
$hr
${font sawasdee regular:pixelsize=14}${alignr}${color3}
GPU:${alignr}${color #FFFFFF}${exec nvidia-smi --query-gpu=gpu_name --format=csv,noheader,nounits}
${color FFFFFF}${font}
Memory: $alignr ${nvidia memfreq} Mhz
Temperature: $alignr ${nvidia temp} C
NVidia GeForce GPU: $alignr ${nvidia gpufreq} Mhz
${color1}Vram Utilization: ${color} $alignr ${exec nvidia-smi | grep % | cut -c 37-40} MB
]];      

```

---

### Post by papriak on 2024-06-18
Is lm-sensors compatible with AMD video cards?

I tried using RadeonTop, but it needs prerequisites that I'm having trouble installing.

---

### Post by QIII on 2024-06-19
lm-sensors should give you information like this:

```
k10temp-pci-00c3
Adapter: PCI adapter
Tctl:         +54.9°C  
Tdie:         +27.9°C  
Tccd1:        +53.5°C  

amdgpu-pci-4300
Adapter: PCI adapter
vddgfx:        1.04 V  
fan1:         345 RPM  (min =    0 RPM, max = 3000 RPM)
edge:         +53.0°C  (crit = +104.0°C, hyst = -273.1°C)
PPT:          41.21 W  (cap = 180.00 W)

```

I think I also had to add psensor to get all of that.

Depending on your kernel/hardware, you can use a shell script like the following to get your activity percentage:

```

#!/bin/sh 

initial_value=$(cat /sys/kernel/debug/dri/0/amdgpu_pm_info | grep 'GPU\ Load' | cut -c10-17)
echo $initial_value

```

which I called AMDGPUActivity.sh and then add something like this to your conky:

```
${voffset -5}${goto 25}${color3}${font Liberation Mono:italic:size=11}${execi 600}GPU
${execi 600}${execi 600}Temp${goto 125}Fan${alignr 10}Load
${execi 1 sensors amdgpu-pci-4300 | grep edge: | cut -c15-23}${goto 90}${execi 1 sensors amdgpu-pci-4300 | grep fan1: | cut -c12-17}rpm${alignr}${execi 1 sensors amdgpu-pci-4300 | grep PPT: | cut -c14-19}W
${execi 1 /usr/bin/sudo sh /home/<my user>/.conky/AMDGPUActivity.sh}
```

You'll need to choose how to align things for your use.  I'd recommend against trying to add your password to the script and just deal with entering it when conky starts.

---

