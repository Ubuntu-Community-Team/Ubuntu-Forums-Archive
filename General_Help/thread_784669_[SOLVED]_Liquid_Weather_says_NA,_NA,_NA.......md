---
title: "[SOLVED] Liquid Weather says: N/A, N/A, N/A......"
date: 2008-05-06
forum: General Help
---

### Post by HousieMousie2 on 2008-05-06
Anyone else having a sudden issue with Liquid Weather?

It was working just great until yesterday (haven't updated/upgraded/installed/uninstalled/changed settings... nothing) when LW started just saying N/A for everything.

My Liquid Weather configuration still lists my location, had not jacked with it prior to problem, but it isn't getting any data to display.  I tried changing locations but that didn't help either.  Manually asking it to update doesn't help.

Checked my speed/band width, everything checks out normal, haven't been able to find anything via Google that suggests anyone else is asking about this issue or how to address it.

Any ideas?

Thank you for your time!

HousieMousie2

---

### Post by jimv on 2008-05-06
I don't know anything about that particular program, but other weather programs usually pull weather data off of a weather site like weather.com, wunderground.com, etc.  It could be that whatever site that Liquid Weather is pulling data from changed their site layout and in the process broke that program.

---

### Post by HousieMousie2 on 2008-05-06
> **jimv said:**
> I don't know anything about that particular program, but other weather programs usually pull weather data off of a weather site like weather.com, wunderground.com, etc.  It could be that whatever site that Liquid Weather is pulling data from changed their site layout and in the process broke that program.

Good thought, thanks, I will check that out and report back.

---

### Post by strabes on 2008-05-06
I'm also having the same problem with the Clear Weather screenlet, so what jimv said is probably likely.

---

### Post by HousieMousie2 on 2008-05-06
> **strabes said:**
> I'm also having the same problem with the Clear Weather screenlet, so what jimv said is probably likely.


lol I tried switching it from Weather.com to AccuWeather... and it broke. lol  I am laughing because it is just how this day is going... I'll get upset about it later, still too funny right now.  :lolflag:

I tried reinstalling Liquid Weather, but haven't gone to the trouble to try reinstalling Super Karamba... maybe tomorrow.

As for now, it just gets stuck on the "Loading... Please wait" sunflower.

Cheers!

---

### Post by jbg144 on 2008-05-07
Developed the same problem here starting yesterday.  Had not made any changes to my configuration.  (Note that exactly the same problem developed on three different boxes, so the problem does not appear to be a misconfiguration on a single machine.  Running Kubuntu 8.04.
Any help would be most appreciated

Interestingly, I am able to update the weather from the default Berlin Accuweather site
When run from the console, I get the following results (default location, New York)
------------------------snip------------------------------------

Reading config
Reading from Config ...
fontSizeMatrix:
[20, 12, 10, 12, 10]
No such application: 'kxdocker'
Downloading weather in initWidget
"http://xoap.weather.com/weather/local/USNY0996?cc=*&dayf=5&prod=xoap&par=1003666583&key=4128909340a9b2fc"
using weather.com
parsing XML
00
00
unit: kph
Observation:  ( @N/A, 00:00 N/A N/A N/A N/A N/A )
  ( with 0 forecasts )
  icon            : na
  sky             : N/A
  temperature     : 0&#65533;C
  relative_heat   : 0&#65533;C
  dewpoint        : 0&#65533;C
  visibility      : N/A
  uv              : N/A
  pollution       : 0
  wind            : Calm
  wind_speed      : 0 kph
  reverse_wind_arrows : 0
  wind_icon       : calm.png
  humidity        : 0 %
  pressure        : 0
  pressure_change : N/A
  cloud_cover     : 0 %
+++++++++++++++++++Today's Forecast++++++++++++++++++++++++
unit: kph
Forecast:  N/A ( date= )
  icon            : na
  sky             : N/A
  temperature_low : 0&#65533;C
  temperature_high: 0&#65533;C
  uv              : N/A
  pollution       : 0
  wind_speed      : 0 kph
  wind            : Calm
  humidity        : 0 %
  rain            : N/A %
  pressure        : 0
  pressure_change : N/A
  sunrise         : N/A
  sunset          : N/A
unit: kph
Forecast:  N/A ( date= )
  icon            : na
  sky             : N/A
  temperature_low : 0&#65533;C
  temperature_high: 0&#65533;C
  uv              : N/A
  pollution       : 0
  wind_speed      : 0 kph
  wind            : Calm
  humidity        : 0 %
  rain            : N/A %
  pressure        : 0
  pressure_change : N/A
  sunrise         : N/A
  sunset          : N/A
unit: kph
Forecast:  N/A ( date= )
  icon            : na
  sky             : N/A
  temperature_low : 0&#65533;C
  temperature_high: 0&#65533;C
  uv              : N/A
  pollution       : 0
  wind_speed      : 0 kph
  wind            : Calm
  humidity        : 0 %
  rain            : N/A %
  pressure        : 0
  pressure_change : N/A
  sunrise         : N/A
  sunset          : N/A
unit: kph
Forecast:  N/A ( date= )
  icon            : na
  sky             : N/A
  temperature_low : 0&#65533;C
  temperature_high: 0&#65533;C
  uv              : N/A
  pollution       : 0
  wind_speed      : 0 kph
  wind            : Calm
  humidity        : 0 %
  rain            : N/A %
  pressure        : 0
  pressure_change : N/A
  sunrise         : N/A
  sunset          : N/A
unit: kph
Forecast:  N/A ( date= )
  icon            : na
  sky             : N/A
  temperature_low : 0&#65533;C
  temperature_high: 0&#65533;C
  uv              : N/A
  pollution       : 0
  wind_speed      : 0 kph
  wind            : Calm
  humidity        : 0 %
  rain            : N/A %
  pressure        : 0
  pressure_change : N/A
  sunrise         : N/A
  sunset          : N/A
unit: mph
unit: mph
unit: mph
unit: mph
unit: mph
unit: mph
unit: mph
unit: mph
unit: mph
unit: mph
unit: mph
unit: mph
Cities for config menu:
['New York, NY (weather.com)', 'London (BBC)', 'Berlin, Germany(Berlin) (Accuweather)']
Exception in thread Thread-2:
Traceback (most recent call last):
  File "/usr/lib/python2.5/threading.py", line 486, in __bootstrap_inner
    self.run()
  File "liquid_weather.py", line 270, in run
    moon_tmpf = open(theme_path[0] + 'moon_icons/' + moon_icon,'r')
NameError: global name 'moon_icon' is not defined

0.00
unit: kph
00
00

---

### Post by perlluver on 2008-05-07
Weather.com, changed there links and how everything is handled, there is another post here [http://ubuntuforums.org/showthread.php?t=784053&highlight=weather](http://ubuntuforums.org/showthread.php?t=784053&highlight=weather) about the new changes.

---

### Post by jbg144 on 2008-05-07
It appears that weather.com has changed the format of their url.
The following fix seems to work:

1.  Uninstall your current version of liquid-weather from the Superkaramba control panel.  Close superkaramba.  Delete (or rename) the .superkaramba file in your home directory.

2.  You will need to extract the files from the .skz wrapper.  You can do this by changing the name of your lwp file from lwp-14.8.skz to lwp-14.8.zip and then doing "extract here"

3. Open the newly-extracted file "liquidweather.py" in your text editor

4. Locate the following lines:

url =http://xoap.weather.com/weather/local/USNY0996?cc=*&dayf=5&prod=xoap&par=1003666583&key=4128909340a9b2fc'

url_suffix = '?cc=*&dayf=5&prod=xoap&par=1003666583&key=4128909340a9b2fc'

Change them to read:

url = 'http://xoap.weather.com/weather/local/USNY0996?cc=*&dayf=5&prod=xoap&link=xoap&par=1003666583&key=4128909340a9b2fc'

url_suffix = '?cc=*&dayf=5&prod=xoap&link=xoap&par=1003666583&key=4128909340a9b2fc'

5.  Save the modified file

6.  To reinstall the theme, open superkaramba.  Then select the option: "Open Local Theme"  Navigate to the directory where you extracted the original skz file (and which contains the newly-modified liquidweather.py file) file and select: liquid_weather.theme

7.  That should do it!

Thanks to Mullens101 and perlluver for pointing me in the right direction :-)

---

### Post by sergiom99 on 2008-05-07
This wont work: after installing I get a message about some cached files when LW starts

EDIT: Finally got it working. There are a couple of blanks in the urls you posted that wont let LW load. And also I coulnt change the location, so what I did was replace the location code in your url with my location code (got it from weather.com)

and now it works.
here are the lines i used:

```
url = 'http://xoap.weather.com/weather/local/[COLOR="Red"][SIZE="4"]MYCODE[/SIZE][/COLOR]?cc=*&dayf=5&prod=xoap&link=xoap&par=1003666583&key=4128909340a9b2fc'

url_suffix = '?cc=*&dayf=5&prod=xoap&link=xoap&par=1003666583&key=4128909340a9b2fc'

```

Great tip. BTW. Thanks!

---

### Post by anjilslaire on 2008-05-08
There's also an issue with the ***&prod=xoap*** snipped in the config files. There's a post in the LW++ forums, that I've paraphrased into my blog (see my sig) for the solution that I used.

---

### Post by HousieMousie2 on 2008-05-12
> **jbg144 said:**
> It appears that weather.com has changed the format of their url.
The following fix seems to work:

-----------------------------------

7.  That should do it!

Thanks to Mullens101 and perlluver for pointing me in the right direction :-)

Thanks a million, jbgl44! (Also thanks too, Mullens101 and perlluver...)

I had broken Liquid Weather... apparently by asking it to use AccuWeather. :(
Your fix not only gave me back a weather reading (instead of a bunch of N/As) but repaired whatever I did that had SuperKaramba locking up.

You rock! :guitar:

---

