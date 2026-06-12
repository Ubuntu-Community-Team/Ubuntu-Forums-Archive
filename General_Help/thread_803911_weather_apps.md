---
title: "weather apps"
date: 2008-05-22
forum: General Help
---

### Post by kopiq on 2008-05-22
hi im looking a weather app in the repos, or not. kweather is ok but it dosent have my city, and also i would like to have a 3 or 5 dayday forcast on my desktop not my panel. thanks for any help!

---

### Post by mano cazalet on 2008-05-22
maybe the screenlets from the repos would be a good option.
or desklets have the weather one to.

---

### Post by HousieMousie2 on 2008-05-22
> **kopiq said:**
> hi im looking a weather app in the repos, or not. kweather is ok but it dosent have my city, and also i would like to have a 3 or 5 dayday forcast on my desktop not my panel. thanks for any help!

My Mom likes GoodWeather, via gdesklets, she used Kpackage, I got it with Synaptic.  Just search for gdesklets, then GoodWeather.

Not sure if they have fixed the Weather.com issue or not yet, but it is a simple fix.  Weather.com changed their format, which is where GoodWeather gets it's info, so the location ID is now your zip code (if in the USA... don't know about out side of the US.)

Check out the site for the installation guide:

[http://www.howtoforge.com/gnome_gdesklets](http://www.howtoforge.com/gnome_gdesklets)

After installing gdesklets and GoodWeather, the fix is:

Go to your home directory and view hidden files, then find .gdesklets/ Sensors/ GoodWeather.  Open the __init__.py, in gedit or other like editor.  Find the line:

WEATHER_SOURCE = "http://xoap.weather.com/weather/local/" \
"%(weather_code)s?cc=*&dayf=5&prod=xoap&" \

 Then change it to: (it's just adding this last bit)

WEATHER_SOURCE = "http://xoap.weather.com/weather/local/" \
"%(weather_code)s?cc=*&dayf=5&prod=xoap&**[SIZE="4"]link=xoap&[/SIZE]**" \

Of course, not larger or bolded... then Save.  Then restart GoodWeather (right click on GoodWeather on your desktop and choose Restart Desklet) and it should be fixed.

^^^This of course comes from greater minds than mine^^^

---

### Post by kopiq on 2008-05-23
thanks i will try these

---

### Post by neymac on 2008-05-23
I use the weather plugin of cairo-dock.
Download and install the deb files (cairodock and plugins)from 
[http://developer.berlios.de/project/showfiles.php?group_id=8724]("http://developer.berlios.de/project/showfiles.php?group_id=8724")

It's configurable and you can put it at the desktop with 5 days forecast.
The clock, big dustbin and weather (five days of sun forecasted here) figures shown are plugins of cairo-dock detached from the main bar.

[[img]http://pix.nofrag.com/4/a/3/3ac26c6a5ba940e0c77fddc469307tt.jpg[/img]](http://pix.nofrag.com/4/a/3/3ac26c6a5ba940e0c77fddc469307.html)

---

