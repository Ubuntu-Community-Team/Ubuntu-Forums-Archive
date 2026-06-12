---
title: "Fixing Screenlets ClearWeather Applet"
date: 2016-01-03
forum: General Help
---

### Post by SurfaceUnits on 2016-01-03
The Screenlets ClearWeather applet runs off an API from weather.com. The API was recently changed and ClearWeather ceased working. 
To get the applet to work again, an edit to two lines in the ClearWeatherScreenlet.py file must be made. The file is located in /usr/share/screenlets/screenlets-pack-all/ClearWeather. 

proxies = proxy.Proxy().get_proxy()
        try:
            data = urlopen('http://xoap.weather.com/weather/local/'+self.ZIP+'?cc=*&dayf=10&prod=xoap&par=1003666583&key=4128909340a9b2fc&unit='+unit + '&link=xoap',proxies=proxies).read()

proxies = proxy.Proxy().get_proxy()
            data = urlopen('http://xoap.weather.com/weather/local/'+self.ZIP+'?cc=*&dayf=10&prod=xoap&par=1003666583&key=4128909340a9b2fc&unit='+unit+'&hbhf=12&link=xoap',proxies=proxies).read()

Change the 3 occurrences of xoap in each line to xml and the applet will work again.

---

