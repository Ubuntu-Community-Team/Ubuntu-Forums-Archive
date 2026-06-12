---
title: "How to disable hdmi ports on rPi4-Ubuntu 22.04.3  LTS"
date: 2023-10-29
forum: General Help
---

### Post by luke3838 on 2023-10-29
Hello ,
my first post .Tryed with "search" but can't find this.How to disable both hdmi ports on rPi4/Ubuntu 22.04.3 LTS  via SSH ?
I'm running rPi4 as audio streamer "headless" and want some power saving with disabling hdmi ports.

---

### Post by TheFu on 2023-10-29
The control is in the /boot/config.txt file ... or user-config.txt, if the distro includes that in the main file to prevent updates from overwriting.  I've never used Ubuntu on my R-pi4, so I don't know. I do use a cut-down debian-based distro on mine, however.   It should go without saying, but use **sudoedit** to modify the file.

raspi-config is used in full debian versions. I doubt Ubuntu leaves it. 

[https://www.raspberrypi.com/documentation/computers/config_txt.html](https://www.raspberrypi.com/documentation/computers/config_txt.html) has more details for the settings.  It may not be possible to disable hdmi0 completely, but you will be able to set the resolution and frequency pretty low to minimize required power.  Seems that setting 4K@60hz is the high-power-use setting to be avoided.  YMMV.

---

### Post by MAFoElffen on 2023-10-29
Add a cron job at reboot
```

sudo crontab -e

```
Press the <O> key to enter insert mode. At the end, add a new line that says
```

@reboot /usr/bin/tvservice -o

```
Press <Escape>, then type :wq, then <Enter>

In the /boot/firmware/usecfg.txt file:
```

hdmi_blanking=2
disable_splash=1

```

---

