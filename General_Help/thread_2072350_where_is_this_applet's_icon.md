---
title: "where is this applet's icon"
date: 2012-10-17
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2012-10-17
the applet:
[http://library.gnome.org/users/cpufreq-applet/stable/cpufreq-applet-introduction.html.en](http://library.gnome.org/users/cpufreq-applet/stable/cpufreq-applet-introduction.html.en)
the closest thing i can find is this file
/usr/share/icons/hicolor/scalable/apps/gnome-cpu-frequency-applet.svg

i am on my 10.04 install which uses gnome 2
i want to copy this icon to my 12.10 xubuntu install of xfce and use it in the genmom-plugin

---

### Post by stinkeye on 2012-10-18
> **pqwoerituytrueiwoq said:**
> the applet:
[http://library.gnome.org/users/cpufreq-applet/stable/cpufreq-applet-introduction.html.en](http://library.gnome.org/users/cpufreq-applet/stable/cpufreq-applet-introduction.html.en)
the closest thing i can find is this file
/usr/share/icons/hicolor/scalable/apps/gnome-cpu-frequency-applet.svg

i am on my 10.04 install which uses gnome 2
i want to copy this icon to my 12.10 xubuntu install of xfce and use it in the genmom-plugin
In 12.10 I have this directory...
/usr/share/pixmaps/cpufreq-applet

---

### Post by pqwoerituytrueiwoq on 2012-10-18
thanks, same place on 10.04
here is my script (gnome cpu freq applet for xfce's genmon plugin)
```
#!/bin/sh
ICONS="/usr/local/share/pixmaps/cpufreq-applet"
if [ -z "$1" ];then
    echo "<img>$ICONS/cpufreq-na.png</img><txt>Which Core?</txt>"
    echo -e "<tool>`basename $0` [Core Number]\n`basename $0` 0</tool>"
    exit
fi
LOC="/sys/devices/system/cpu/cpu$1/cpufreq"

CUR=`cat $LOC/scaling_cur_freq`
MAX=`cat $LOC/scaling_max_freq`
USE=`echo '' | awk "{print int($CUR/$MAX*1000)}"`
GHz=`echo '' | awk "{print int($CUR/1000000)}"`
if [ $USE -lt 375 ];then
    echo "<img>$ICONS/cpufreq-25.png</img>"
elif [ $USE -lt 625 ];then
    echo "<img>$ICONS/cpufreq-50.png</img>"
elif [ $USE -lt 875 ];then
    echo "<img>$ICONS/cpufreq-75.png</img>"
else
    echo "<img>$ICONS/cpufreq-100.png</img>"
fi
echo "<tool>`echo $USE/10 | bc`%</tool>"
echo "<txt>$GHz GHz</txt>"
```

---

