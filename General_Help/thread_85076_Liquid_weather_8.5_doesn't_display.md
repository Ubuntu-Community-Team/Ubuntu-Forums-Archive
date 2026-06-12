---
title: "Liquid weather 8.5 doesn't display"
date: 2005-11-01
forum: General Help
---

### Post by Zerlinna on 2005-11-01
I installed the newest version of Superkaramba (with /.configure make make install - all went fine) and downloaded liquid weather 8.5. 
But when I start liquid weather it doesn't display on the screen. I know it's there because I can rightclick on it (it'll show me options like "toggle locked position" etc). 

When I run superkaramba with liquid weather from konsole it gives me:

> superkaramba: Starting theme: Liquid Weather ++
superkaramba: /home/mirjam/.superkaramba/liquid_weather.rc
superkaramba: Loading python module: liquid_weather
UTF-8
UTF-8
flatstring:
sys.path.insert(0, '/home/mirjam/apps/liquidweather/')
iso-8859-1
Using pyqt config
No such application: 'kxdocker'
URL: [http://xoap.weather.com/weather/local/NZXX0049?cc=*&dayf=5&prod=xoap&par=1003666583&key=4128909340a9b2fc](http://xoap.weather.com/weather/local/NZXX0049?cc=*&dayf=5&prod=xoap&par=1003666583&key=4128909340a9b2fc)
using weather.com
parsing XML
===================================================
Exception encountered.
Fatal Error; Cannot connect to site or load old data
Call to initWidget failed
Traceback (most recent call last):
  File "/home/mirjam/apps/liquidweather/liquid_weather.py", line 2660, in initWidget
    getWeather(widget)
  File "/home/mirjam/apps/liquidweather/liquid_weather.py", line 1948, in getWeather
    hourly.metric(metric_units)
NameError: global name 'hourly' is not defined

Any ideas?

---

### Post by Zerlinna on 2005-11-06
Since nobody  helped me here I had to find help elswhere. A fedora guy told me that I could find and install the missing application "kxdocker" from kde-look.org. 

After installing that liquid weather works like a charm!

---

