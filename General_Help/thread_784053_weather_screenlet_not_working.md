---
title: "weather screenlet not working"
date: 2008-05-06
forum: General Help
---

### Post by jontybuntu on 2008-05-06
My weather screenlets aren't working this morning.  No matter which weather screenlet I try to run, they are unable to connect to weather.com.  I can connect to weather.com with my browser, and my weather widgets are working when I boot into windows.  Is anyone else having trouble?

---

### Post by jcrow on 2008-05-06
Nothing works for me either!

---

### Post by poit on 2008-05-06
yup, same here. I guess either weather.com's XML feed is dead or one of the updates intalled in the last day broke the desklet. 

(I'm running Hardy and using the hardy-proposed repositories)

---

### Post by mullens101 on 2008-05-06
Looking at the WeatherScreenlet.py file, the URL it's trying to load is "http://xoap.weather.com/weather/local/17068?cc=*&dayf=10&prod=xoap&par=1003666583&key=4128909340a9b2fc&unit=s&hbhf=12"  If I go to that URL, I get
"<?xml version="1.0" encoding="ISO-8859-1"?>
<error>
  <err type="8">Bad or missing query parameters in request.</err>
</error>"

Looks like either updates broke the screenlets or weather.com has changed required parameters.

---

### Post by mullens101 on 2008-05-06
OK, figured it out ... you need to edit the weatherscreenlet.py file and add "&link=xoap" to the xoap.weather.com URL.  Looks like there's a new required parameter on Weather.com's xoap interface.  So, The above URL becomes ""http://xoap.weather.com/weather/local/17068?cc=*&dayf=10&prod=xoap**&link=xoap**&par=1003666583&key=41 28909340a9b2fc&unit=s&hbhf=12"

---

### Post by halln on 2008-05-06
That fix did nothing on my weather screenlet. Did it work to anybody here?

---

### Post by jontybuntu on 2008-05-06
That worked for me!  I had to reboot after editing the file.  Thanks, Mullens!

---

### Post by MemoryDump on 2008-05-06
I received an email from weather.com stating they were updating their code for feeds. Stuff will break if they aren't updated.

---

### Post by jcrow on 2008-05-06
I added the parameter and it works. my problem was actually with the AWN Weather applet. The fix works for both.
The parameter you need to add is:

xoap&link=

 Just insert it after prod=

---

### Post by Grone1985 on 2008-05-06
You made a little mistake when marking what had to be added... The URL should look like this...

```

http://xoap.weather.com/weather/local/17068?cc=*&dayf=10&prod=**xoap&link=**xoap&par=1003666583&key=41 28909340a9b2fc&unit=s&hbhf=12
```

Thanks!!

---

### Post by LeoSolaris on 2008-05-06
Flawless! I added this little line to both instances of the url in the script and it is working just as smooth as before. 

Thanks!

---

### Post by strabes on 2008-05-06
Where is the weatherscreenlet.py file?

---

### Post by Silvestre on 2008-05-07
Hi,
i am using the **gdesklets** "GoodWeather" and it doesnt work. I added the above mentioned URL and i get an error. :(
The URL is working because it looks like a long xml-File.
Do you know, if **gdesklets** are working with this "workaround"? 
I paste again later.
Thanks a lot.

---

### Post by vandalous03 on 2008-05-07
Hello!
I had the same problem with the clearweather screenlet.i changed the line to the script and unfortunately the screenlet crashed...:confused:
After a few reboots and install/unistall screenlet package/manager the clearweather screenlet didn't start at all and it's not appearing on the desktop...oh man,these bugs!
I really like having screenlets on my desktop and especially the clearweather so if anyone has a solution on this let me know plz!

screenlets version = 0.1
*I 've used clearweather all versions,weather extended,smoothweather but they won't budge anymore!

---

### Post by vandalous03 on 2008-05-07
OK! It seems that smoothweather screenlet works like a charm again so i'll use that instead of clearweather!Afterall smoothweather is as good as clearweather!:guitar:

---

### Post by vandalous03 on 2008-05-07
Man screenlets are really buggy!!!
I once again lost the smoothweather!
What's going on with these weather screenlets???:confused:

Has anyone faced any of these symptoms?

---

### Post by n1cecupoftea on 2008-05-07
I  also cannot get gdesklets GoodWeather working. Can anyone offer a solution for this?

---

### Post by Baltuki on 2008-05-07
> **n1cecupoftea said:**
> I  also cannot get gdesklets GoodWeather working. Can anyone offer a solution for this?

Edit the *__init__.py* file in "/.gdesklets/Sensors/GoodWeather" and add **link=xoap&** to the Weather Source.


"http://xoap.weather.com/weather/local/" \
                     "%(weather_code)s?cc=*&dayf=5&prod=xoap&**link=xoap&**" \
                     "par=1003832479&key=bb12936706a2d601"

---

### Post by crispaul on 2008-05-07
Thanks a lot guys!!! I solved the problem with CrystalWeather screenlet, and now it's working like a charm.

But how about the Weather plugin in Cairo-Dock?  Any of you know where is the file that needs to be edited to insert the new parameters in the Weather URL?

Thanks in advance!

---

### Post by peacewithall on 2008-05-07
And another thanks from me everyone, this was one of those desklets I really rely on.

---

### Post by Silvestre on 2008-05-07
@Baltuki

Thanks. Now it is working.

I use gdesklets Goodweather because it looks better than the weather screenlet.

---

### Post by vandalous03 on 2008-05-07
Hey people.I really need your help here!I'm having a serious problem with the ClearWeather Screenlet.I lanch it from the screenlet manager but it doesn't seem to start and it doesn't appear anywhere on the desktop.
I recently installed the 0.1.1 screenlets version but the problem is still there.I don;t know what to do and clearweather is really usefull...
When i'm trying to launch the ClearWeatherScreenlet.py script(allowed as executable) from the terminal i receive the following message:

CachingBackend: Loading instances from cache
CachingBackend: Loading <ClearWeather1>
Error in screenlets.session.connect_daemon: org.freedesktop.DBus.Error.ServiceUnknown: The name org.screenlets.ScreenletsDaemon was not provided by any .service files
Found a running session of ClearWeather, adding new instance by service.
Error in screenlets.services.get_service_by_name: org.freedesktop.DBus.Error.ServiceUnknown: The name org.screenlets.ClearWeather was not provided by any .service files
Screenlet has already been added to /tmp/screenlets/screenlets.root.running
Loading instances in: /home/vs/.config/Screenlets/ClearWeather/default/
File: ClearWeather1.ini
Creating new instance: 
UPDATING SHAPE
/home/vs/.config/Screenlets/ClearWeather/default/ClearWeather1
LOAD NEW THEME: default
FOUND: /usr/share/screenlets/ClearWeather/themes/default
theme.conf found! Loading option-overrides.
theme.conf loaded: 
Name: Stardock weather icons
Author: Stardock Corporation
Version: 1.0
Info: These weather images are (c) 2003 by Stardock Corporation.  All rights reserved.
UPDATING SHAPE
WARNING - add_default_menuitems and add_menuitems should be set in on_init ,menu values will be displayed incorrectly
WARNING - add_default_menuitems and add_menuitems should be set in on_init ,menu values will be displayed incorrectly
Set options in ClearWeatherScreenlet
LOAD NEW THEME: default
FOUND: /usr/share/screenlets/ClearWeather/themes/default
theme.conf found! Loading option-overrides.
theme.conf loaded: 
Name: Stardock weather icons
Author: Stardock Corporation
Version: 1.0
Info: These weather images are (c) 2003 by Stardock Corporation.  All rights reserved.
UPDATING SHAPE
Screenlet has been initialized.
Restored instances from session 'default' ...
UPDATING SHAPE
UPDATING SHAPE
UPDATING SHAPE
CachingBackend: Saving <#ClearWeather1> :) ...
OK
UPDATING SHAPE 
...etc,etc...!


What do you think is the problem???
Any help would be appreciated,thanx in advance!

---

### Post by Depressed Man on 2008-05-07
I believe the problem may not be the screenlets themselves but weather.com

Since they recently changed something in their code, so most of the weather screenlets, widgets, applets in docks, or even omweather on the n800/n810 don't work.

---

### Post by halln on 2008-05-07
Is there a tutorial for a newbies out there who doesn't know how to open the .py file or where to find the URL to be edited. thnx so much.:confused:

---

### Post by itsjustarumour on 2008-05-07
> **halln said:**
> Is there a tutorial for a newbies out there who doesn't know how to open the .py file or where to find the URL to be edited. thnx so much.:confused:

Hi Halln,

Try here:

> /home/(your username)/.screenlets/Weather

Then right-click on the file, select "Open With", then "Open with another application", then select "Text Editor".  Edit the file, then "Save", then reboot your PC and hopefully it should work...

---

### Post by halln on 2008-05-07
screenshot3.png
this is what happened on your how to. Need more help pls.

---

### Post by halln on 2008-05-07
sori i have to resend my screenshot and this is what happened.(with attachment)

---

### Post by itsjustarumour on 2008-05-07
> **halln said:**
> sori i have to resend my screenshot and this is what happened.(with attachment)

Hmmm, not sure what happened there! I think you were trying to edit the Directory, rather than the WeatherScreenlet.py file contained within it.

Whise has just released an upgraded Screenlets 0.1.1 package though, which fixes the weather screenlet problem.

You can download it here [http://www.gnome-look.org/content/show.php/Screenlets+0.1.1?content=80452]("http://www.gnome-look.org/content/show.php/Screenlets+0.1.1?content=80452")

Hope this helps!

Cheers,

itsjustarumour

---

### Post by halln on 2008-05-07
I did this:
#!/usr/bin/env python

# This application is released under the GNU General Public License 
# v3 (or, at your option, any later version). You can find the full 
# text of the license under [http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt). 
# By using, editing and/or distributing this software you agree to 
# the terms and conditions of this license. 
# Thank you for using free software!

#ClearWeatherScreenlet (c) Whise <helder.fraga@hotmail.com>

import re
from urllib import urlopen
import screenlets
from screenlets.options import StringOption, BoolOption
from Numeric import *
import pygtk
pygtk.require('2.0')
import cairo
import pango
import sys
import gobject
import time
import datetime
import math
import gtk
from gtk import gdk


class ClearWeatherScreenlet(screenlets.Screenlet):
	"""A Weather Screenlet modified from the original to look more clear and to enable the use of icon pack , you can use any icon pack compatible with weather.com , you can find many packs on deviantart.com or http://liquidweather.net/icons.php#iconsets."""
	
	# default meta-info for Screenlets
	__name__ = 'ClearWeatherScreenlet'
	__version__ = '0.4'
	__author__ = 'by Helder Fraga aka Whise based on Weather Screenlet by robgig1088'
	__desc__ = 'A Weather Screenlet modified from the original to look more clear and to enable the use of icon pack , you can use any icon pack compatible with weather.com , you can find many packs on deviantart.com or [http://liquidweather.net/icons.php#iconsets](http://liquidweather.net/icons.php#iconsets).'

	# internals
	__timeout = None

	update_interval = 300
	show_error_message = 1

	lasty = 0
	lastx = 0   ## the cursor position inside the window (is there a better way to do this??)
	over_button = 1

	ZIP = "USNY0996"
	use_metric = True
	show_daytemp = True
	mini = False
	
	latest = []          ## the most recent settings we could get...
	latestHourly = []

	updated_recently = 0 ## don't keep showing the error messages until a connection has been established
			     ## and then lost again.
	
	# constructor
	def __init__(self, text="", **keyword_args):
		#call super (and not show window yet)
		screenlets.Screenlet.__init__(self, width=int(132 * self.scale), height=int(100 * self.scale),uses_theme=True, **keyword_args) 
		# set theme
		self.theme_name = "default"
		# add zip code menu item 
		self.add_menuitem("zipcode", "Zip Code...")
		self.add_menuitem("mini", "Toggle mini-view")
		# init the timeout function
		self.update_interval = self.update_interval
                self.add_options_group('Weather',
                        'The weather widget settings')
                self.add_option(StringOption('Weather', 'ZIP',
                        str(self.ZIP), 'ZIP', 'The ZIP code to be monitored taken from Weather.com'), realtime=False)
		self.add_option(BoolOption('Weather', 'show_error_message', 
			bool(self.show_error_message), 'Show error messages', 
			'Show an error message on invalid location code'))
		self.add_option(BoolOption('Weather', 'use_metric', 
			bool(self.use_metric), 'Use celsius temperature ', 
			'Use the metric system for measuring values'))
		self.add_option(BoolOption('Weather', 'mini',
			bool(self.mini), 'Use mini-mode',
			'Switch to the mini-mode'))
		self.add_option(BoolOption('Weather', 'show_daytemp',
			bool(self.show_daytemp), 'Show 6 day temperature',
			'Show 6 day temperature high/low'))

	
	# attribute-"setter", handles setting of attributes
	def __setattr__(self, name, value):
		# call Screenlet.__setattr__ in baseclass (ESSENTIAL!!!!)
		screenlets.Screenlet.__setattr__(self, name, value)
		# check for this Screenlet's attributes, we are interested in:
		if name == "ZIP":
			self.__dict__[name] = value
			gobject.idle_add(self.update_weather_data)
		if name == "update_interval":
			if value > 0:
				self.__dict__['update_interval'] = value
				if self.__timeout:
					gobject.source_remove(self.__timeout)
				self.__timeout = gobject.timeout_add(value * 1000, self.update)
			else:
				# TODO: raise exception!!!
				pass

	def on_init (self):
		print "Screenlet has been initialized."
		# add default menuitems
		self.add_default_menuitems()	

	def update(self):
		gobject.idle_add(self.update_weather_data)
		
		return True


	def update_weather_data(self):
		temp = self.parseWeatherData()
		temp2 = self.parseWeatherDataHourly()
		
		if temp[0]["where"] == '':    ##did we get any data?  if not...
			if self.show_error_message==1 and self.updated_recently == 1:
				self.show_error()
			self.updated_recently = 0
		else:
			#if temp[0]["where"].find(',') > -1:
			#	temp[0]["where"] = temp[0]["where"][:temp[0]["where"].find(',')]
			self.latest = temp
			self.latestHourly = temp2
			self.updated_recently = 1
			self.redraw_canvas()


	def parseWeatherData(self):
		if self.use_metric:
			unit = 'm'
		else:
			unit = 's'
		data = urlopen('http://xoap.weather.com/weather/local/'+self.ZIP+'?cc=*&dayf=10&prod=xoap&link=xoap&par=1003666583&key=4128909340a9b2fc&unit='+unit).read()
		forecast = []

		dcstart = data.find('<loc ')
		dcstop = data.find('</cc>')     ###### current conditions
		data_current = data[dcstart:dcstop]
		forecast.append(self.tokenizeCurrent(data_current))

		for x in range(10):
			dcstart = data.find('<day d=\"'+str(x))
			dcstop = data.find('</day>',dcstart)   #####10-day forecast
			day = data[dcstart:dcstop]
			forecast.append(self.tokenizeForecast(day))

		return forecast


	def parseWeatherDataHourly(self):
		if self.use_metric:
			unit = 'm'
		else:
			unit = 's'
		data = urlopen('http://xoap.weather.com/weather/local/'+self.ZIP+'?cc=*&dayf=10&prod=xoap&link=xoap&par=1003666583&key=4128909340a9b2fc&unit='+unit+'&hbhf=12').read()
		hforecast = []

		for x in range(8):
			dcstart = data.find('<hour h=\"'+str(x))
			dcstop = data.find('</hour>',dcstart)   ####hourly forecast
			hour = data[dcstart:dcstop]
			hforecast.append(self.tokenizeForecastHourly(hour))

		return hforecast


	def tokenizeForecast(self, data):
	
		day = self.getBetween(data, '<part p="d">', '</part>')
		daywind = self.getBetween(day, '<wind>', '</wind>')
	
		night = self.getBetween(data, '<part p="n">', '</part>')
		nightwind = self.getBetween(night, '<wind>', '</wind>')

		tokenized = {
		'date': self.getBetween(data, 'dt=\"','\"'),
		'day' : self.getBetween(data, 't=\"','\"'),
		'high': self.getBetween(data, '<hi>','</hi>'),
		'low': self.getBetween(data, '<low>','</low>'),	
		'sunr': self.getBetween(data, '<sunr>','</sunr>'),
		'suns' : self.getBetween(data, '<suns>','</suns>'),		
		'dayicon' : self.getBetween(day, '<icon>','</icon>'), 
		'daystate' : self.getBetween(day, '<t>','</t>'), 
		'daywindspeed' : self.getBetween(daywind, '<s>','</s>'), 
		'daywinddir' : self.getBetween(daywind, '<t>','</t>'), 
		'dayppcp' : self.getBetween(day, '<ppcp>','</ppcp>'), 
		'dayhumid' : self.getBetween(day, '<hmid>','</hmid>'),
		'nighticon' : self.getBetween(night, '<icon>','</icon>'), 
		'nightstate' : self.getBetween(night, '<t>','</t>'), 
		'nightwindspeed' : self.getBetween(nightwind, '<s>','</s>'), 
		'nightwinddir' : self.getBetween(nightwind, '<t>','</t>'), 
		'nightppcp' : self.getBetween(night, '<ppcp>','</ppcp>'), 
		'nighthumid' : self.getBetween(night, '<hmid>','</hmid>'),
		}
		return tokenized

	def tokenizeForecastHourly(self, data):
		tokenized = {
		'hour' : self.getBetween(data, 'c=\"','\"'),
		'tmp': self.getBetween(data, '<tmp>','</tmp>'),
		'flik': self.getBetween(data, '<flik>','</flik>'),
		'icon': self.getBetween(data, '<icon>','</icon>')
		}
		return tokenized
	
	def tokenizeCurrent(self, data):
		wind = self.getBetween(data, '<wind>', '</wind>')
		bar = self.getBetween(data, '<bar>', '</bar>')
		uv = self.getBetween(data, '<uv>', '</uv>')

		tokenized = {
		'where': self.getBetween(data, '<dnam>','</dnam>'),
		'time' : self.getBetween(data, '<tm>','</tm>'),
		'sunr': self.getBetween(data, '<sunr>','</sunr>'),
		'suns' : self.getBetween(data, '<suns>','</suns>'),	
		'date' : self.getBetween(data, '<lsup>','</lsup>'),
		'temp' : self.getBetween(data, '<tmp>','</tmp>'),	
		'flik' : self.getBetween(data, '<flik>','</flik>'), 
		'state' : self.getBetween(data, '<t>','</t>'), 
		'icon' : self.getBetween(data, '<icon>','</icon'),
		'pressure' : self.getBetween(data, '<r>','</r>'),
		'windspeed' : self.getBetween(wind, '<s>','</s>'), 
		'winddir' : self.getBetween(wind, '<t>','</t>'), 
		'humid' : self.getBetween(data, '<hmid>','</hmid>'),
		'vis' : self.getBetween(data, '<vis>','</vis>'),
		'dew' : self.getBetween(data, '<dewp>','</dewp>')
		}
		return tokenized		


	def getBetween(self, data, first, last):
		x = len(first)
		begin = data.find(first) +x
		end = data.find(last, begin)
		return data[begin:end]


	def get_icon(self, code):
		if code < 3200:
			weather = str(code)
		
		elif code == 3200:
			weather = "na"
		return weather


	def get_day_or_night(self, weather):
		time = weather[0]["time"].split()[0]
		ampm = weather[0]["time"].split()[1]
		sunset = weather[0]["suns"].split()[0]
		sunrise = weather[0]["sunr"].split()[0]

		hour = time.split(':')[0]
		min = time.split(':')[1]
		risehr = sunrise.split(':')[0]
		risemin = sunrise.split(':')[1]
		sethr = sunset.split(':')[0]
		setmin = sunset.split(':')[1]

		if int(hour) == 12:
			hour = 0
		if ampm == "AM" :
		        if int(risehr) > int(hour) :
		                dark = 1
		        elif int(risehr) < int(hour) :
				dark = 0
		        else :
		                if int(risemin) > int(min) :
        	                	dark = 1
      		          	elif int(risemin) < int(min) :
       	 	                	dark = 0
         		        else :
           				dark = -1

		elif ampm == "PM" :
		        if int(sethr) > int(hour) :
		                dark = 0
		        elif int(sethr) < int(hour) :
		                dark = 1
		        else :
		                if int(setmin) > int(min) :
		                        dark = 0
		                elif int(setmin) < int(min) :
		                        dark = 1
		                else :
		                        dark = -1
		if dark == 1:
			return "moon"
		else:
			return "sun"


	def on_draw(self, ctx):
		weather = self.latest
		hourly = self.latestHourly

		# set size
		ctx.scale(self.scale, self.scale)
		# draw bg (if theme available)
		ctx.set_operator(cairo.OPERATOR_OVER)
		if self.theme:
			if (self.mini == False and weather != []):
				self.theme['weather-bg.svg'].render_cairo(ctx)
			else:
				self.theme['weather-bg-mini.svg'].render_cairo(ctx)
		# draw memory-graph
		if self.theme:
			if (self.theme_name == "glassy"):
				ctx.set_source_rgba(0, 0, 0, 0.8)
			else:
				ctx.set_source_rgba(1, 1, 1, 0.8)

			if weather == []:
				ctx.save()	
				ctx.translate(15, 35)
				p_layout = ctx.create_layout()
				p_fdesc = pango.FontDescription()
				p_fdesc.set_family_static("Sans")
				p_fdesc.set_size(4 * pango.SCALE)
				p_fdesc.set_weight(300)
				p_fdesc.set_style(pango.STYLE_NORMAL)   ####render no info message
				p_layout.set_font_description(p_fdesc)
				p_layout.set_markup('<b>No weather information available</b>')						
				ctx.show_layout(p_layout)
				ctx.restore()
			else:
				ctx.save()
				ctx.translate(-2, 0)
				ctx.scale(.6,.6)
				if weather[0]["icon"]=="-": weather[0]["icon"]="48"
				icon = str(self.get_icon(int(weather[0]["icon"])) )
				self.theme.render(ctx,icon)
				ctx.restore()
				
			#	for x in range(4):
			#		ctx.save()
			#		ctx.translate(28+x*10,3);
			#		icon = str(self.get_icon(int(hourly[x+1]["icon"])) )
			#		ctx.scale(.25,.25)
			#		self.theme.render(ctx,icon)
			#		ctx.restore()

				ctx.save()
				ctx.translate(90,25)
				degree = unichr(176)
				p_layout = ctx.create_layout()
				p_fdesc = pango.FontDescription()
				p_fdesc.set_family_static("Sans")
				p_fdesc.set_size(14 * pango.SCALE)
				p_fdesc.set_weight(300)
				p_fdesc.set_style(pango.STYLE_NORMAL)
				p_layout.set_font_description(p_fdesc)   ######render current temp
				if len(str(weather[0]["temp"])) == 3:
					ctx.translate(-7, 0)
				p_layout.set_markup('<b>' + weather[0]["temp"] + degree +'</b>')							
				ctx.show_layout(p_layout)
				ctx.restore()

				ctx.save()	
				ctx.translate(25  , 50)
				p_layout1 = ctx.create_layout()
				p_fdesc = pango.FontDescription()
				p_fdesc.set_family_static("Sans")
				p_fdesc.set_size(6 * pango.SCALE)
			
			

				p_layout1.set_font_description(p_fdesc)      ### draw location

			
				p_layout1.set_width(int((102* pango.SCALE )))
				p_layout1.set_alignment(pango.ALIGN_RIGHT)
				p_layout1.set_markup('<b>' + weather[0]["where"][:weather[0]["where"].find(',')][:10] +'</b>')

				ctx.show_layout(p_layout1)
			#	ctx.translate(0, 6)
			#	p_layout = ctx.create_layout()
			#	p_fdesc.set_size(3 * pango.SCALE)
			#	p_layout.set_font_description(p_fdesc)
			#	p_layout.set_markup('<b>'+weather[0]["where"][weather[0]["where"].find(',') + 2:]+'</b>')
			#	ctx.show_layout(p_layout)

			#	ctx.translate(0, 8)
			#	p_layout = ctx.create_layout()
			#	p_fdesc = pango.FontDescription()
			#	p_fdesc.set_family_static("Sans")
			#	p_fdesc.set_size(5 * pango.SCALE)
			#	p_fdesc.set_weight(300)
			#	p_fdesc.set_style(pango.STYLE_NORMAL)   ####render today's highs and lows
			#	p_layout.set_font_description(p_fdesc)
			#	p_layout.set_markup('<b>' + "High: "+weather[1]["high"] + degree + "   Low: " +weather[1]["low"] + degree +'</b>')						
			#	ctx.show_layout(p_layout)
				ctx.restore()	


#other stuff text

			
	#			for x in range(4):
	#				ctx.save();
	#				ctx.translate(x*10,0);
	#				p_layout.set_markup('<i>' + ""+hourly[x+1]["hour"] + "h</i>")						
	#				ctx.show_layout(p_layout)
	#				ctx.restore();
	#			ctx.translate(0,5);
	#			for x in range(4):
	#				ctx.save();
	#				ctx.translate(x*10,0);
	#				p_layout.set_markup('<b>' + ""+hourly[x+1]["tmp"] + degree + "</b>")						
	#				ctx.show_layout(p_layout)
	#				ctx.restore();

				
		#		ctx.translate(0, 5)
		#		p_layout.set_markup("p:<b>"+weather[0]["pressure"]+"</b>  h:<b>"+weather[0]["humid"] + "%</b>  w:<b>" +weather[0]["windspeed"] + " m/s</b>")	
		#		ctx.show_layout(p_layout)
				ctx.save() 
				ctx.restore()
				

				if (self.mini == False):
					ctx.save() 
					ctx.translate(14, 65)
					self.theme['day-bg.svg'].render_cairo(ctx)   ###render the days background
					p_layout = ctx.create_layout()
					p_fdesc = pango.FontDescription()
					p_fdesc.set_family_static("Monospace")
					p_fdesc.set_size(6 * pango.SCALE)
					p_fdesc.set_weight(300)    ##### render the days of the week
					p_fdesc.set_style(pango.STYLE_NORMAL)
					p_layout.set_font_description(p_fdesc)
					p_layout.set_markup('<b>' +weather[1]["day"][:3] + '</b>')						
					ctx.show_layout(p_layout)
					ctx.translate(20, 0)
					p_layout.set_markup('<b>' +weather[2]["day"][:3] + '</b>')	
					ctx.show_layout(p_layout)
					ctx.translate(20, 0)
					p_layout.set_markup('<b>' +weather[3]["day"][:3] + '</b>')	
					ctx.show_layout(p_layout)
					ctx.translate(20, 0)
					p_layout.set_markup('<b>' +weather[4]["day"][:3] + '</b>')	
					ctx.show_layout(p_layout)
					ctx.translate(20, 0)
					p_layout.set_markup('<b>' +weather[5]["day"][:3] + '</b>')
					ctx.show_layout(p_layout)
					ctx.translate(20, 0)
					p_layout.set_markup('<b>' +weather[6]["day"][:3] + '</b>')	
					ctx.show_layout(p_layout)

					ctx.restore()	

				#	ctx.save()	
				#	ctx.translate(0, 50)   ###render the days background
				#	self.theme['day-bg.svg'].render_cairo(ctx)
				#	p_layout = ctx.create_layout()
				#	p_fdesc = pango.FontDescription()
				#	p_fdesc.set_family_static("Monospace")
				#	p_fdesc.set_size(3 * pango.SCALE)
				#	p_fdesc.set_weight(300)    ###render the days of the week (second row)
				#	p_fdesc.set_style(pango.STYLE_NORMAL)
				#	p_layout.set_font_description(p_fdesc)
				#	p_layout.set_markup('<b>' + "  "+weather[4]["day"].center(14)+weather[5]["day"].center(14)+weather[6]["day"].center(12)+'</b>')						
				#	ctx.show_layout(p_layout)
				#	ctx.restore()

					#ctx.save()
					#ctx.translate(36, 28)
					#self.theme['divider.svg'].render_cairo(ctx)
					#ctx.translate(31,0)     ######render the dividers
					#self.theme['divider.svg'].render_cairo(ctx)
					#ctx.restore()
		

					ctx.save()
					ctx.translate(10, 72)
					ctx.scale(.2, .2)
					self.theme.render(ctx,self.get_icon(int(weather[1]["nighticon"]))  )				
					ctx.translate(98,0)
					self.theme.render(ctx,   self.get_icon(int(weather[2]["dayicon"])) )	
					ctx.translate(98,0)
					self.theme.render(ctx,   self.get_icon(int(weather[3]["dayicon"]))  )	
					

				
					ctx.translate(98, 0)
			
					self.theme.render(ctx,   self.get_icon(int(weather[4]["dayicon"]))  )				
					ctx.translate(98,0)
					self.theme.render(ctx,   self.get_icon(int(weather[5]["dayicon"]))  )	
					ctx.translate(98,0)
					self.theme.render(ctx,   self.get_icon(int(weather[6]["dayicon"]))  )	
					ctx.restore()						
					

					p_layout = ctx.create_layout()
					p_fdesc = pango.FontDescription()
					p_fdesc.set_family_static("Monospace")
					p_fdesc.set_size(int(5 * pango.SCALE))
					p_fdesc.set_weight(300)    ###note:: this font needs to be set only once for the next few 
					p_fdesc.set_style(pango.STYLE_NORMAL)  #things we need to do, so I'll do it here.
					p_layout.set_font_description(p_fdesc)	
		
					if self.show_daytemp == True:
						ctx.save()
						ctx.set_source_rgba(0, 0, 0, 1)
						ctx.translate(18,76)
						p_layout.set_markup('<b>' + weather[1]["high"]+degree+'</b>\n'+ weather[1]["low"]+degree)					
						ctx.show_layout(p_layout)   ##day1's temps
					
					
						ctx.restore()
		
						ctx.save()
						ctx.set_source_rgba(0, 0, 0, 1)
						ctx.translate(37, 76)
						p_layout.set_markup('<b>' + weather[2]["high"]+degree+'</b>\n'+ weather[2]["low"]+degree)					
						ctx.show_layout(p_layout)
					
						ctx.restore()

						ctx.save()
						ctx.set_source_rgba(0, 0, 0, 1)
						ctx.translate(57, 76)
						p_layout.set_markup('<b>' + weather[3]["high"]+degree+'</b>\n'+ weather[3]["low"]+degree)					
						ctx.show_layout(p_layout)
					
						ctx.restore()

						ctx.save()
						ctx.set_source_rgba(0, 0, 0, 1)
						ctx.translate(76, 76)
						p_layout.set_markup('<b>' + weather[4]["high"]+degree+'</b>\n'+ weather[4]["low"]+degree)					
						ctx.show_layout(p_layout)
					
						ctx.restore()

						ctx.save()
						ctx.set_source_rgba(0, 0, 0, 1)
						ctx.translate(96, 76)
						p_layout.set_markup('<b>' + weather[5]["high"]+degree+'</b>\n'+ weather[5]["low"]+degree)					
						ctx.show_layout(p_layout)
					
						ctx.restore()

						ctx.save()
						ctx.set_source_rgba(0, 0, 0, 1)
						ctx.translate(116, 76)
						p_layout.set_markup('<b>' + weather[6]["high"]+degree+'</b>\n'+ weather[6]["low"]+degree)					
						ctx.show_layout(p_layout)

						ctx.restore()
						ctx.save()
			

				p_layout2 = ctx.create_layout()
				p_fdesc = pango.FontDescription()
				p_fdesc.set_family_static("Sans")
				p_fdesc.set_size(5 * pango.SCALE)
				p_fdesc.set_weight(300)    ###note:: this font needs to be set only once for the next few 
				p_fdesc.set_style(pango.STYLE_NORMAL)  #things we need to do, so I'll do it here.
				p_layout2.set_font_description(p_fdesc)	
				ctx.translate(68, 28)
				p_layout2.set_markup('<b>' + weather[1]["high"]+degree+'</b>')					
				ctx.show_layout(p_layout2)   ##day1's temps
				ctx.translate(0, 6)
				p_layout2.set_markup('<b>' + weather[1]["low"]+degree+'</b>')
				ctx.show_layout(p_layout2)
				if weather[1]["dayppcp"] <> '0':
					ctx.translate(0, 6)
					p_layout2.set_markup('<i>' + weather[1]["dayppcp"]+'%</i>')
					ctx.show_layout(p_layout2)
				
		
		
					


	def on_draw_shape(self,ctx):
		if self.theme:
			# set size rel to width/height
			self.on_draw(ctx)

	def menuitem_callback(self, widget, id):
		screenlets.Screenlet.menuitem_callback(self, widget, id)
		if id=="zipcode":
			self.show_edit_dialog()
			self.update()
		if id == "mini":
			self.mini = not self.mini
			self.update()
			


	def show_edit_dialog(self):
		# create dialog
		dialog = gtk.Dialog("Zip Code", self.window)
		dialog.resize(300, 100)
		dialog.add_buttons(gtk.STOCK_OK, gtk.RESPONSE_OK, 
			gtk.STOCK_CANCEL, gtk.RESPONSE_CANCEL)
		entrybox = gtk.Entry()
		entrybox.set_text(str(self.ZIP))
		dialog.vbox.add(entrybox)
		entrybox.show()	
		# run dialog
		response = dialog.run()
		if response == gtk.RESPONSE_OK:
			self.ZIP = entrybox.get_text()
			self.updated_recently = 1
		dialog.hide()
		self.update()





	def show_error(self):

		dialog = gtk.Dialog("Zip Code", self.window)
		dialog.resize(300, 100)
		dialog.add_buttons(gtk.STOCK_OK, gtk.RESPONSE_OK)

		label = gtk.Label("Could not reach weather.com.  Check your internet connection and location and try again.")
		dialog.vbox.add(label)
		check = gtk.CheckButton("Do not show this again")
		dialog.vbox.add(check)
		dialog.show_all()
		response = dialog.run()
		if response == gtk.RESPONSE_OK:
			if check.get_active() == True:
				self.show_error_message = 0			
			dialog.hide()


if __name__ == "__main__":
	import screenlets.session
	screenlets.session.create_session(ClearWeatherScreenlet)

Save it and restarted but nothing happen my weather screenlet is still could not reach weather.com.

---

### Post by grndragon57 on 2008-05-07
There is a fix in todays updates.

---

### Post by PoopyTheJ on 2008-05-07
oh now I see grndragon57's post, after I went and changed the links manually. Oh well it works now so I'm happy. Thanks for the info! I was a bit miffed there for a second :)

---

### Post by CosminGC on 2008-05-08
> **Baltuki said:**
> Edit the *__init__.py* file in "/.gdesklets/Sensors/GoodWeather" and add **link=xoap&** to the Weather Source.


"http://xoap.weather.com/weather/local/" \
                     "%(weather_code)s?cc=*&dayf=5&prod=xoap&**link=xoap&**" \
                     "par=1003832479&key=bb12936706a2d601"


Thanks :D

---

### Post by the2ndgenesis on 2008-05-08
I recently re-installed the screenlets package from Synaptic because ClearWeather refused to work, and I've also run a system update to try to correct the issue. It still doesn't work for me, though, nor can I find the .py file to edit ClearWeather's settings...

Anyone have any ideas for me?

---

### Post by niwrip on 2008-05-08
I have a quick question about the SysMonitor Screenlet.  Currently it displays the IP of one of my VMNET interfaces, I would like it to show what my WLAN (eth1) IP addy is and even my eth0.  Any Ideas on how to change this?

---

### Post by strabes on 2008-05-08
> **the2ndgenesis said:**
> I recently re-installed the screenlets package from Synaptic because ClearWeather refused to work, and I've also run a system update to try to correct the issue. It still doesn't work for me, though, nor can I find the .py file to edit ClearWeather's settings...

Anyone have any ideas for me?

Had the same problem as you. Here's how to fix it. First remove the existing Clear Weather screenlet you have added. Download the Clear Weather Screenlet file from [here](http://www.gnome-look.org/content/show.php/Clear+Weather+Screenlet?content=66609). Extract it into ~/.screenlets. The .py file is located here: ~/.screenlets/ClearWeather/ClearWeatherScreenlet.py. Edit it and add the few characters mentioned in several posts in this thread. The easiest way to do this is to simply go to Search > Replace, and search for some text before it, and replace it with the text you searched for + what you're supposed to add. Once you've saved the file, in the Screenlets manager, simply add it again, enter your zip code, and you should be good to go.

Hope this helps.

---

### Post by rpage on 2008-05-08
Thanks for this thread!! Got mine fixed! Nice!

---

### Post by srt4play on 2008-05-08
> **rpage said:**
> Thanks for this thread!! Got mine fixed! Nice!

Same here. But 6-day high/low temperature display doesn't work anymore, any ideas?

---

### Post by 45acp on 2008-05-09
>  Originally Posted by Baltuki  View Post
Edit the __init__.py file in "/.gdesklets/Sensors/GoodWeather" and add link=xoap& to the Weather Source.


"http://xoap.weather.com/weather/local/" \
"%(weather_code)s?cc=*&dayf=5&prod=xoap&link=xoap&" \
"par=1003832479&key=bb12936706a2d601"

Thanks, Much Appreciated.

---

### Post by mpurses on 2008-05-10
Where is the latest 0.4 version?

---

### Post by Emerald Wolf on 2008-05-10
I'm sure glad that I stumbled on this thread.  I'd been banging my head against the wall for the last couple of days trying to get SmoothWeather to work.

Thanks for the hint, worked fine.

Catchya on the Flip Side.....

Emerald Wolf -- has finally got everything back to normal after the 8.10 update...:-&

---

### Post by nynoah on 2008-05-10
> **CosminGC said:**
> Thanks :D


Just wanted to say thanks.  It was a little hard to get this right, but not too hard.  I have my weather screenlet working again thanks to you all.

Noah

---

### Post by srt4play on 2008-05-11
> **srt4play said:**
> Same here. But 6-day high/low temperature display doesn't work anymore, any ideas?

Seems weird to quote myself but I think I was the only one. I got the 6-day high/low working again by restoring my screenlet's python file to the original, and then editing it to remove "prod=xoap&". I got the idea from [here.]("http://liquidweather.net/phpBB2/viewtopic.php?t=649")

---

### Post by iwanridder on 2008-05-12
> **Baltuki said:**
> Edit the *__init__.py* file in "/.gdesklets/Sensors/GoodWeather" and add **link=xoap&** to the Weather Source.


"http://xoap.weather.com/weather/local/" \
                     "%(weather_code)s?cc=*&dayf=5&prod=xoap&**link=xoap&**" \
                     "par=1003832479&key=bb12936706a2d601"

This all makes sense, except: I cannot find the GoodWeather folder anywhere. The desklet is running, but I don't know where it is installed. In the Sensors-folder there are 61 desklets, but no GoodWeather, only GoodTime and Weather.
Tried to search in File System on Goodweather, no hits except for the downloaded tar.gz file. Anyone having the same problem?

Thanx a lot, Iwan

---

### Post by Silvestre on 2008-05-12
it should be there:

```
/home/user/.gdesklets/Sensors/GoodWeather/_init_.py 
```

---

### Post by iwanridder on 2008-05-13
> **Silvestre said:**
> it should be there:

```
/home/user/.gdesklets/Sensors/GoodWeather/_init_.py 
```

Silvestre, thanks a lot. I had to turn on the option to see hidden files. I restarted the desklet and it worked immediately:).
Thanks again!
Greets, Iwan

---

### Post by chadwit on 2008-05-14
A somewhat related question:
I believe my temp is displaying in Celcius. I'd like it to be in Farenheit. In the same file we all had to edit I found "use_metric = True" which I changed to "False" and restarted the screenlet, but it's still the same. I also tried stopping and restarting the screenlet mgr. Any ideas?

Thanks...

---

### Post by john3333 on 2008-05-15
I've tried the solution for getting my Goodweather desklet working, to no avail.
It still won't load.
My _init_.py file is actually in /usr/share/gdesklets/sensors/weather and not in the place you suggest.
Do you have any other ideas???

---

### Post by Mangust22 on 2008-05-16
[http://www.gdesklets.de/index.php?q=desklet/view/232](http://www.gdesklets.de/index.php?q=desklet/view/232)

Is it helpfull link for you? Look at comments (remove old applet and add new using manual installation).

---

### Post by john3333 on 2008-05-16
Thanks for the suggestion.
I tried to follow the directions. 
But where is the ~/.gdesklet where they suggested I place some folders??? Is ~/.gdesklet a folder? How do I find this folder, or get to it?

---

### Post by Baltuki on 2008-05-17
.gdesklets is a hidden folder, you can find it by pressing "Ctrl+H" keys in your home directory.

---

### Post by john3333 on 2008-05-17
Hey, thanks a lot, Mangust22 and Baltuki.
It's working now.  Amazing!

---

### Post by john3333 on 2008-05-17
Sorry, spoke too soon.
It was working for a minute (I think).
But now the temperatures are way off.
It's giving me 118F for the current temperature, etc. and using the Celsius scale it's just as crazy.

---

### Post by MarZiano on 2008-05-19
Thanks guys. Worked like a charm!!!!

---

### Post by asdqwe on 2008-05-21
Hi guise,
my weather screenlet is working, 
but I'm wonderin about something:

At this location all information about my town are shown
[http://de.weather.com/weather/local/GMXX5100?letter=H]("http://de.weather.com/weather/local/GMXX5100?letter=H")

but via ***xoap.weather.com***, I get this crap:
[http://xoap.weather.com/weather/local/GMXX5100]("http://xoap.weather.com/weather/local/GMXX5100")

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<error>
  <err type="2">Invalid location provided.</err>
</error>
```

e.g. 
Berlin looks like this:

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<!--This document is intended only for use by authorized licensees of The Weather Channel. Unauthorized use is prohibited. Copyright 1995-2005, The Weather Channel Interactive, Inc. All Rights Reserved.-->
<weather ver="2.0">
  <head>
    <locale>en_US</locale>
    <form>MEDIUM</form>
    <ut>F</ut>
    <ud>mi</ud>
    <us>mph</us>
    <up>in</up>
    <ur>in</ur>
  </head>
  <loc id="GMXX0007">
    <dnam>Berlin, Germany</dnam>
    <tm>6:07 AM</tm>
    <lat>52.52</lat>
    <lon>13.41</lon>
    <sunr>5:01 AM</sunr>
    <suns>9:06 PM</suns>
    <zone>2</zone>
  </loc>
</weather>
```

I guess there is no solution.

Yours faithfully,
asdqwe

---

### Post by satya_461 on 2008-05-28
Thanks Working like Charm Now! Thanks buddy! U Rock :guitar:

---

### Post by trash on 2008-06-12
Can anybody say why the fix seems to work for some people but does not work for everybody?
Can anybody suggest a weather app. that works, this one(screenlets/clearweather) has been broken for way to long now.

---

### Post by Baltuki on 2008-06-13
> **trash said:**
> Can anybody suggest a weather app. that works, this one(screenlets/clearweather) has been broken for way to long now.

You can try gdesklets/goodweather.
Install gdesklets and download [**goodweather.tar.gz**]("http://gdesklets.zencomputer.ca/GoodWeather.tar.gz").
Open gdesklets and install the downloaded file.
Edit __init__.py file:
```
gedit ~/.gdesklets/Sensors/GoodWeather/__init__.py
```
Find where the Weather code is and add "link=xoap&"
```
WEATHER_SOURCE = "http://xoap.weather.com/weather/local/" \
                     "%(weather_code)s?cc=*&dayf=5&prod=xoap&**link=xoap&**" \
```

This is working for me

---

### Post by psyopper on 2008-06-14
The real solution is to get the updated version of Screenlets. The current version is 0.1.2. The version included with Hardy is 0.0.14. The Clearweather screenlet is fixed in 0.1.2. It also no longer displays the weather.com logo (thankfully).

[http://www.getdeb.net/app/Screenlets]("http://www.getdeb.net/app/Screenlets")

Lots of UI updates including global control of transparency regardless of theme.

---

### Post by wulfhound on 2008-07-07
Does everyone using SmoothWeather get the radar to work? If I switch to it it shows a blank square and becomes unresponsive.

L

---

### Post by trash on 2008-07-18
> **psyopper said:**
> The real solution is to get the updated version of Screenlets. The current version is 0.1.2. The version included with Hardy is 0.0.14. The Clearweather screenlet is fixed in 0.1.2. It also no longer displays the weather.com logo (thankfully).

[http://www.getdeb.net/app/Screenlets]("http://www.getdeb.net/app/Screenlets")

Lots of UI updates including global control of transparency regardless of theme.

Thanks but i am using 0.1.2 (Gutsy), a few days ago i did see the weather in NY but after changing it to CAQC0213 I get the same 'no weather info available.:(... I have tried both fixes found on this forum.

---

### Post by saratchandra on 2008-07-19
[This one]("http://gnome-look.org/content/show.php/Weather+extended?content=76974") is working for me

---

### Post by clay_leblanc on 2008-08-12
wow. adding that little string in the __init__.py file worked for me :D

using xubuntu 8.04

THANKS!

---

### Post by vidgms on 2008-09-10
When I go in to edit the .py file for ClearWeather it says that I do not have the necessary to save the file so I can not save the file so I can not even change the link to update ClearWeather.

Anyone know how to change permissions to save files?

---

### Post by Ecologger on 2008-09-10
you will have to go through the terminal, sudo gedit /usr/share/screenlets/ClearWeather/ClearWeather.py and then you can save it

---

### Post by ft23002 on 2008-09-27
> **srt4play said:**
> Seems weird to quote myself but I think I was the only one. I got the 6-day high/low working again by restoring my screenlet's python file to the original, and then editing it to remove "prod=xoap&". I got the idea from [here.]("http://liquidweather.net/phpBB2/viewtopic.php?t=649")

hehe... Quote Yourself Away...

Did as you suggested and theres now a lot more info being shown.
Using Smoothweather on screenlets manager 0.1.2

Wonder how many people have abandond this thread not knowing the first fix didn't correct it as it should be.

Thank You!

---

### Post by pmuzyk on 2008-10-03
Hi Everyone,
I was messing around with the url
```
"http://xoap.weather.com/weather/local/" \
"[weather_code_here]?cc=*&dayf=5&prod=xoap&link=xoap&" \
"par=1003832479&key=bb12936706a2d601"
```
and came across the fix for people who are in Australia (maybe elsewhere or universally) and want to get the local weather with a lot more details.

Remove "&prod=xoap" from the url and your weather *let will work perfect except for radar maps (can't get them in Sydney anyway?) and other junk.
You will also notice that there are more forecast days in the extended forecast and that the weather details are a lot more detailed. I don't know why this is.

I used "weatherscreenlet v0.1" but this works with all weather.com based *lets.
Cheers

nb. I'm confirming a fix. I am aware of the previous posts. :)

---

### Post by everthonvaladao on 2008-10-20
wow, the fix work to me too!  here is how to quick fix it via sed:

```

sudo sed -i 's/\?cc=/\?link=xoap\&cc=/g' /usr/share/screenlets/ClearWeather/ClearWeatherScreenlet.py

```

:-)

---

### Post by wmichaelb on 2009-02-04
This worked for me in both Hardy 32-bit and Intrepid 64-bit, although I'm not a programmer and have not the faintest clue what it means...:confused:

Replace the WEATHER_SOURCE code in .gdesklets/Sensors/Goodweather/__init__.py with:

WEATHER_SOURCE = "http://xoap.weather.com/weather/local/" \
		     "%(weather_code)s?cc=*&dayf=5&prod=xoap&link=xoap&" \
                     "par=1003832479&key=bb12936706a2d601"

This to me is one of the most useful desklets out there, and I wanted to document the repair. Enjoy!

---

### Post by kvorion on 2009-03-28
Where can I find this file WeatherScreenlet.py?

---

### Post by wmichaelb on 2009-03-29
kvorian: Go to "places" in Nautilus, and open the home/yourname directory. Click on View/Hidden Files, and then go to .gdesklets/sensors/Goodweather, and you should find the WeatherScreenlet.py file to edit.

Since I made this post, I found a "Weather Report" app for the Gnome panel that seems to work out of the box without all this effort. You might try that one as well. Simply right-click on an empty section of the panel on the top of the screen, and click on the "add to panel" entry. You should get a list of available apps and their icons for the Gnome panel. 

Good luck, and let me know if I can be of further help!

---

### Post by imran_khan_79 on 2010-02-05
i just see a grey icon on my top panel... no clouds or sun... however hovering gives the tooltip of the actual condition... help.. i dont know ubuntu 9.10 well that s what i have/ quit windows for good

---

### Post by jcoles on 2010-02-14
Two years later, I have the same problem after an update from 8.10 to 9.04.

I couldn't find .gdesklets on my machine. You do mean ~/.gdesklets, don't you?

People have a bad habit of giving filenames without a full path. 

I'm having the problem with Weather Report 2.26.1.
Any ideas how to fix it.

Is it best to ignore the online updates? They break more than they fix!

---

### Post by wmichaelb on 2010-02-14
jcoles: In order of your questions,

1.) Yes, gdesklets is installed in the hidden file ~/.gdesklets. The program must be installed from the Ubuntu repositories. This is not a Canonical application, so to find it you must add "all open source software" to your Ubuntu software repositories. This is selectable from the "Show" bar in the applications/Add/Remove dialog box. Forgive me if you already know this; I don't know your level of comfort with Ubuntu.

It's been a while now since I worked with gdesklets. I do remember having a good bit of trouble with it. I'm running 9.04 on both my laptop and desktop. In both cases I'm running the panel weather application, and it runs well. To install this one, right click on the top Gnome panel, then on + Add to Panel. You will find a dialog box that drops down. Scroll down to weather, and click to install. The icon will appear on the upper Gnome panel, but indicating 0 degrees C. Right click on the icon, click on properties, and select your location. I've found this application to be much more reliable and consistent than the gDesklets one, which unlike this one seemed to be problematic when I updated. In addition, it offers a much more detailed forward-looking forecast, and the option of a weather radar map. It isn't as pretty, but it works and has good data.

2.) I'm not familiar with Weather Report 2.26.1 by name; is this the panel application, the gdesklet, or ??

Hope this helps. Good luck!
- wmichaelb

---

### Post by jcoles on 2010-02-14
Weather Report is the panel app. It stopped working after the upgrade. I prefer a panel app to something on the desktop.

I installed the gdesklets thing and put up the Weather (PSI) applet. It can't update either. 

I can't use the fixes described here because I can't find the configuration files people are talking about. 

jcoles@thispc:~$ ls -R ~/.gdesklets

/home/jcoles/.gdesklets:
Controls  Displays  displays  gdesklets%3A0.0.pid  logs  registry  sockets

/home/jcoles/.gdesklets/Controls:

/home/jcoles/.gdesklets/Displays:

/home/jcoles/.gdesklets/logs:
gdesklets%3A0.0.log

/home/jcoles/.gdesklets/registry:
config0xf18d9316L.db  controls.reg  shell.config  version

/home/jcoles/.gdesklets/sockets:
%3A0.0

---

### Post by jcoles on 2010-02-14
Added another question, then solved it myself and wanted to delete this message. Used the Edit/Delete button. I can edit, but how do I delete?

---

### Post by wmichaelb on 2010-02-16
jcoles: for gdesklets, try this link:

[http://ubuntuforums.org/showthread.php?t=1158189](http://ubuntuforums.org/showthread.php?t=1158189)

For the panel applet, did you set the location? Right-click on the panel icon, select properties, and then the location tab, and drill down to a location nearby. Other than that, I'm sorry, I'm flat out of ideas, other than to simply reinstall.

Let us know how it turns out.

---

### Post by unc0nn3ct3d on 2012-04-19
went through hell fixing this problem and finally came up with a solution so i'm sharing for future googlers

Need to replace xoap with xml, I ended up finding the solution here: 
[http://blog.netflowdevelopments.com/2012/04/19/weather-app-for-awn-not-working-network-error/](http://blog.netflowdevelopments.com/2012/04/19/weather-app-for-awn-not-working-network-error/)

---

