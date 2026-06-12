---
title: "My-Weather-Indicator won't start"
date: 2016-10-15
forum: General Help
---

### Post by george_2 on 2016-10-15
Hope someone can advise on this.  My-Weather-Indicator refuses to start on my Dell laptop running 16.04 LTS, although it runs fine on my other computers running the same O/S.  

I've uninstalled and reinstalled it several times via Synaptic Package Manager but it still refuses to run.  After doing a Complete Removal via Synaptic I still see something named "my-weather-indicator | preferences" all in lower case, and I can't see how to remove that.

This is a great program and I'd love to be able to use it on my laptop.

Thanks for any help.

---

### Post by CantankRus on 2016-10-15
I just installed from ppa.
```
sudo add-apt-repository ppa:atareao/atareao
sudo apt update
sudo apt install my-weather-indicator
```

I got the run command by dragging My-Weather-Indicator icon from dash into an open gedit window.
In terminal ran ....
```
/opt/extras.ubuntu.com/my-weather-indicator/bin/my-weather-indicator
```

On first run it gave this error and failed to start but it did create a config @ **~/.config/my-weather-indicator/my-weather-indicator.conf**
```
**[COLOR="#006400"]glen@Xenial:~$ [/COLOR]/opt/extras.ubuntu.com/my-weather-indicator/bin/my-weather-indicator**
<gettext.GNUTranslations object at 0x7f7e7f2db710>
#####################################################
System: Linux
Machine: x86_64
Node: Xenial
Release: 4.4.0-43-generic
Version: #63-Ubuntu SMP Wed Oct 12 13:48:03 UTC 2016
Platform: Linux-4.4.0-43-generic-x86_64-with-Ubuntu-16.04-xenial
My-Weather-Indicator version: 0.8.1-0extras16.04.1
#####################################################

<urlopen error unknown url type: https>
[Errno 2] No such file or directory: '/home/glen/.config/my-weather-indicator/my-weather-indicator.conf'
******* Adquiring inv direction *******
Traceback (most recent call last):
  File "/opt/extras.ubuntu.com/my-weather-indicator/bin/my-weather-indicator", line 69, in <module>
    mwi = MWI()
  File "/opt/extras.ubuntu.com/my-weather-indicator/share/my-weather-indicator/myweatherindicator.py", line 143, in __init__
    self.load_preferences()
  File "/opt/extras.ubuntu.com/my-weather-indicator/share/my-weather-indicator/myweatherindicator.py", line 248, in load_preferences
    latitude, longitude)['city']
  File "/opt/extras.ubuntu.com/my-weather-indicator/share/my-weather-indicator/geocodeapi.py", line 130, in get_inv_direction
    aplace = reverse.resolve()
GLib.Error: geocode_error: Unable to geocode (1)
```


