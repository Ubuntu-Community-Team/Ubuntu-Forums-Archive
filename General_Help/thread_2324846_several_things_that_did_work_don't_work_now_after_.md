---
title: "several things that did work don't work now after upgrade to 16.04"
date: 2016-05-16
forum: General Help
---

### Post by Evil Wayz on 2016-05-16
My digital camera no longer shows up as a drive.  It isn't even detected by lsusb.

There is no bluetooth icon when bluetooth is active and connected.

Neither my-weather-indicator or gnome weather work anymore. 


I am using Cinnamon 3.0 as my window manager, I'm not sure if this is the issue. 

16.04, 4.3 kernel.

---

### Post by peter228 on 2016-05-16
How did you arrive at 16.04?  Was this a fresh install or an upgrade from something?  If it was an upgrade which release have you upgraded from?

Did you keep your old /home directory or did you just copy over the dot files from /home or what?

---

### Post by Evil Wayz on 2016-05-16
I got to 16.04 from an upgrade from 14.04.4 which quit in the middle, and I had to use a live disk to finish it.  Kept my old home directory.  I was already using Cinnamon 3.0 with 14.04.4.

---

### Post by peter228 on 2016-05-17
hmm.. I think you need to avoid pain.

May I suggest that the best course of action for you would be to perform a fresh install of 16.04?   The reason for me saying this is that you are not really at risk of hard work ..  you kept your /home directory so all your settings are there so what you are facing is simply reinstalling the operating system and that takes no time at all.

The real challenge is that it sounds like something fundamental went wrong during your upgrade since the installer stopped and whilst you were able to complete using the live disk it sounds like there are a number of things not quite right.  Rather than look at each problem in detail it will be faster to make a fresh install and you will not run the risk of fixing individual problems and then discovering more at a later date.

Others reading this thread may of course take a different view ..

---

### Post by Evil Wayz on 2016-05-17
I'm not doing that.  Not only would that mean I'd have to re install all the programs I added, it would also mean I'd have to re do all the tweaks I did to 14.04, which I don't remember.  This is one of my gripes with Ubuntu, and why I won't let my parents install it as their main OS.  I am not scared of the command line, which is why I didn't freak out when my computer crashed mid upgrade and completely borked my system.  I ended up cobbling three tutorials to make it work, which I documented in another thread.  THere should be a recovery program, and there isn't.  "Back up your data and perform a clean install" shouldn't be the answer.

---

### Post by peter228 on 2016-05-17
If you have saved your /home directory then you will also have saved the dot files.  These files store all the tweaks and settings.

Since you know the command line you will find that to install all the programs you need beyond the core install is also easy.  Basically one command listing all programs to install in a string.

If before running the upgrade you had listed your installed software it may have been easier as well.  This is a good move in any event since a list of installed software can be put to good use in the event of hdd failure for example.

Good luck with this.  I am sure that others will come to your rescue.  I still think it will be a lot quicker for you and provide safer foundations to make a fresh install but I also understand your perspective.

---

### Post by Evil Wayz on 2016-05-17
I didn't mean to come off like an unappreciative jerk, im just frustrated with Ubuntu and their upgrade program, which, to date, I have never gotten to work 100% successfully.  And by tweaks that includes ppas and extra libraries and such.  I  also found that certain changes I made to 14.04.4.4 didn't work in 16.04 anymore.  FOr instance I had a remapped audio channel for a defective bluetooth headset that used to connect automatically and reverse channels.

---

### Post by mastablasta on 2016-05-17
new kernel, new drivers. stuff stops working. nothing new.

btrfs and ZFS enable snapshots. there are plenty of backup programs that will enable you to backup and restore. although nothing does the whole system i believe. which is the same in windows when you do the upgrade.

---

### Post by Evil Wayz on 2016-05-17
I've had some success with cloning the entire drive.  

I could live with no weather, since for whatever reason Gnome Weather works from the menu but not in the panel.  

Trying to figure out how to make my Canon digital camera get "seen" by the computer.  I assume a driver went bad or the camera isn't supported anymore.

---

### Post by buzzingrobot on 2016-05-17
Do you see the same issues in Unity, assuming you've installed Cinnamon on a Unity system?

Also, Cinnamon 3 is very new.  It isn't in Canonical repos and it isn't supported by Canonical.

Also, believe there's a setting in Cinnamon to toggle the use of indicators. Is it enabled?

---

### Post by oldrocker99 on 2016-05-17
It is a truism that upgrades just don't always work; I always do a new install and it really doesn't take all that long to install the extra programs.

---

### Post by Evil Wayz on 2016-05-17
I have not used unity since they introduced it without asking anyone.  

I will take the hit, I should have waited for the point release.

I will go check out if this stuff is present in Unity.  The other indicators work, so I'm not sure if that's the problem.

---

### Post by Evil Wayz on 2016-05-17
Ok the bluetooth indicator is present in Unity.  But my-weather-indicator crashes immediately on starting.  Filed report.  Gnome weather works, but not as an applet.  But lunar indicator does.  Camera is still not being recognized. or iat least its not auto mounting.

