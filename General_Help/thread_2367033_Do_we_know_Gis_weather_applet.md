---
title: "Do we know Gis weather applet?"
date: 2017-07-25
forum: General Help
---

### Post by shantiq on 2017-07-25
been using  [[SIZE=2]my-weather-indicator         [/SIZE]]("https://ubuntuforums.org/showthread.php?t=2036527&highlight=shantiq+weather")for years now and just came across this too on Slackware sbopkg package manager and turns out there is a version too for Ubuntu....   very nice indeed



[http://www.noobslab.com/2016/12/gis-weather-widget-updated-and-now.html](http://www.noobslab.com/2016/12/gis-weather-widget-updated-and-now.html)

---

### Post by #&amp;thj^% on 2017-07-25
Yep been using it for about a year or more now, very nice indeed. :)
> 
    View weather for several days
    Detailed weather forecast for today and tomorrow
    Fast switching between cities
    Select the background and theme weather icons
    "Compass" with the wind direction, with adjustable angle of rotation
    Highlighting the high wind
    Supported weather services:
    > Gismeteo.com
    > AccuWeather.com
    > OpenWeatherMap.org
    > Yr.no
    Support SVG and widget scale
    Indicator to panel
    Presets

If you don't want to add a PPA, you can just download the .deb (or specific packages for other distros)
[https://sourceforge.net/projects/gis-weather/files/gis-weather/0.8.2.5/](https://sourceforge.net/projects/gis-weather/files/gis-weather/0.8.2.5/)
[https://github.com/RingOV/gis-weather#readme](https://github.com/RingOV/gis-weather#readme)

---

### Post by Habitual on 2017-07-25
I installed gis weather years ago, and it was great *then* :)

---

### Post by rburkartjo on 2017-07-25
also been using for a couple of years. good app

---

### Post by shantiq on 2018-06-21
it appears gis-weather is broken on 16.04 at the moment
anyone else finding that?

it is looping on all services


```
Processing triggers for menu (2.1.47ubuntu1) ...
shan@shan-Aspire-XC-780:~$ gis-weather 
Gis Weather 0.8.2.5
/usr/share/gis-weather/gis-weather.py:66: PyGIWarning: AppIndicator3 was imported without specifying a version first. Use gi.require_version('AppIndicator3', '0.1') before import to ensure that the right version gets loaded.
  from gi.repository import AppIndicator3
/usr/share/gis-weather/gis-weather.py:74: PyGIWarning: Rsvg was imported without specifying a version first. Use gi.require_version('Rsvg', '2.0') before import to ensure that the right version gets loaded.
  from gi.repository import Rsvg
Configuration folder:
    /home/shan/.config/gis-weather/gw_config2.json
Widget size:
    width = 684 height = 320 including indent = 20
Screenshot saved to /home/shan/.config/gis-weather/main_screenshot.png
Your screen does not support alpha
> Getting weather for 7 days
> Downloading http://www.yr.no/place/United_Kingdom/England/Norwich/forecast.xml
OK
> Downloading http://api.yr.no/weatherapi/locationforecast/1.9/?lat=52.62783;lon=1.29834
1
2
3
4
5
[!] Unable to download page, check the network connection
[!] Next try in 10 seconds
----------------------------------------
> Getting weather for 7 days
> Downloading http://www.yr.no/place/United_Kingdom/England/Norwich/forecast.xml
OK
> Downloading http://api.yr.no/weatherapi/locationforecast/1.9/?lat=52.62783;lon=1.29834
1
2
3
4
5
[!] Unable to download page, check the network connection
[!] Next try in 10 seconds
----------------------------------------


```

---

### Post by #&amp;thj^% on 2018-06-21
I also can confirm gis-weather for all services is broken>>>I had noticed this since yesterday 6/20/2018. :(

---

### Post by shantiq on 2018-06-21
thanx 1fallen for confirmation
anyone knows why and how to work around if at all possible?

---

### Post by #&amp;thj^% on 2018-06-21
It seems that Openweathermap is still working but not suitable for me>>inaccurate temp and conditions reported so a waste of time.
Also see: [https://github.com/RingOV/gis-weather/issues/35](https://github.com/RingOV/gis-weather/issues/35)

---

### Post by shantiq on 2018-06-21
thanx 1fallen  will carry on lookin

---

### Post by shantiq on 2018-08-29
ha great news  works again using   [first purged the old one]

```
 sudo apt-get install git fakeroot
```

then

```
 cd && git clone [https://github.com/RingOV/gis-weather.git](https://github.com/RingOV/gis-weather.git) && cd gis-weather/scripts && python3 build_deb.py && cd ../DEB && sudo dpkg -i *.deb
```


as shown [here]("https://github.com/RingOV/gis-weather")


and the version is VERSION = 0.8.2.76   and not the 8.2.5 found in debs and which no longer works

PS Now   with yr and OpenWeatherMap it is in ENG with gismeteo in RU / Ukrainian/Latvian/Lithuanian/Romanian

---