Ran the command again and it worked although appears to be using lon":0,"lat":0 as the location.
```
**[COLOR="#006400"]glen@Xenial:~$[/COLOR] /opt/extras.ubuntu.com/my-weather-indicator/bin/my-weather-indicator**
<gettext.GNUTranslations object at 0x7f7bd7f38710>
#####################################################
System: Linux
Machine: x86_64
Node: Xenial
Release: 4.4.0-43-generic
Version: #63-Ubuntu SMP Wed Oct 12 13:48:03 UTC 2016
Platform: Linux-4.4.0-43-generic-x86_64-with-Ubuntu-16.04-xenial
My-Weather-Indicator version: 0.8.1-0extras16.04.1
#####################################################

****** Requesting timezone identificacion
** OWM **
6295630 0 0
1
***** refreshing weather *****
<urlopen error unknown url type: https>
--- Updating data in location 0 ---
****** Updating weather
****** Calculating rawOffset
-------------------------------------------------------
OpenWeatherMap Weather Service url:http://api.openweathermap.org/data/2.5/weather?id=6295630&appid=4516154e5c8a6494e7e13b550408c863
-------------------------------------------------------
****** Updated weather
None
--- End of updating data in location 0 ---
*** Looking For Internet ***
<urlopen error unknown url type: https>
*** Internet Found ***
***** refreshing weather *****
<urlopen error unknown url type: https>
--- Updating data in location 0 ---
****** Updating weather
****** Calculating rawOffset
-------------------------------------------------------
OpenWeatherMap Weather Service url:http://api.openweathermap.org/data/2.5/weather?id=6295630&appid=4516154e5c8a6494e7e13b550408c863
-------------------------------------------------------
****** Updated weather
{'update_time': 1476586719.3496833, 'forecasts': [{'condition_icon': 'mwil-rain.png', 'snow_day': None, 'sunrise': '06:42', 'sunset': '18:49', 'avewind': '5 km/h (S)', 'avehumidity': '0 %', 'wind_icon': 'mwi-wind16.png', 'day_of_week': 'Sunday', 'qpf_day': None, 'moon_icon': 'mwi-moon14.png', 'cloudiness': '54 %', 'maxhumidity': None, 'condition': 'light rain', 'moon_phase': 'Full Moon', 'high': '26', 'low': '26', 'snow_allday': None, 'condition_text': 'Rain', 'qpf_night': None, 'snow_night': None, 'qpf_allday': None, 'minhumidity': None, 'condition_image': 'mwig-rain.png', 'maxwind': None}, {'condition_icon': 'mwil-cloudy.png', 'snow_day': None, 'sunrise': '06:42', 'sunset': '18:49', 'avewind': '5 km/h (SSW)', 'avehumidity': '100 %', 'wind_icon': 'mwi-wind18.png', 'day_of_week': 'Monday', 'qpf_day': None, 'moon_icon': 'mwi-moon15.png', 'cloudiness': '56 %', 'maxhumidity': None, 'condition': 'cloudy', 'moon_phase': 'Full Moon', 'high': '26', 'low': '25', 'snow_allday': None, 'condition_text': 'Cloudy', 'qpf_night': None, 'snow_night': None, 'qpf_allday': None, 'minhumidity': None, 'condition_image': 'mwig-cloudy.png', 'maxwind': None}, {'condition_icon': 'mwil-cloudy.png', 'snow_day': None, 'sunrise': '06:42', 'sunset': '18:49', 'avewind': '8 km/h (SBW)', 'avehumidity': '100 %', 'wind_icon': 'mwi-wind17.png', 'day_of_week': 'Tuesday', 'qpf_day': None, 'moon_icon': 'mwi-moon16.png', 'cloudiness': '64 %', 'maxhumidity': None, 'condition': 'cloudy', 'moon_phase': 'Waning Gibbous', 'high': '26', 'low': '26', 'snow_allday': None, 'condition_text': 'Cloudy', 'qpf_night': None, 'snow_night': None, 'qpf_allday': None, 'minhumidity': None, 'condition_image': 'mwig-cloudy.png', 'maxwind': None}, {'condition_icon': 'mwil-partly-cloudy.png', 'snow_day': None, 'sunrise': '06:42', 'sunset': '18:49', 'avewind': '8 km/h (S)', 'avehumidity': '100 %', 'wind_icon': 'mwi-wind16.png', 'day_of_week': 'Wednesday', 'qpf_day': None, 'moon_icon': 'mwi-moon17.png', 'cloudiness': '20 %', 'maxhumidity': None, 'condition': 'partly sunny', 'moon_phase': 'Waning Gibbous', 'high': '26', 'low': '25', 'snow_allday': None, 'condition_text': 'Partly sunny', 'qpf_night': None, 'snow_night': None, 'qpf_allday': None, 'minhumidity': None, 'condition_image': 'mwig-partly-cloudy.png', 'maxwind': None}, {'condition_icon': 'mwil-rain.png', 'snow_day': None, 'sunrise': '06:41', 'sunset': '18:48', 'avewind': '5 km/h (SSW)', 'avehumidity': '0 %', 'wind_icon': 'mwi-wind18.png', 'day_of_week': 'Thursday', 'qpf_day': None, 'moon_icon': 'mwi-moon18.png', 'cloudiness': '16 %', 'maxhumidity': None, 'condition': 'light rain', 'moon_phase': 'Waning Gibbous', 'high': '26', 'low': '26', 'snow_allday': None, 'condition_text': 'Rain', 'qpf_night': None, 'snow_night': None, 'qpf_allday': None, 'minhumidity': None, 'condition_image': 'mwig-rain.png', 'maxwind': None}, {'condition_icon': 'mwil-rain.png', 'snow_day': None, 'sunrise': '06:41', 'sunset': '18:48', 'avewind': '6 km/h (SW)', 'avehumidity': '0 %', 'wind_icon': 'mwi-wind20.png', 'day_of_week': 'Friday', 'qpf_day': None, 'moon_icon': 'mwi-moon19.png', 'cloudiness': '42 %', 'maxhumidity': None, 'condition': 'light rain', 'moon_phase': 'Waning Gibbous', 'high': '26', 'low': '25', 'snow_allday': None, 'condition_text': 'Rain', 'qpf_night': None, 'snow_night': None, 'qpf_allday': None, 'minhumidity': None, 'condition_image': 'mwig-rain.png', 'maxwind': None}, {'condition_icon': 'mwil-rain.png', 'snow_day': None, 'sunrise': '06:41', 'sunset': '18:48', 'avewind': '7 km/h (SBW)', 'avehumidity': '0 %', 'wind_icon': 'mwi-wind17.png', 'day_of_week': 'Saturday', 'qpf_day': None, 'moon_icon': 'mwi-moon20.png', 'cloudiness': '22 %', 'maxhumidity': None, 'condition': 'light rain', 'moon_phase': 'Last Quarter', 'high': '26', 'low': '25', 'snow_allday': None, 'condition_text': 'Rain', 'qpf_night': None, 'snow_night': None, 'qpf_allday': None, 'minhumidity': None, 'condition_image': 'mwig-rain.png', 'maxwind': None}], 'forecast_information': {'city': '...', 'postal_code': '', 'latitude_e6': '', 'forecast_date': '', 'current_date_time': '', 'longitude_e6': '', 'unit_system': 'SI'}, 'current_conditions': {'solarradiation': None, 'precip_today': None, 'temperature': '25', 'heat_index': 1.8274420607861117, 'condition_icon_light': 'mwil-cloudy.png', 'rawOffset': 1.0, 'condition_icon_dark': 'mwid-cloudy.png', 'sunrise': '06:42', 'moon_icon': 'mwi-moon14.png', 'sunset': '18:49', 'sunrise_time_utc': '05:42', 'wind_icon': 'mwi-wind18.png', 'visibility': None, 'humidity': '100 %', 'wind_condition': '6 km/h (SSW)', 'dusk_time': '19:10', 'windchill': 0.0, 'sunset_time_utc': '17:49', 'dawn_time': '06:21', 'precip_1hr': None, 'cloudiness': '92 %', 'isday': False, 'dawn': '06:21', 'moon_phase': 'Full Moon', 'sunrise_time': '06:42', 'dew_point': '26', 'condition': 'overcast', 'dusk': '19:10', 'UV': None, 'condition_text': 'Overcast', 'pressure': None, 'condition_image': 'mwig-cloudy.png', 'feels_like': '26', 'sunset_time': '18:49'}, 'ok': True}
--- End of updating data in location 0 ---
```

