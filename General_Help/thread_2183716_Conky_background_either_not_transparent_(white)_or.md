---
title: "Conky background either not transparent (white) or bordered."
date: 2013-10-26
forum: General Help
---

### Post by DuckHook on 2013-10-26
Hi all,

Conky is misbehaving on a fresh pristine install of Ubuntu 13.10 but with inherited /home directory. I've tried fiddling with setting:

own_window_type to "normal", "override" and "desktop"

"override" yields white background -- not transparent, even though transparency is set to "on".
"desktop" yields good result until I open another window, at which point, conky display disappears entirely (though ps -ef shows it still running as a process)
"normal" yields least objectionable result. At lease conky doesn't disappear, but this option produces thin dark borders (1 pixel) around the conky box.

no_buffers "yes" makes conky display disappear after opening another window
setting to "no" seems to stabilize display

syslog, dmesg, xorg.log and kern.log show nothing suspicious.

Current conky settings are:```
# Conky settings #
background no
update_interval 1

cpu_avg_samples 2
net_avg_samples 2

override_utf8_locale yes

double_buffer yes
no_buffers no

text_buffer_size 2048
#imlib_cache_size 0

# Window specifications #

own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below

# border_inner_margin 0
# border_outer_margin 0

minimum_size 200 250
maximum_width 200

alignment tr
gap_x 35
gap_y 55

# Graphics settings #
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no

# Text settings #
use_xft yes
xftfont caviar dreams:size=8
xftalpha 0.5

uppercase no
```

I'm willing to live with thin black borders if there is no other solution, but would like to get rid of them for aesthetic reasons. Conky display was good in 12.04

Both Google and prior threads suggest twiddling with Conky's parameters which I have done with varying degrees of success as described above. System description is:

Dell Latitude D830
CPU Intel dual-core w/ 8GB DRAM
GPU Quadro NVS 140M w/ 256 MB dedicated VRAM
Outputting to external HP w2408 monitor DVI-out to DVI-in directly
Proprietary nVidia driver version 319.32

All suggestions most appreciated.

---

### Post by deadflowr on 2013-10-26
Sometimes if you add these two lines it can give transparency

```
own_window_argb_visual yes
own_window_argb_value 255
```

---

### Post by DuckHook on 2013-10-26
Thanks deadflower. Will try this as soon as I get home.

---

### Post by DuckHook on 2013-10-26
@deadflowr

You are a rock star. These settings did the trick. I now have transparency with no border artifacts. Voila. Marking this "solved", and thanks for the help.

---

### Post by deadflowr on 2013-10-26
Thank VinDSL, among others.:D

---