---

### Post by him610 on 2016-05-17
Yeah, it's a pitch. Ain't it? 
Oftentimes, back in the past, maybe we configured or tweaked something in a unique way - didn't keep notes or a log of what we did then along comes the next release...,and we upgrade. Sometimes, things just happen that way.

It happens to all of us.

---

### Post by mc4man on 2016-05-17
It's been broken numerous times of late. Your best bet currently is to open it from a terminal & manually set your location. When you close the terminal it will close, then log out/in & if you set it to autostart it should be ok.
If it survives the 1st refresh (default 1 hr.) then it should be ok.
To open from cli  - 
/opt/extras.ubuntu.com/my-weather-indicator/bin/my-weather-indicator

As far as Release upgrades - all ppa's should be purged before doing the upgrade, some, if left are guaranteed to cause issue. (many that will say so clearly on the ppa page.

---

### Post by Evil Wayz on 2016-05-17
> **mc4man said:**
> It's been broken numerous times of late. Your best bet currently is to open it from a terminal & manually set your location. When you close the terminal it will close, then log out/in & if you set it to autostart it should be ok.
If it survives the 1st refresh (default 1 hr.) then it should be ok.
To open from cli  - 
/opt/extras.ubuntu.com/my-weather-indicator/bin/my-weather-indicator

I did that, it spit out this output and then did nothing:

