---
title: "Changing GNOME desktop wallpaper through terminal."
date: 2006-10-30
forum: General Help
---

### Post by cvp on 2006-10-30
Basically, I have too many wallpapers to decide on one to stick with, so I'd like Ubuntu to automagically switch out my wallpaper with another random one from my wallpaper collection every hour. I figured that GNOME likely has some variable for the desktop wallpaper that points to a particular file, and so I'd like to know if it's possible to set up a system like this using **cron**.

So I'd be adding "**01 * * * * [command]**" to my crontab. What would the command be? If it's a script, what would I put in the script?

Thanks in advance!
-cvp

---

### Post by tribaal on 2006-10-30
Basically your gnome wallpaper's path is stored in an XML file: /home/<username>/.gconf/desktop/gnome/background/%gconf.xml

You should be able to modify the wanted line with a good grep regexp and a little loop, but I don't know enough bash on top of my head to write it for you (I'm sitting at my step-brother's windows rig).

Good luck :)

- trib'

---

### Post by William the Conquerer on 2006-10-30
well...  if this helps here's an innefficient really old little script that I used at one point to do something like that:

```
#!/usr/bin/env python

import os, commands, random

#directory = commands.getoutput('ls /usr/share/backgrounds')
directory = commands.getoutput('find /home/william/Photos /usr/share/backgrounds/ -iname *.jpg')

directory = directory.split('\n')


selection = random.randrange(0, len(directory), 1)

os.system('gconftool-2 -t str -s /desktop/gnome/background/picture_filename ' + str(directory[selection]))
```

if you save it to a file and run chmod a+x ./FILENAME.py whatever you want the file to be called...  than it should work =)

the only like that actually changes the background is: **gconftool-2 -t str -s /desktop/gnome/background/picture_filename PUT_THE_PATH_TO_IMAGE_HERE**

---

### Post by CatKiller on 2006-10-30
This is a script that I found on this forum when I was looking at this before: ```
#!/usr/bin/env python

BACKGROUND_DIRS = ['/usr/share/backgrounds', '/data/wallpaper', '~/backgrounds']

import os, glob, random, itertools, gconf

files = list(itertools.chain(*[[os.path.join(dirpath, name)
                                for name in filenames]
                               for dirpath, dirnames, filenames in
                               itertools.chain(*[os.walk(os.path.expanduser(d))
                                                 for d in BACKGROUND_DIRS])]))
gconf.client_get_default().set_string(
    '/desktop/gnome/background/picture_filename',
    random.choice(files)) 

``` although I'm currently working with a friend on amendments to it to make it keep a record of which wallpapers you like and which you don't, and weight the choice accordingly.

EDIT: This script runs when I log in, and my crontab looks like ```
  00 * * * * python /home/iain/ranwp.py

```

---

### Post by ~LoKe on 2006-10-30
> **cvp said:**
> Basically, I have too many wallpapers to decide on one to stick with, so I'd like Ubuntu to automagically switch out my wallpaper with another random one from my wallpaper collection every hour. I figured that GNOME likely has some variable for the desktop wallpaper that points to a particular file, and so I'd like to know if it's possible to set up a system like this using **cron**.

So I'd be adding "**01 * * * * [command]**" to my crontab. What would the command be? If it's a script, what would I put in the script?

Thanks in advance!
-cvp

While that may be a good way to learn; the fact of the matter is that there are already applications that will choose random wallpapers for you.  Just look for 'em.

---

### Post by William the Conquerer on 2006-10-31
oh yeah...  that's true.  Check out this program: [http://drapes.mindtouchsoftware.com/](http://drapes.mindtouchsoftware.com/)

I found it a while ago at gnomefiles.org: [http://www.gnomefiles.org/app.php/Desktop_Drapes](http://www.gnomefiles.org/app.php/Desktop_Drapes)

---

