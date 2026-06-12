---
title: "&quot;Wayland events: Broken pipe&quot; leading to frequent log outs"
date: 2024-11-23
forum: General Help
---

### Post by raif on 2024-11-23
Ever since upgrading to 24.10, my laptop has been crashing multiple times daily. I can't work out what's going wrong and I've given up hoping that a software update will solve it as it's been happening for over a month, the longest running problem I've had with Ubuntu in over a decade of using it.

I've checked the logs with journalctl and get the following:

```
gnome-shell[168920]: (EE) failed to read Wayland events: Broken pipe
unknown[168151]: Error reading events from display: Broken pipe
systemd[167511]: org.gnome.Shell@wayland.service: Main process exited, code=killed, status=9/KILL
```

Basically the screen will momentarily freeze then log out. A few crashes require powering off but they are rare, like once or twice per week. Before when I was on Ubuntu 24.04, I could for go months without any instability. I've tried turning off extensions and shutting down most programs but it doesn't make a difference. The only trend is that the crashes are more likely when more applications / tabs are open. I'm on a laptop with an AMD Ryzen™ 7 and 16GB RAM, fully updated to latest kernel etc.

Any help gratefully appreciated!

---

