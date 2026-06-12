---
title: "Keyboard Lag in 18.04"
date: 2018-09-08
forum: General Help
---

### Post by motobeats on 2018-09-08
Recently upgraded from 16.04 to 18.04. Upgrade has introduced a significant and consistent lag in the keyboard. Especially when switching between windows. Firefox seems to suffer the most but the terminal is slow too.

Hardware - Intel NUC i5 with 16GB 
Keyboard - Logitech K520 wireless (with mouse)

Tried so far
1. New batteries
2. USB keyboard
3. Moving the USB receiver for the keyboard
4. Switching back to Unity

Particularly annoying is typing in the search bar after opening a new Firefox tab. I seem to be losing focus on the text box as my typing will start to move me around the screen rather than populate the box.

What's next to try? Any info I can supply?

---

### Post by TheFu on 2018-09-08
Gather data as the system is running to figure out which processes are eating all the CPU and RAM.
**htop** is a good way to do that.

It is always a good idea to check the system logs for any issues too. Google "ubuntu log files" for a how-to, if you need it.

---

### Post by motobeats on 2018-09-08
I think there are a few causes of the experience I am having. But I'm nearly certain it is not caused by lack of resources. vmstat shows the CPU ~85% idle or more nearly all the time and 8GB of cached memory of the 16 on the system so plenty of memory if Linux needs it. Additionally HD is SSD so I/O should be pretty quick even if the system was swapping.

For the Firefox issues I finally found this link. Much better with Accessibility off.
[https://support.mozilla.org/en-US/questions/1197166](https://support.mozilla.org/en-US/questions/1197166)

As for general keyboard lag, switching back to unity and uninstalling gnome-shell using apt-get then restarting seems to have resolved those occurrences. Thank goodness. I was getting ready to bail on 18.04

---

### Post by motobeats on 2018-09-08
Followed this post for getting rid of gnome desktop and shell.

[https://askubuntu.com/questions/767577/how-can-i-remove-gnome-desktop-environment-without-messing-unity-de-ubuntu-16](https://askubuntu.com/questions/767577/how-can-i-remove-gnome-desktop-environment-without-messing-unity-de-ubuntu-16)

---