```
wolf@shaitan:~$ /opt/extras.ubuntu.com/my-weather-indicator/bin/my-weather-indicator
<gettext.GNUTranslations object at 0x7f0c0785dba8>
#####################################################
System: Linux
Machine: x86_64
Node: shaitan
Release: 4.4.0-22-generic
Version: #40-Ubuntu SMP Thu May 12 22:03:46 UTC 2016
Platform: Linux-4.4.0-22-generic-x86_64-with-Ubuntu-16.04-xenial
My-Weather-Indicator version: 0.8.1-0extras16.04.1
#####################################################

****** Requesting timezone identificacion
** OWM **
4160021 -81.6851 30.3246
1
***** refreshing weather *****
<urlopen error unknown url type: https>
--- Updating data in location 0 ---
****** Updating weather
****** Calculating rawOffset
-------------------------------------------------------
OpenWeatherMap Weather Service url:http://api.openweathermap.org/data/2.5/weather?id=4160021&appid=4516154e5c8a6494e7e13b550408c863
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
OpenWeatherMap Weather Service url:http://api.openweathermap.org/data/2.5/weather?id=4160021&appid=4516154e5c8a6494e7e13b550408c863
-------------------------------------------------------
****** Updated weather
{'current_conditions': {'wind_condition': '1 knots (SEBE)', 'condition': 'light rain', 'dusk': '20:42', 'precip_today': None, 'dawn_time': '06:05', 'sunrise_time': '06:31', 'wind_icon': 'mwi-wind11.png', 'windchill': 0.0, 'isday': False, 'dawn': '06:05', 'sunset_time_utc': '00:15', 'condition_icon_dark': 'mwid-rain.png', 'condition_icon_light': 'mwil-rain.png', 'precip_1hr': None, 'solarradiation': None, 'moon_icon': 'mwi-moon11.png', 'rawOffset': -4.0, 'cloudiness': '100 %', 'condition_text': 'Rain', 'feels_like': '70', 'sunset': '20:15', 'sunrise': '06:31', 'moon_phase': 'Waxing Gibbous', 'condition_image': 'mwig-rain.png', 'sunrise_time_utc': '10:31', 'UV': None, 'pressure': '30.4 inches of mercury', 'sunset_time': '20:15', 'dew_point': '70', 'temperature': '70', 'dusk_time': '20:42', 'humidity': '100 %', 'heat_index': 0, 'visibility': None}, 'ok': True, 'forecast_information': {'postal_code': '', 'city': '...', 'unit_system': 'SI', 'longitude_e6': '', 'current_date_time': '', 'latitude_e6': '', 'forecast_date': ''}, 'forecasts': [{'wind_icon': 'mwi-wind14.png', 'condition_icon': 'mwil-rain.png', 'qpf_night': None, 'avehumidity': '100 %', 'qpf_allday': None, 'avewind': '2 knots (SSE)', 'snow_day': None, 'high': '69', 'minhumidity': None, 'low': '69', 'cloudiness': '92 %', 'maxwind': None, 'condition_text': 'Intensity rain', 'day_of_week': 'Tuesday', 'sunset': '20:15', 'moon_phase': 'Waxing Gibbous', 'condition_image': 'mwig-rain.png', 'snow_night': None, 'moon_icon': 'mwi-moon11.png', 'sunrise': '06:31', 'maxhumidity': None, 'condition': 'heavy intensity rain', 'snow_allday': None, 'qpf_day': None}, {'wind_icon': 'mwi-wind19.png', 'condition_icon': 'mwil-rain.png', 'qpf_night': None, 'avehumidity': '100 %', 'qpf_allday': None, 'avewind': '1 knots (SWBS)', 'snow_day': None, 'high': '72', 'minhumidity': None, 'low': '69', 'cloudiness': '92 %', 'maxwind': None, 'condition_text': 'Intensity rain', 'day_of_week': 'Wednesday', 'sunset': '20:16', 'moon_phase': 'Waxing Gibbous', 'condition_image': 'mwig-rain.png', 'snow_night': None, 'moon_icon': 'mwi-moon11.png', 'sunrise': '06:31', 'maxhumidity': None, 'condition': 'heavy intensity rain', 'snow_allday': None, 'qpf_day': None}, {'wind_icon': 'mwi-wind03.png', 'condition_icon': 'mwil-rain.png', 'qpf_night': None, 'avehumidity': '85 %', 'qpf_allday': None, 'avewind': '2 knots (NEBN)', 'snow_day': None, 'high': '79', 'minhumidity': None, 'low': '71', 'cloudiness': '64 %', 'maxwind': None, 'condition_text': 'Rain', 'day_of_week': 'Thursday', 'sunset': '20:16', 'moon_phase': 'Full Moon', 'condition_image': 'mwig-rain.png', 'snow_night': None, 'moon_icon': 'mwi-moon12.png', 'sunrise': '06:30', 'maxhumidity': None, 'condition': 'light rain', 'snow_allday': None, 'qpf_day': None}, {'wind_icon': 'mwi-wind11.png', 'condition_icon': 'mwil-rain.png', 'qpf_night': None, 'avehumidity': '78 %', 'qpf_allday': None, 'avewind': '2 knots (SEBE)', 'snow_day': None, 'high': '83', 'minhumidity': None, 'low': '74', 'cloudiness': '68 %', 'maxwind': None, 'condition_text': 'Moderate rain', 'day_of_week': 'Friday', 'sunset': '20:17', 'moon_phase': 'Full Moon', 'condition_image': 'mwig-rain.png', 'snow_night': None, 'moon_icon': 'mwi-moon13.png', 'sunrise': '06:30', 'maxhumidity': None, 'condition': 'moderate rain', 'snow_allday': None, 'qpf_day': None}, {'wind_icon': 'mwi-wind23.png', 'condition_icon': 'mwil-rain.png', 'qpf_night': None, 'avehumidity': '0 %', 'qpf_allday': None, 'avewind': '4 knots (WBS)', 'snow_day': None, 'high': '82', 'minhumidity': None, 'low': '73', 'cloudiness': '38 %', 'maxwind': None, 'condition_text': 'Intensity rain', 'day_of_week': 'Saturday', 'sunset': '20:18', 'moon_phase': 'Full Moon', 'condition_image': 'mwig-rain.png', 'snow_night': None, 'moon_icon': 'mwi-moon14.png', 'sunrise': '06:29', 'maxhumidity': None, 'condition': 'heavy intensity rain', 'snow_allday': None, 'qpf_day': None}, {'wind_icon': 'mwi-wind27.png', 'condition_icon': 'mwil-rain.png', 'qpf_night': None, 'avehumidity': '0 %', 'qpf_allday': None, 'avewind': '2 knots (NWBW)', 'snow_day': None, 'high': '84', 'minhumidity': None, 'low': '72', 'cloudiness': '22 %', 'maxwind': None, 'condition_text': 'Rain', 'day_of_week': 'Sunday', 'sunset': '20:18', 'moon_phase': 'Full Moon', 'condition_image': 'mwig-rain.png', 'snow_night': None, 'moon_icon': 'mwi-moon15.png', 'sunrise': '06:29', 'maxhumidity': None, 'condition': 'light rain', 'snow_allday': None, 'qpf_day': None}, {'wind_icon': 'mwi-wind30.png', 'condition_icon': 'mwil-rain.png', 'qpf_night': None, 'avehumidity': '0 %', 'qpf_allday': None, 'avewind': '2 knots (NNW)', 'snow_day': None, 'high': '87', 'minhumidity': None, 'low': '72', 'cloudiness': '14 %', 'maxwind': None, 'condition_text': 'Rain', 'day_of_week': 'Monday', 'sunset': '20:19', 'moon_phase': 'Waning Gibbous', 'condition_image': 'mwig-rain.png', 'snow_night': None, 'moon_icon': 'mwi-moon16.png', 'sunrise': '06:28', 'maxhumidity': None, 'condition': 'light rain', 'snow_allday': None, 'qpf_day': None}], 'update_time': 1463534754.0282488}

(my-weather-indicator:5130): Gtk-WARNING **: Theme file for default has no name


(my-weather-indicator:5130): Gtk-WARNING **: Theme file for default has no directories

--- End of updating data in location 0 ---
```

> As far as Release upgrades - all ppa's should be purged before doing the upgrade, some, if left are guaranteed to cause issue. (many that will say so clearly on the ppa page.

This I actually did.  But then I couldn't remember what ppa went with what. I ended up using y-ppa-manager, and its a good little program, tells you what ppas are valid in your new upgrade and such.

---

