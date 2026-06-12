---
title: "desktop calendar"
date: 2008-05-29
forum: General Help
---

### Post by perillux on 2008-05-29
I have found a script that will change my wallpaper to a random image from a specific folder.
Then I have noticed that the command **cal** prints out a very nice calendar.  So I'm wondering if there is a way to sort of print, or draw, that calendar onto the wallpaper before it gets set.
so I can run it at startup and everyday I will have an up to date calendar on a random wallpaper as my background.

---

### Post by mdebusk on 2008-05-29
> **perillux said:**
> Then I have noticed that the command **cal** prints out a very nice calendar.  So I'm wondering if there is a way to sort of print, or draw, that calendar onto the wallpaper before it gets set.

Look at **[Rainlendar]("http://www.rainlendar.net/")** instead. It displays the calendar on your desktop but does not print it to your wallpaper. The "lite" version is free (There's a "pro" version with additional features for 15 euro, about $23) and there's a debian package available. I've tried it and I liked it, but I just use Google Calendar now.

If you really want calendar wallpaper, I used to use **pcal** (it's in the repositories) to print a monthly calendar, converted that calendar to PNG using ghostscript, and set that file as my wallpaper. It was ugly wallpaper but extremely functional. Probably wouldn't take much to write a shell script to do the job.

If I were to want to do that again, I'd probably print my Google Calendar (in "agenda" view) to PDF, convert that to PNG with ghostscript, and import it using, maybe, ImageMagick to a wallpaper-sized blank image.

---

### Post by perillux on 2008-05-30
I tried rainlendar, it's a really nice program.  But I don't need all the functions.  I really don't even need a calendar, just thought it would look nice ;)

Also, this has sort of become a challenge for me, and I love a good challenge, I figured out how to do it too!  I put the python script below.
There's just 1 problem though, it doesn't indicate the current day in any way, its just the plain calendar, so if anyone can see a way to make any visual improvements, please I'd be delighted to hear it.

Most of this script was made by somebody else, it was to select and set a random wallpaper from the indicated folder whenever the script was run.  I only modified it a tiny bit to add the calendar.

supported file types are:
*jpeg, jpg, png, gif, bmp*

NOTE: In both scripts you must set the path to your wallpapers to be selected at random. It's at the very top of each script.
Also, note that the second script will create a file CALENDAR.bmp which will contain one of the random images converted to .bmp with the calendar drawn on it.

**ORIGINAL SCRIPT: desktop-random.py**
```
#!/usr/bin/python

from os import listdir
from os.path import isfile, splitext
from random import randrange
from subprocess import call
from sys import exit


image_dir = '/CHANGE/THIS/TO/ANY/DIRECTORY/WITH/YOUR/WALLPAPERS/'
#MAKE SURE TO INCLUDE THE '/' AT THE END OF THE ABOVE PATH


def get_image_files():
    image_extensions = ['.jpeg', '.jpg', '.png', 'gif', 'bmp']
    files = listdir(image_dir)

    image_files = []
    for file in files:
        ext = splitext(file)[1]
        if ext.lower() in image_extensions and isfile(image_dir + file):
            image_files.append(file)
    return image_files


def pick_one(image_files):
    index = randrange(0, len(image_files))
    return image_files[index]


def set_key(key, value):
    command = [
        'gconftool',
        '-t',
        'string',
        '-s',
        key,
        value,
    ]
    return call(command)


def change_background(image_file):
    root_key = '/desktop/gnome/background/'
    image_key = 'picture_filename'
    options_key = 'picture_options'
    retval = set_key(root_key + image_key, image_dir + image_file)
    if retval == 0:
        retval = set_key(root_key + options_key, "stretched")
    return retval


image_files = get_image_files()
image_file = pick_one(image_files)
print image_file
exit(change_background(image_file))
```

**MY MODIFIED SCRIPT: desktop-calendar.py**  <--it is currently set for my 1280x800 resolution, check for the commented line (scroll all the way to the bottom) showing where to change the calendars position.
[b]THE BELOW SCRIPT REQUIRES THE "imagemagick" PACKAGE.  INSTALL WITH:
*sudo apt-get install imagemagick*[/b]
```
#!/usr/bin/python

import os
from os import listdir
from os.path import isfile, splitext
from random import randrange
from subprocess import call
from sys import exit


image_dir = '/CHANGE/THIS/TO/ANY/DIRECTORY/WITH/YOUR/WALLPAPERS/'
#MAKE SURE TO INCLUDE THE '/' AT THE END OF THE ABOVE PATH


def get_image_files():
    image_extensions = ['.jpeg', '.jpg', '.png', 'gif', 'bmp']
    files = listdir(image_dir)

    image_files = []
    for file in files:
        ext = splitext(file)[1]
        if ext.lower() in image_extensions and isfile(image_dir + file):
            image_files.append(file)
    return image_files


def pick_one(image_files):
    index = randrange(0, len(image_files))
    return image_files[index]


def set_key(key, value):
    command = [
        'gconftool',
        '-t',
        'string',
        '-s',
        key,
        value,
    ]
    return call(command)


def change_background():
    root_key = '/desktop/gnome/background/'
    image_key = 'picture_filename'
    options_key = 'picture_options'
    retval = set_key(root_key + image_key, image_dir + 'CALENDAR.bmp')
    if retval == 0:
        retval = set_key(root_key + options_key, "stretched")
    return retval


image_files = get_image_files()
image_file = pick_one(image_files)
print image_file
full_path = image_dir + image_file


##############################
# to change the location of the calendar look for the part (below)
# that says '-annotate +875+680' and change the numbers to the screen
# coordinates you desire (-annotate +x+y)
# this prints the calendars SHADOW in black.
##############################


cal_command = 'cal -3 | convert ' + full_path + ' -fill black -font VeraMono.ttf -pointsize 10 -annotate +875+680 @- ' + image_dir + 'CALENDAR.bmp'
os.system(cal_command)



##############################
# below will print the actual calendar on top of the shadow in gray.
# it is slightly offset from the above coordinates, so if set it to:
# -annotate +(x+1)+(y+1)  so for example, if you set the above to:
# -annotate +100+100
# then below you would set it to:
# -annotate +101+101
##############################



cal_command = 'cal -3 | convert ' + image_dir + 'CALENDAR.bmp -fill gray -font VeraMono.ttf -pointsize 10 -annotate +876+681 @- ' + image_dir + 'CALENDAR.bmp'
os.system(cal_command)
exit(change_background())
```

---

### Post by perillux on 2008-06-01
forgot to mentio, you will need a fixed width, monospace, font.

So, any ideas on how I can manage to recognize and highlight the current day?

---

### Post by perillux on 2008-06-01
actually I have an idea.

All I will need is a script or program that will replace all the other days with a space, so it could be run like this possibly:

cal | program

and then it will repleace every character with a space except for the (today is June 1st) character "1" under June.
and since it's using a monospace font I can then repeat the drawing in a different color and it will line up perfectly.

if anyone wants to help write this script/program let me know cause I'm not sure how to go about it at the moment lol

---

### Post by sayakb on 2008-06-01
You may also try to [screenlets]("http://getdeb.net/app/Screenlets"). After installing, goto Application->Accessories->Screenlets to access the daemon.

---

### Post by perillux on 2008-06-02
I did it :) :)

