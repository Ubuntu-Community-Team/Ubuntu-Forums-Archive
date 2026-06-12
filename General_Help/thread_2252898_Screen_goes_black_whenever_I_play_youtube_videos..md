---
title: "Screen goes black whenever I play youtube videos."
date: 2014-11-15
forum: General Help
---

### Post by techdragon2 on 2014-11-15
Hi, I recently installed Xubuntu 14.04 and every time I try to play YouTube videos in any web browser my whole screen goes black and I cannot go back to my desktop.
So I have to forcefully shut-down my laptop and restart it again.
I have tried to reinstall flash player and use every other web browser but yet the problem still occurs.

I do not know how to solve this problem, but this only started after I attempted to install arch Linux.
I'm fairly new to Linux so if you can make it simple that would be very helpful.
Computer Specs............

Model: Toshiba Satellite Pro-M300
OS: xubuntu 14.04
HDD: 150GB
RAM: 2GB
Previous OS: Linux Mint 17 (cinnamon)
32 bit.

---

### Post by pqwoerituytrueiwoq on 2014-11-15
install the [xfce4-genmon-plugin]("apt:xfce4-genmon-plugin")
add the applet to your panel
have it run this script and pass the -u option to it
```
#!/bin/sh
if [ "$1" = "-t" ];then
    if [ $(xdg-screensaver status) = "enabled" ];then
        arg1="suspend"
    else
        arg1="resume"
    fi
    arg2=$(xwininfo -root | grep 'Window id'|awk '{print $4}')
    xdg-screensaver $arg1 $arg2
elif [ "$1" = "-u" ];then
    echo "<tool>Screensaver</tool><click>toggle-screensaver -t</click>"
    if [ $(xdg-screensaver status) = "enabled" ];then
        echo "<img>/usr/share/icons/gnome/16x16/apps/xscreensaver.png</img>"
    else
        echo "<img>/usr/share/icons/gnome/16x16/devices/computer.png</img>"
    fi
else
    xdg-screensaver status
fi
exit
```
now when you click the genmon applet you just added it will disable your screensaver, another click will re-enable it
[[img]http://www.zimagez.com/miniature/screenshot-11152014-024657pm.php[/img]](http://www.zimagez.com/zimage/screenshot-11152014-024657pm.php)

---

### Post by techdragon2 on 2014-11-15
It came up with this error.
[SIZE=6][ATTACH=CONFIG]257990[/ATTACH][/SIZE][SIZE=5][/SIZE]

---

### Post by pqwoerituytrueiwoq on 2014-11-15
cause you did not make the script i posted see the code?
i have it saved to /usr/local/bin/toggle-screensaver
don't forget to chmod +x the file

---

### Post by techdragon2 on 2014-11-16
Thanks alot the problem has stopped now.

---

