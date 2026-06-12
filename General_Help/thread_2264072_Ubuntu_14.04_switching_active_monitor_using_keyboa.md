---
title: "Ubuntu 14.04 switching active monitor using keyboard"
date: 2015-02-05
forum: General Help
---

### Post by superusek on 2015-02-05
I'm struggling with it for some time and still have no solution. I've got default monitor under HDMI1 (1680x1050) and projector for watching movies on HDMI2 (1280x720). I tried to use xrandr and made two files in my home/scripts/: 

dvionly.sh
```
#!/bin/bash
xrandr --output HDMI1 --auto --output HDMI2 --off

```

and hdmionly.sh
```
#!/bin/bash
xrandr --output HDMI1 --off --output HDMI2 --auto

```It was working bot not always - very annoying. Especially recently, when I just couldn't turn off projector and turn on monitor - projector was always back on and monitor stays off. Different kind of strange behaviours noticed previously.


Also tried arandr but it's actually xrandr under the gui so didn't work either. The only always-working solution is to use Displays dialog from Ubuntu but I guess it's obvious that's not a handy solution. Any idea how to do it?


PS. I've got Asus H81M-Plus Motherboard / Pentium G3258 with integrated GPU only. In bios - I have enabled Intel Virtualization Technology (basically only change I made in BIOS).

---

