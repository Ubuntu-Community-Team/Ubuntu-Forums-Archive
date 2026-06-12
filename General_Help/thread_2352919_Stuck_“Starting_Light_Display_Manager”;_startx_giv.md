---
title: "Stuck “Starting Light Display Manager”; startx gives (EE) Fatal error: no screens fou"
date: 2017-02-17
forum: General Help
---

### Post by fallenpwr on 2017-02-17
I'm on Ubuntu 15.10, XPS 15 9550 w/ Nvidia 960m.

Troubles started with I tried to dual-display with nvidia 361; failed horribly, so i tried switching to nouveau drivers. Work, but then after I resumed from sleep, it didn't start unity, so I rebooted, and got a checksum error(??????). Rebooting again, I got stuck on Starting Light Display Manager. Tried purging nvidia, tried removing xorg.conf, tried [http://askubuntu.com/questions/692445/ubuntu-hangs-on-starting-light-display-manager-on-bootup](http://askubuntu.com/questions/692445/ubuntu-hangs-on-starting-light-display-manager-on-bootup) and tried [http://askubuntu.com/questions/734792/boot-process-stuck-on-started-light-display-manager](http://askubuntu.com/questions/734792/boot-process-stuck-on-started-light-display-manager), no cigar.


Tried reinstalling nvidia-352, and nvidia-331. Which brings me to being stuck on "Starting ACPI daemon". Well, not exactly stuck but rather the screen says that, then flickers/turns off, and then flashes the same thing again. I can't even get a terminal with `ctrl``alt``F1` because of it.


There was one time I was doing some random stuff including changing my xorg.conf, changing `device "nvidia"` to `device "vesa"` and that got me into unity albeit a very strange unity (via `startx unity`). I tried to change to nvidia-352 in the *Additional Software* menu, but it got stuck or something. I rebooted, only to find the flickering thing again.


My `xorg.conf`:


   ```
 Section "ServerLayout"
        Identifier "layout"
        Screen 0 "nvidia"
        Inactive "intel" (tried switching nvidia and intel but that = black screen)
    EndSection


    Section "Device"
        Identifier "intel"
        Driver "modesetting"
        BusID "{something}"
        Option "AccelMethod" "None"
    EndSection


    Section "Screen"
        Identifier "intel"
        Device "intel"
    EndSection
    
    Section "Device"
        Identifier "nvidia"
        Driver "nvidia" (I tried changing to vesa)
        Option "AllowEmptyInitialConfiguration" "on"
        Option "IgnoreDisplayDevices" "CRT" 
```(I tried changing to "UseDisplayDevice" and also "CRT" to "DFP", not that I have any clue what's happening)
    EndSection

---

### Post by wildmanne39 on 2017-02-17
I can not help with the issue but you are using an ubuntu version that is no longer supported so you can not even get security updates so your system is at risk being connected to the internet.

---