So then from the **panel indicator > preferences** set my location.


**So what I suggest is....**
Delete the config @ **~/.config/my-weather-indicator/my-weather-indicator.conf**
and try again by running twice in terminal...
```
/opt/extras.ubuntu.com/my-weather-indicator/bin/my-weather-indicator
```
...and then setting your location.

or

You could also try copying over a config from a machine that works to **~/.config/my-weather-indicator/my-weather-indicator.conf**
For reference here's mine after I set my location...
```
{
    "24h": true,
    "autolocation": false,
    "first-time": false,
    "http-port": 0,
    "http-proxy": "",
    "https-port": 0,
    "https-proxy": "",
    "icon-light": true,
    "latitude": -31.952712,
    "latitude2": 0,
    "location": "Perth",
    "location2": "",
    "longitude": 115.8604796,
    "longitude2": 0,
    "main-location": true,
    "onalldesktop1": true,
    "onalldesktop2": true,
    "onwidget1hide": false,
    "onwidget1top": false,
    "onwidget2hide": false,
    "onwidget2top": false,
    "pressure": "mb",
    "rain": "mm",
    "refresh": 1.0,
    "second-location": false,
    "show-notifications": true,
    "show-notifications2": true,
    "show-temperature": true,
    "show-temperature2": true,
    "showintaskbar1": false,
    "showintaskbar2": false,
    "skin1": "/opt/extras.ubuntu.com/my-weather-indicator/share/my-weather-indicator/skins/super",
    "skin2": "/opt/extras.ubuntu.com/my-weather-indicator/share/my-weather-indicator/skins/super",
    "snow": "cm",
    "temperature": "C",
    "version": "0.8.1-0extras16.04.1",
    "visibility": "km",
    "weather-service": "openweathermap",
    "widget1": false,
    "widget2": false,
    "wind": "km/h",
    "wp1-x": 0,
    "wp1-y": 0,
    "wp2-x": 0,
    "wp2-y": 0,
    "wu-key": "",
    "wwo-key": ""
}
```

---

### Post by george_2 on 2016-10-19
Thank you for your help.  I successfully re-installed it from ppa.  Hope it runs longer than the previous install!  :)

---

