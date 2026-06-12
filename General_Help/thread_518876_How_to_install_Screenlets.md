---
title: "How to install Screenlets?"
date: 2007-08-06
forum: General Help
---

### Post by orbital on 2007-08-06
I've tried to install Screenlets using some repos like

deb [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) feisty screenlets
deb-src [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) feisty screenlets

but it seems there repos are broken. How should I install Screenlets (preferably the newest version of course)? I'm running Feisty with Compiz.

---

### Post by Depressed Man on 2007-08-06
The newest version is .09 (but you'll have to manually install it. No deb yet). 

[http://forum.compiz.org/viewtopic.php?t=358&start=0](http://forum.compiz.org/viewtopic.php?t=358&start=0)

---

### Post by Guitar King on 2007-08-06
How do you compile it? 
I have compiled software before in Vector Linux, but this is my first day running Ubuntu

---

### Post by Depressed Man on 2007-08-06
The read me has the directions. Just have to copy and paste them or type them into the terminal.

---

### Post by Guitar King on 2007-08-06
I am having trouble unpacking it. I am logged in as the user set to root, but it can't unpack it

---

### Post by Depressed Man on 2007-08-06
Is it giving you an error when you unpack it? If your using a GUI try opening it with a GUI compressed file manager. If it says some error it likely means that the file got corrupted when you downloaded it (happens to me when I'm on my home network..the wireless cuts out randomly on my desktop because of the range) so I have to redownload it.

---

### Post by Guitar King on 2007-08-06
ok, thanks for that. I now have it installed but were is it? How do I run the program? running "screenlets" in the terminal renders "bash: run: command not found"

---

### Post by Depressed Man on 2007-08-06
If you choose to make a folder in the menu (instructions were in the read me) then its under applications > screenlets. Then you launch each screenlet you want.

If not, then I think they're in 

/usr/local/share/screenlets/

You want to go into the folder say control, then launch controlscreenlet.py

For convinence sake you can make a script. 

Here's the one I use. 

```
#!/bin/bash
##python -u -O /home/vforviktor/.screenlets/Facebook/FacebookScreenlet.py > /dev/null &
python -u -O /home/vforviktor/.screenlets/NowPlaying/NowPlayingScreenlet.py > /dev/null &
python -u -O /home/vforviktor/.screenlets/TorrentSearch/TorrentSearchScreenlet.py > /dev/null &
python -u -O /home/vforviktor/.screenlets/Weather/WeatherScreenlet.py > /dev/null &
python -u -O /home/vforviktor/.screenlets/Wireless/WirelessScreenlet.py > /dev/null &
python -u -O /usr/local/share/screenlets/Control/ControlScreenlet.py > /dev/null &
python -u -O /usr/local/share/screenlets/Windowlist/WindowlistScreenlet.py > /dev/null &
##python -u -O /home/vforviktor/.screenlets/RDesktop/RDesktopScreenlet.py > /dev/null &
python -u -O /home/vforviktor/.screenlets/Temperature/TemperatureScreenlet.py > /dev/null &

# ...
```

Note you don't have the vforviktor folder (that's mine). Because those are screenlets I got off the compiz forums (not official basically). The ## means that it's a comment line, anything on that line isn't run.

Save the script with gedit (or any other text writing program) in your home directory (access it by typing ~ in the location of say nautilus or whatever file manager you use. And save it as screenlets_start.sh or whatever. Then open a terminal to that location and type in "ch mod x screenlets_start.sh" or whatever you named it. At least I think that's how you make a file executable (sorry I'm still learning myself). 

Then you can click that file and it'll start all the screenlets you listed in there.

---

### Post by Guitar King on 2007-08-06
So my file is in /usr/local/share/screenlets/, however the only file there is "screenletsd" which is a shell script. I would lunch a .py file but this shell script is the only file and lunching it does nothing.

---

### Post by Depressed Man on 2007-08-06
That's odd., if you followed the read me then /usr/local/share/screenlets should've been populated with folders with the individual screenlets inside of each. Try toggling on hidden files (ctrl+h) to see if that helps. 

Though I believe screenletsd is depreciated (no longer used) as of version .09. 

Though I can't think of anything else (I just followed the instructions myself). You could try going on the Compiz Forums ([http://forum.compiz.org](http://forum.compiz.org)) and posting in the screenlets thread for assistance however. I'm sure the people who work on it will be of more help then I have. :(

---

### Post by orbital on 2007-08-09
Okay so now I have screenlets installed, and the default screenlets work just fine. I want to install new ones, but don't really know where to install them to. Anyone?

---

### Post by orbital on 2007-08-09
Never mind I got it working now.

---

### Post by .: Juan :. on 2007-08-10
I can't install this thing. 
Anyone willing to help me?

---

### Post by orbital on 2007-08-11
Just download, unpack and install using the instructions given in README.

[http://forum.compiz-fusion.org/showthread.php?t=323](http://forum.compiz-fusion.org/showthread.php?t=323)

---

### Post by Guitar King on 2007-08-13
bah, they have a stupid forum. I tryed registering but I keep getting an error telling me to email the admin, but there is no email address.

Right now I am running version 0.0.7 and it works fine

---

### Post by Guitar King on 2007-08-14
ok, I have 0.0.9 running now, but how to you add "after market" screenlets to it?

---

### Post by orbital on 2007-08-14
> **Guitar King said:**
> ok, I have 0.0.9 running now, but how to you add "after market" screenlets to it?

Just download, extract and run the Screenlet from where you extracted it.

---

### Post by Guitar King on 2007-08-14
yeah, but that does not work. 

"Cannot open Desktop/Sy...tus/SystemstatusScreenlet.pyc: No application is known for this kind of file."

---

### Post by orbital on 2007-08-14
> **Guitar King said:**
> yeah, but that does not work. 

"Cannot open Desktop/Sy...tus/SystemstatusScreenlet.pyc: No application is known for this kind of file."

Try to run the file SystemstatusScreenlet.py

---

### Post by Guitar King on 2007-08-15
it just gives me a text document

```
#!/usr/bin/env python

#
#SystemStatusScreenlet
#Copyright (C) 2007 Hendrik Kaju <sorcerer@hot.ee>
#
#Added: Fix to the Temperature.
#Fabian Chong <fabian@linuxsig.net>
#
#This program is free software; you can redistribute it and/or
#modify it under the terms of the GNU General Public License
#as published by the Free Software Foundation; either version 2
#of the License, or (at your option) any later version.
#
#This program is distributed in the hope that it will be useful,
#but WITHOUT ANY WARRANTY; without even the implied warranty of
#MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#GNU General Public License for more details.
#
#You should have received a copy of the GNU General Public License
#along with this program; if not, write to the Free Software
#Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA  02110-1301, USA.
#

import screenlets
from screenlets.options import FloatOption, BoolOption, StringOption, FontOption, ColorOption, IntOption
import cairo
import pango
import sys
import re
import gobject
from screenlets import DefaultMenuItem
import os
from os import popen
from time import sleep
import commands

class SystemstatusScreenlet(screenlets.Screenlet):
	"""Shows information about your system"""
	
	# default meta-info for Screenlets
	__name__ = 'SystemStatusScreenlet'
	__version__ = '0.2'
	__author__ = 'Hendrik Kaju'
	__desc__ = 'Shows information about your system'

	# internals
	__timeout = None
	
	#editable options
	font_name = "Free Sans 10"
	update_interval = 10
	netadapter = 'eth0'
	rgba_color = (0.0, 0.0, 0.0, 0.9)
	text_x = 15
	text_y = 25
	show_uptime = True
	show_hostname = True
	show_temperature = False
	temperature_name = "/proc/acpi/thermal_zone/TZS0/temperature"
	show_load = True
	show_downspeed = False
	show_upspeed = False
	show_freemem = True
	show_usedmem = True
	disk_name = ""
	show_diskusage = False
	disk_value = "use percentage"
	
	def __init__(self, **keyword_args):
		screenlets.Screenlet.__init__(self, width=200, height=200, 
			uses_theme=True, **keyword_args)
		self.theme_name = "default"
		self.add_options_group('System', 'SystemStatus options')
		self.add_options_group('Text', 'Text settings.')
		self.add_option(FontOption('Text', 'font_name', 
			self.font_name, 'Default Font', 
			'The default font of the text) ...'))
		self.add_option(IntOption('Text', 'text_x', 
			self.text_x, 'X-Position of Text', 
			'The X-Position of the text-rectangle\'s upper left corner ...', 
			min=0, max=200))
		self.add_option(IntOption('Text', 'text_y', 
			self.text_y, 'Y-Position of Text', 
			'The Y-Position of the text-rectangle\'s upper left corner ...', 
			min=0, max=200))
		self.add_option(ColorOption('Text', 'rgba_color', 
			self.rgba_color, 'Default Color', 
			'The default color of the text (when no Markup is used) ...'))
		self.add_option(BoolOption('System', 'show_uptime', 
			self.show_uptime, 'Show uptime', 
			'Show uptime ...'))
		self.add_option(BoolOption('System', 'show_hostname', 
			self.show_hostname, 'Show hostname', 
			'Show hostname ...'))
		self.add_option(BoolOption('System', 'show_temperature', 
			self.show_temperature, 'Show CPU temperature', 
			'Show CPU temperature ...'))
		self.add_option(StringOption('System', 'temperature_name', 
			self.temperature_name, 'ACPI temperature location', 
			'Location of your ACPI temperature'), realtime=False)
		self.add_option(BoolOption('System', 'show_load', 
			self.show_load, 'Show load average', 
			'Show load average ...'))
		self.add_option(BoolOption('System', 'show_freemem', 
			self.show_freemem, 'Show available memory', 
			'Show available memory ...'))
		self.add_option(BoolOption('System', 'show_usedmem', 
			self.show_usedmem, 'Show used memory', 
			'Show used memory ...'))
		self.add_option(BoolOption('System', 'show_diskusage', 
			self.show_diskusage, 'Show disk status', 
			'Show disk usage/free space/total space...'))
		self.add_option(StringOption('System', 'disk_name', 
			self.disk_name, 'Disk or partition name', 
			'The name of the disk or partition to be monitored ...'), realtime=False)
		self.add_option(StringOption('System', 'disk_value', 
			self.disk_value, "Show disk's", 
			"Disk's attribute to display...", choices=['total space', 'used space', 'free space', 'use percentage']))
		self.add_option(IntOption('System', 'update_interval', 
			self.update_interval, 'Update interval', 
			'The interval for updating info (in seconds)', min=1, max=600))
		self._create_menu()
		self.update_interval = self.update_interval
	
	def __setattr__(self, name, value):
		screenlets.Screenlet.__setattr__(self, name, value)
		if name in ('show_uptime', 'show_temperature', 'temperature_name',
				'show_hostname', 'show_load', 
				'show_usedmem', 'show_freemem',
				'text_x', 'text_y', 'font_name', 
				'rgba_color', 'show_upspeed',
				'show_downspeed', 'show_diskusage',
				'disk_name', 'disk_value'):
			if self.window:
				self.redraw_canvas()
		if name == "update_interval":
			if value > 0:
				self.__dict__['update_interval'] = value
				if self.__timeout:
					gobject.source_remove(self.__timeout)
				self.__timeout = gobject.timeout_add(int(value * 1000), self.update)
			else:
				self.__dict__['update_interval'] = 1
				pass
				
	def on_menuitem_select(self, id):
		"""handle MenuItem-events in right-click menu"""
		if id[:5] == "exec:":
			# execute shell command
			os.system(id[5:] + " &")
				
	def _create_menu(self):
		"""Create menu from a XML file and add default menuitems 
		after the XML menu"""
		self.add_default_menuitems(DefaultMenuItem.XML)
		self.add_default_menuitems()
	
	# timeout-function
	def update(self):
		self.redraw_canvas()
		return True
		
	def get_uptime(self):
		"""Get uptime using 'cat /proc/uptime'"""
		data1 = commands.getoutput("cat /proc/uptime")
		uptime = float( data1.split()[0] )
		days = int( uptime / 60 / 60 / 24 )
		uptime = uptime - days * 60 * 60 * 24
		hours = int( uptime / 60 / 60 )
		uptime = uptime - hours * 60 * 60
		minutes = int( uptime / 60 )
		return str(hours) + " hours and " + str(minutes) + " minutes"
		
	def get_hostname(self):
		"""Get user- and hostname and return user@hostname"""
		user = commands.getoutput("echo $USER")
		hostname = commands.getoutput("hostname")
		return user + "@" + hostname
		
	def get_cputemp(self):
		"""Get CPU temperature using the ACPI proc interface"""
		temperature = commands.getoutput("cat " + self.temperature_name + " | cut -d ' ' -f 14")
		return int(temperature)
		
	def get_load(self):
		"""Get average load"""
		data = commands.getoutput("cat /proc/loadavg")
		load1 = float( data.split()[0] )
		load2 = float( data.split()[1] )
		load3 = float( data.split()[2] )
		return str(load1) + " " + str(load2) + " " + str(load3)
		
	def get_freemem(self):
		"""Get free memory"""
		cached = commands.getoutput("""cat /proc/meminfo | grep Cached | awk 'BEGIN {FS=":"} {print $2}' | awk '{print $1, $9}'""")
		buffers = commands.getoutput("""cat /proc/meminfo | grep Buffers | awk 'BEGIN {FS=":"} {print $2}' | awk '{print $1, $9}'""")
		free = commands.getoutput("""cat /proc/meminfo | grep MemFree | awk 'BEGIN {FS=":"} {print $2}' | awk '{print $1, $9}'""")
		return str(int(cached.split()[0])/1024 + int(buffers)/1024 + int(free)/1024)
		
	def get_usedmem(self):
		"""Get used memory"""
		total = commands.getoutput("""cat /proc/meminfo | grep MemTotal | awk 'BEGIN {FS=":"} {print $2}' | awk '{print $1, $9}'""")
		cached = commands.getoutput("""cat /proc/meminfo | grep Cached | awk 'BEGIN {FS=":"} {print $2}' | awk '{print $1, $9}'""")
		buffers = commands.getoutput("""cat /proc/meminfo | grep Buffers | awk 'BEGIN {FS=":"} {print $2}' | awk '{print $1, $9}'""")
		free = commands.getoutput("""cat /proc/meminfo | grep MemFree | awk 'BEGIN {FS=":"} {print $2}' | awk '{print $1, $9}'""")
		return str(int(total)/1024 - int(cached.split()[0])/1024 - int(buffers)/1024 - int(free)/1024)
		
	def get_diskusage(self):
		"""Get the amount of disk space used"""
		data = commands.getoutput("df | grep " + self.disk_name)
		total = str( data.split()[1] )
		used = str( data.split()[2] )
		free = str( data.split()[3] )
		mountpoint = str( data.split()[5] )
		percentage = str( data.split()[4] )
		if self.disk_value == "total space":
			return [str(int(total)/1024) + " MB total", mountpoint]
		elif self.disk_value == "used space":
			return [str(int(used)/1024) + " MB used", mountpoint]
		elif self.disk_value == "free space":
			return [str(int(free)/1024) + " MB free", mountpoint]
		elif self.disk_value == "use percentage":
			return [percentage + " used", mountpoint]
		
	def on_draw(self, ctx):
		ctx.scale(self.scale, self.scale)
		ctx.set_operator(cairo.OPERATOR_OVER)
		if self.theme:
			self.theme['background.svg'].render_cairo(ctx)
		ctx.save()
		ctx.translate(self.text_x, self.text_y)
		p_layout = ctx.create_layout()
		p_fdesc = pango.FontDescription()
		p_fdesc.set_family_static("Free Sans")
		p_fdesc.set_size(10 * pango.SCALE)
		p_layout.set_font_description(p_fdesc)
		p_layout.set_width(((self.width - self.text_x) * pango.SCALE))
		om = '<span font_desc="'+self.font_name+'">'
		cm = '</span>'
		if self.show_hostname == True:
			hostname = "<b>" + self.get_hostname() + "</b>\n\n"
		else:
			hostname = ""
		if self.show_diskusage == True:
			diskusage = "<b>" + str(self.get_diskusage()[1]) + ": </b>" + str(self.get_diskusage()[0]) + "\n"
		else:
			diskusage = ""
		if self.show_uptime == True:
			uptime = "<b>Uptime:</b> " + self.get_uptime() + "\n"
		else:
			uptime = ""
		if self.show_temperature == True:
			if self.get_cputemp() <= 50:
				temperature = '<b>Temperature: </b>' + str(self.get_cputemp()) + ' C\n'
			elif (self.get_cputemp() >= 50) and (self.get_cputemp() <= 65):
				temperature = '<b>Temperature: </b><span foreground="orange">' + str(self.get_cputemp()) + ' C</span>\n'
			elif self.get_cputemp() > 65:
				temperature = '<b>Temperature: </b><span foreground="red">' + str(self.get_cputemp()) + ' C</span>\n'
		else:
			temperature = ""
		if self.show_load == True:
			load = "<b>Load average:</b> " + self.get_load() + "\n"
		else:
			load = ""
		if self.show_freemem == True:
			freemem = "<b>Memory free:</b> " + self.get_freemem() + " MB\n"
		else:
			freemem = ""
		if self.show_usedmem == True:
			usedmem = "<b>Memory used:</b> " + self.get_usedmem() + " MB\n"
		else:
			usedmem = ""
		if self.show_upspeed == True:
			upspeed = "<b>Upload speed:</b> " + self.get_netspeed()[1] + "\n"
		else:
			upspeed = ""
		if self.show_downspeed == True:
			downspeed = "<b>Download speed:</b> " + self.get_netspeed()[0] + "\n"
		else:
			downspeed = ""
		p_layout.set_markup(om + hostname + uptime \
						+ temperature + load + downspeed \
						+ upspeed + usedmem + freemem + diskusage + cm)
		ctx.set_source_rgba(self.rgba_color[0], 
			self.rgba_color[1], self.rgba_color[2], 
			self.rgba_color[3])
		ctx.show_layout(p_layout)
		ctx.fill()
		ctx.restore()
		
	def on_draw_shape(self,ctx):
		ctx.scale(self.scale, self.scale)
		if self.theme:
			self.theme['background.svg'].render_cairo(ctx)

	
# If the program is run directly or passed as an argument to the python
# interpreter then create a Screenlet instance and show it
if __name__ == "__main__":
	sl = screenlets.create_new_instance('SystemStatusScreenlet')
	sl.main()
```

---

### Post by phonzie on 2007-08-21
Same thing happens to me but only on the SystemStatus fixed screenlet

---

