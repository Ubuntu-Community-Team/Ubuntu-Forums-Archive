---
title: "Desktop Changer using Python"
date: 2008-06-13
forum: General Help
---

### Post by Mung the Wicked on 2008-06-13
Hey everybody!

I created this python script that will change your Desktop Wallpaper to a random pic within a specified directory.  The path I had all my pictures in was ~/Pictures/Wallpapers.  I'm using Ubuntu Hardy Heron with Gnome.  I also have compiz-config installed.  I also set this to a cron job that executed the script every 10 minutes.

To clarify something.  I only put pics in the directory Wallpapers - no other files!  If you want to add a component that will sort out only pics, you can figure it out or Google for it.

Open up a text editor(I used Gedit) and paste the code below and save the file as changeWallpaper.py(or any other file name with .py succeeding it).

Here's the script changeWallpaper.py:
#!/usr/bin python

import gconf
import os
import random
from os import path

def changeBG():
	# Get the default client for  - which will be Gnome
	__client__ = gconf.client_get_default ()
	
	# Set the path of the Wallpapers relative to the user folder ~
	Folder = "Pictures/Wallpapers"
	
	# Generation of the path of Wallpapers
	Wallpapers= os.path.join(os.path.expanduser( "~"), Folder)
	
	# Get all the files from the specified directory
	files = os.listdir(Wallpapers)
	
	# Choose a new background randomly
	new_bg = random.choice(files)

	# Get the current background
	current_bg = __client__.get_string ("/desktop/gnome/background/picture_filename")
	
	while (new_bg == current_bg):
		new_bg = random.choice(files)

	# Sets the current wallpaper to the new random picture from specified directory
	__client__.set_string ("/desktop/gnome/background/picture_filename", os.path.join (Wallpapers, new_bg))

if __name__ == "__main__":
    changeBG()

----------------------------------------------------------------------

To create the cron job:
1.) Open terminal
2.) type: crontab -e
3.) The cron editor will open up
4.) type: 0,10,20,30,40,50 * * * * python /home/YOUR_USER_NAME/changeWallpaper.py
5.) Ctrl+K+D to Save the cron job
6.) Ctrl+C

*Notes:
For steps 5 & 6, don't press the + sign.  I mean press those keys simultaneously.  I know, you would think that would be straight-forward enough, but wonders never cease to amaze me.
Obviously in step 4 you could type in ~/changeWallpaper.py

Enjoy!  Hopefully, no one should have any problems.  If you do, someone else in the forum is probably better off helping you.  I'll try if I can.

---

### Post by easybake on 2008-06-13
You can do a similiar thing with a shell script and cron change the wallpaper depending on what time of day it is. You can edit the times below (they are on a 24hour scale) just be sure to change the numbers in both texts.

1.In terminal
```
gedit .change.sh
```

(in the code below simply change the PATH-TO-PICTURE to the proper paths)

2.add this to text editor
```
#!/bin/bash
HOUR=$(date +%H)
case $HOUR in
04|05|06|07)
gconftool -t string -s /desktop/gnome/background/picture_filename PATH-TO-SUNRISE-PICTURE
;;
08|09|10|11|12|13|14|15)
gconftool -t string -s /desktop/gnome/background/picture_filename PATH-TO-DAY-PICTURE
;;
16|17|18 )
gconftool -t string -s /desktop/gnome/background/picture_filename PATH-TO-SUNSET-PICTURE
;;
*)
gconftool -t string -s /desktop/gnome/background/picture_filename PATH-TO-NIGHT-PICTURE
;;
esac
```
Save

3.In terminal
```
gedit .change.cron
```
4.In text editor add this (change it to your homefolder path)
```
 * 4,8,16,19 * * *sh /home/YOUR-HOME-FOLDER/.change.sh
```
Save

5.In SYSTEM>PREFERENCES>SESSIONS
add ```
crontab PATH-TO-YOUR-HOME-FOLDER/.change.cron
```with any name you want

6.In SYSTEM>PREFERENCES>SESSIONS
add ```
PATH-TO-YOUR-HOME-FOLDER/.change.sh
```with any name you want

---

### Post by Mung the Wicked on 2010-04-09
Nice shell script!

---

