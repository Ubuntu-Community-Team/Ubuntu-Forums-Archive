---
title: "Help with python script for weather changing background"
date: 2008-06-04
forum: General Help
---

### Post by easybake on 2008-06-04
I don't know much about python to begin with. I wanted to know if there was a way to have my background change based off the results of this page:
[http://xoap.weather.com/weather/local/USIL1204?cc=]("http://xoap.weather.com/weather/local/USIL1204?cc=")

I wanted to know if python could read what is inbetween <t> and <t/> run it through a key like:

if "Mostly Cloudy" = change background to clouds.jpg

Something like this:
> 
#!/usr/bin/python

import urllib, urlparse, string, time
import gconf
 
def get_weather change background:
    url = urlparse.urljoin('http://xoap.weather.com/weather/local/USIL1204?cc=',
                         
    data = urllib.urlopen(url).read()
    start = string.index(data, '<t>') + len('<t>')
    stop = string.index(data, '<t/>', start-1)
	if 'Mostly Cloudy'
		Run: gconftool-2 -t string -s /desktop/gnome/background/cloudy.jpg

Any changing of the script or what the start of a key would look like would be greatly appreciated. I have no idea what I'm doing.> 

---

### Post by tamoneya on 2008-06-04
since the file is an xml file you are probably best off import the xml module.  This should get you down the right track:
[http://oreilly.com/catalog/pythonxml/chapter/ch01.html](http://oreilly.com/catalog/pythonxml/chapter/ch01.html)

---

### Post by easybake on 2008-06-04
> **tamoneya said:**
> since the file is an xml file you are probably best off import the xml module.  This should get you down the right track:
[http://oreilly.com/catalog/pythonxml/chapter/ch01.html](http://oreilly.com/catalog/pythonxml/chapter/ch01.html)

Thanks. I understand that I would probably need to use sax. But I am still having trouble finding anything that I could use like a template or example.

I was looking for something basic since all I need is to gather what is between the <t> and </t> of the page, then compare it to some sort of key with run commands.

Any more ideas?

---

### Post by tamoneya on 2008-06-04
look near the bottom of the page i linked to you.

---

### Post by DaymItzJack on 2008-06-04
[http://ubuntuforums.org/showthread.php?t=669922&highlight=rain+raining](http://ubuntuforums.org/showthread.php?t=669922&highlight=rain+raining)

I remember doing that and got it working for rain/snow, modify it.

---

### Post by easybake on 2008-06-04
> **DaymItzJack said:**
> [http://ubuntuforums.org/showthread.php?t=669922&highlight=rain+raining](http://ubuntuforums.org/showthread.php?t=669922&highlight=rain+raining)

I remember doing that and it working for rain/snow, modify it.

Awesome thanks a lot I'll post the results when I finish it.

---

### Post by easybake on 2008-06-06
I've gotten this far with the script but I can't figure out what I'm doing wrong any help. The coloring of letters stops after <<<"$WEATHER" Any ideas?

> #!/bin/bash
# Set some session specific variables
export DISPLAY=:0
export DBUS_SESSION_BUS_ADDRESS=`cat ~/.dbus/user-dbus-address`

# Get the local weather
WEATHER=`weather --id=KMDW | grep 'Weather'`

# Check if it is raining
echo $WEATHER | grep -q rain

WEATHER = $(tr [:upper:] [:lower:] <<< "$WEATHER")

if [[ $WEATHER == *rain* || $WEATHER == *mist* ]]
then
   if [[ ! -f ~/.raining ]]
   then
      gconftool -t string -s /desktop/gnome/background/picture_filename /home/easybake/Pictures/Background/Rain.jpg
   fi
else
   if [[ -f ~/.raining ]]
   then
      gconftool -t string -s /desktop/gnome/background/picture_filename /home/easybake/Pictures/Background/Cloudy.jpg
   fi
fi

---

### Post by LinuX-M@n1@k on 2008-11-04
[php]import urllib2, re, os

url = 'http://xoap.weather.com/weather/local/USIL1204?cc='
page = urllib2.urlopen(url).readlines()

#check every line in the page and get the first line containing '<t>'
for line in page:
    if line.startswith('<t>'):
        weather = line
        break

weather = re.sub('(\s*<t>|</t>\s*)', '', weather)
print weather  #print it on the screen

#this is not a full list of the weather conditions, only an example
if weather == 'Partly Cloudy':
    #replace fbsetbg with the program you are using to set the wallpaper
    os.system('fbsetbg PartyCloudyWallpaper.jpg')

elif weather == 'Cloudy':
    #etc......
    #repeat for every condition, since there's no 'case' function in Python[/php]
Yea.. I know it's a 5 months old thread.

---

### Post by easybake on 2008-11-10
> **LinuX-M@n1@k said:**
> [php]import urllib2, re, os

url = 'http://xoap.weather.com/weather/local/USIL1204?cc='
page = urllib2.urlopen(url).readlines()

#check every line in the page and get the first line containing '<t>'
for line in page:
    if line.startswith('<t>'):
        weather = line
        break

weather = re.sub('(\s*<t>|</t>\s*)', '', weather)
print weather  #print it on the screen

#this is not a full list of the weather conditions, only an example
if weather == 'Partly Cloudy':
    #replace fbsetbg with the program you are using to set the wallpaper
    os.system('fbsetbg PartyCloudyWallpaper.jpg')

elif weather == 'Cloudy':
    #etc......
    #repeat for every condition, since there's no 'case' function in Python[/php]
Yea.. I know it's a 5 months old thread.

Nicely done, I had completely forgot about it but I'll try it out.

---

