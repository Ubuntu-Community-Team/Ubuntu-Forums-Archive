---
title: "Stop Monitor Going to Sleep whilst watching Youtube"
date: 2013-10-27
forum: General Help
---

### Post by ktz84 on 2013-10-27
How do I stop my monitor going to sleep when I'm watching a youtube video. It's does it whether I'm fullscreen or not. I'm in Ubuntu 13.10 x64.

Thanks

---

### Post by philinux on 2013-10-27
> **ktz84 said:**
> How do I stop my monitor going to sleep when I'm watching a youtube video. It's does it whether I'm fullscreen or not. I'm in Ubuntu 13.10 x64.

Thanks

system settings > brightness and lock.

Turn screen off when inactive = never.

---

### Post by ktz84 on 2013-10-27
That would do it however not what I'm really looking for as I'd like to the screen to lock after inactivity in most circumstances. If I watch a film or tv show in VLC player in fullscreen the monitor won't go to sleep however if I'm watching YouTube fullscreen it does go to sleep. Is there anyway to prevent this with YouTube.

Thanks

---

### Post by philinux on 2013-10-27
> **ktz84 said:**
> That would do it however not what I'm really looking for as I'd like to the screen to lock after inactivity in most circumstances. If I watch a film or tv show in VLC player in fullscreen the monitor won't go to sleep however if I'm watching YouTube fullscreen it does go to sleep. Is there anyway to prevent this with YouTube.

Thanks

I think the problem with youtube is that flash does not follow the same rules as VLC. It should but it doesn't. Same for me with bbc iplayer which uses flash. So I set the option to never then set it back to 10 mins after watching.

This has been noted for years by the way.

---

### Post by vasa1 on 2013-10-27
This script works for me:```
#!/usr/bin/env bash

sleep_period=8m 

while true; do
  if ps -eo %C --sort -%cpu | head -2 | awk 'NR==2 { exit !($1>10); }'; then
      xdotool key shift
  fi
  sleep ${sleep_period}
done

```
It is triggered when the %CPU usage is > 10% which is usually the case when watching videos, whether YouTube or others. A key press is sent by **xdotool** and that prevents screen blanking. You will need to install xdotool with **sudo apt-get install xdotool**. The sleep period is set for 8 min but that can be changed as can the %CPU in "{ exit !($1>**10**); }".

---

