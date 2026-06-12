---
title: "my-weather-indicator not working after update"
date: 2016-04-02
forum: General Help
---

### Post by fizikz on 2016-04-02
After an update today for my-weather-indicator, neither the indicator the indicator area (gnome classic) nor the applet show up. However, the process is running. I'm running Ubuntu 14.04 LTS. 

I don't remember the previous version of my-weather-indicator before the update, but the current version is 0.7.3-0extras15.10.0. I wonder if this is an issue since it seems to refer to Ubuntu 15.10. 

I did not change any settings since it was last working. I also don't see any error messages when I start it from the terminal. Simply, no applet/indicator. Has anyone else having this issue?

---

### Post by kostkon on 2016-04-02
Kill it, delete its config file, i.e.
```
rm ~/.config/my-weather-indicator/my-weather-indicator.conf
```
then restart it, see how it goes.

---

### Post by fizikz on 2016-04-02
Thanks. I tried that and it makes no difference. No icon or applet appears. This is the output in the terminal:

```
$ /opt/extras.ubuntu.com/my-weather-indicator/bin/my-weather-indicator
<gettext.GNUTranslations object at 0xb528e74c>
#####################################################
System: Linux
Machine: i686
Node: ssg1
Release: 3.13.0-83-generic
Version: #127-Ubuntu SMP Fri Mar 11 00:26:47 UTC 2016
Platform: Linux-3.13.0-83-generic-i686-with-Ubuntu-14.04-trusty
#####################################################

My-Weather-Indicator version: 0.7.3-0extras15.10.0
#####################################################


```

---

### Post by kostkon on 2016-04-03
> **fizikz said:**
> Thanks. I tried that and it makes no difference. No icon or applet appears. This is the output in the terminal:

```
$ /opt/extras.ubuntu.com/my-weather-indicator/bin/my-weather-indicator
<gettext.GNUTranslations object at 0xb528e74c>
#####################################################
System: Linux
Machine: i686
Node: ssg1
Release: 3.13.0-83-generic
Version: #127-Ubuntu SMP Fri Mar 11 00:26:47 UTC 2016
Platform: Linux-3.13.0-83-generic-i686-with-Ubuntu-14.04-trusty
#####################################################

My-Weather-Indicator version: 0.7.3-0extras15.10.0
#####################################################


```
Seems to be running fine as far as I can see. What happens if you right-click on your panel, do you see the option to add its applet. Does it actually come as an applet in gnome classic or is it the indicator that is missing? Are you sure you haven't somehow removed the indicator area applet from your panel?

---

### Post by fizikz on 2016-04-03
Before the update, I had both the applet and indicator (taskbar icon). Now I don't see either anywhere. I did not change any settings before/during the update of my-weather-indicator.

Here is my config file:
```
{
    "24h": true,
    "autolocation": false,
    "first-time": false,
    "icon-light": true,
    "latitude": [edited],
    "latitude2": 0,
    "location": "[edited]",
    "location2": "",
    "longitude": [edited],
    "longitude2": 0,
    "main-location": true,
    "onalldesktop1": false,
    "onalldesktop2": true,
    "onwidget1hide": true,
    "onwidget1top": false,
    "onwidget2hide": false,
    "onwidget2top": false,
    "pressure": "mb",
    "rain": "mm",
    "refresh": 1.0,
    "second-location": false,
    "show-notifications": false,
    "show-notifications2": true,
    "show-temperature": true,
    "show-temperature2": true,
    "showintaskbar1": true,
    "showintaskbar2": false,
    "skin1": "/opt/extras.ubuntu.com/my-weather-indicator/share/my-weather-indicator/skins/anotherone",
    "skin2": "/opt/extras.ubuntu.com/my-weather-indicator/share/my-weather-indicator/skins/simple",
    "snow": "cm",
    "temperature": "C",
    "version": "0.7.1-0extras15.10.0",
    "visibility": "km",
    "weather-service": "openweathermap",
    "widget1": true,
    "widget2": false,
    "wind": "km/h",
    "wp1-x": 1053,
    "wp1-y": 24,
    "wp2-x": 0,
    "wp2-y": 0,
    "wu-key": "",
    "wwo-key": ""
}
```

I checked that the directories mentioned in the config file exist and contain the skins. The only discrepancy I notice is the version number (0.7.1 in config file vs 0.7.3 from terminal output). I did not manually edit the config file.

---

### Post by fizikz on 2016-04-03
Good news! There was another update to my-weather-indicator today (version 0.7.4-0extras15.10.11) and it fixes the regression/issues. Now it's working again.

---

### Post by fizikz on 2016-04-04
It seems the quality control on my-weather-indicator updates could use improvement. An update today (v 0.7.6-0extras15.10.0) left me with only one widget. No matter which style chosen in the preferences it always displays the same widget. 

Also, it does not seem to use yahoo API even when it is selected; the data seem to be from openweathermap. It's been a few weeks that the yahoo data source isn't working.

Has anyone else noticed these issues?

---

### Post by Bashing-om on 2016-04-04
fizikz; Hello;

Maybe:
[https://www.igorkromin.net/index.php/2016/03/27/yahoo-effectively-shut-down-its-weather-api-by-forcing-oauth-10-and-crippling-it/](https://www.igorkromin.net/index.php/2016/03/27/yahoo-effectively-shut-down-its-weather-api-by-forcing-oauth-10-and-crippling-it/)

does this apply ? If so .. I too am open to a re-work .

[INDENT][INDENT]depends, depends
[/INDENT][/INDENT]

---

### Post by fizikz on 2016-04-04
That makes sense, and the timeline fits too. I figured it could be an issue with changes in the yahoo API. Unfortunately the openweathermap data is really quite inaccurate. The two other weather services (wunderground, world weather online) require signing up, and the latter no longer provides free accounts.

EDIT: Upon closer inspection it seems since the MWI update (v 0.7.6-0extras15.10.0), it now works with the yahoo weather data source.

---

### Post by Valter_Silva on 2016-06-10
> **kostkon said:**
> Kill it, delete its config file, i.e.
```
rm ~/.config/my-weather-indicator/my-weather-indicator.conf
```
then restart it, see how it goes.


Thank you. That worked. I just had to change the weather service.

Greetings!

---

### Post by george_2 on 2016-06-29
Same problem here with MWI on Ubuntu 15.04 laptop.  It's running but the icons in the system tray are gone.  I tried killing the config file to no avail.

Funny thing is, it works OK on my Ubuntu 15.04 desktop!!

Anybody have further suggestions?

George

---