attached screenshot at bottom
so, it selects a random wallpaper from a folder, copies it to CALENDAR.bmp and draws todays calendar on it (3 months) indicating the current day, and then sets that image as the background.

I like it because this is an older laptop so I don't really want an extra program running in the background, it just starts when I log in runs and closes, simple.

Anyways, I didn't include any of the code and stuff here, because I doubt anyone will really want this other than me lol.  But if anyone does just ask and I'll put it all up.

---

### Post by PeterTrotman on 2008-06-02
That's fantastic, I really enjoyed reading that.

I'm a bit of a newbie to Ubuntu but I've had some experience with Python and was able to follow most of your code, but some things I didn't understand. Where did you find the information on how to do all this?

Thanks! :)

---

### Post by perillux on 2008-06-02
well I really don't know python.  I'm good with C++ though, that's why I made a separate program to draw the current day in yellow, because it has to do a lot of string manipulation.

For the python script, I didn't make the original script, I found that online somewhere, all it does is select a random wallpaper and set it.  I studied it for a while and managed to make the modifications that are present in the second script (with no python knowledge at all).  The biggest change I made though is at the very end where I just made it simply run some terminal commands.  So I really can't tell you where to go to learn all that stuff.  But I'm a pretty good programmer so if you have a question I'm sure I could figure it out.

---

### Post by mdebusk on 2008-06-04
> **perillux said:**
> So, any ideas on how I can manage to recognize and highlight the current day?

I like [this version of cal]("http://unicorn.us.com/cal.html") which can be set to display its output in color. It does highlight the current day using (if I recall correctly) ASCII characters. (I'm not home right now to check.) I don't know how your script will handle it, though; looking at the source, it appears to use ANSI escape sequences to create the colors, so you *might* get a stream of nonsense on your wallpaper instead. 

By the way, have you seen [kate.net's calendar wallpaper]("http://www.kate.net/funstuff/calendars.html")? She does a good job. Not what you're looking to accomplish, but not too far off either.

---

### Post by mdebusk on 2008-06-04
> **perillux said:**
> I'm good with C++ though, that's why I made a separate program to draw the current day in yellow, because it has to do a lot of string manipulation.

I hope you'll take a look at the source for the version of "cal" to which I linked, then. IANAP, but it seems to me to be be a simple c program; perhaps you could modify it to do what you're wanting and bypass the extra program altogether.

---

### Post by perillux on 2008-06-05
well I simply used cal to pass a string of text into the imagemagick program.  And it would be difficult to make that read escape characters, it's not really made for text, but does have limited text printing functions.
I might look into those suggestions though, but for now I'm happy with what I have.

---

