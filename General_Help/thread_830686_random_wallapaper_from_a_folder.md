---
title: "random wallapaper from a folder"
date: 2008-06-16
forum: General Help
---

### Post by terrordrone on 2008-06-16
Hi,

I have a folder of wallpapers. I would like the OS to choose a random wallpaper from that folder everytime is boots. 

How do i do this in ubuntu gutsy ?

---

### Post by iaculallad on 2008-06-16
> **terrordrone said:**
> Hi,

I have a folder of wallpapers. I would like the OS to choose a random wallpaper from that folder everytime is boots. 

How do i do this in ubuntu gutsy ?

-Nevermind-

---

### Post by cariboo on 2008-06-16
I use Desktop Drapes for exactly the same purpose. Make sure you have all the repositories selected except for CD-Rom in System-->Adminsitration--Software Sources, The you can either type in a terminal:

```
sudo apt-get install drapes
```

or use System-->Administration-->Synaptic Package Manger.

Jim

---

### Post by terrordrone on 2008-06-16
i installed drapes...

desktop drapes isnt loading... 

my system becomes really slow and my cpu is hogged

mono and mount.ntfs-3g use up most/all of my resources

i tried purging and reinstalling the software.. still the same

---

### Post by stoodleysnow on 2008-06-16
Try wallpapoz (I think it's on Getdeb.net)
Get the newest version and make sure you set up a startup option of 'daemon_wallpapoz'
Then you're laughing, with or without Compiz (but it's far cooler with Compiz, of course)

---

### Post by geirha on 2008-06-16
It's a fairly simple task, so I made a small python-script to do it.

[php]#!/usr/bin/env python
import os,random,gconf

# Change this to the folder where your wallpapers are stored
folder= os.path.expandvars("$HOME/wallpapers")

gconf_path= "/desktop/gnome/background/picture_filename"
wallpapers= os.listdir(folder)
wallpaper= os.path.join(folder, random.choice(wallpapers))
gconf.client_get_default().set_string(gconf_path, wallpaper)
[/php]

Save it some place like $HOME/bin/change_wall.py for example. Make it executable and test that it works for you 
```

$ chmod +x $HOME/bin/change_wall.py
$ $HOME/bin/change_wall.py   # should change wallpaper instantly, and return with no output.
$ 

```

Go to «System -> Preferences -> Sessions» and add it as a «Startup Program»

---

### Post by terrordrone on 2008-06-17
> **geirha said:**
> It's a fairly simple task, so I made a small python-script to do it.

[php]#!/usr/bin/env python
import os,random,gconf

# Change this to the folder where your wallpapers are stored
folder= os.path.expandvars("$HOME/wallpapers")

gconf_path= "/desktop/gnome/background/picture_filename"
wallpapers= os.listdir(folder)
wallpaper= os.path.join(folder, random.choice(wallpapers))
gconf.client_get_default().set_string(gconf_path, wallpaper)
[/php]

Save it some place like $HOME/bin/change_wall.py for example. Make it executable and test that it works for you 
```

$ chmod +x $HOME/bin/change_wall.py
$ $HOME/bin/change_wall.py   # should change wallpaper instantly, and return with no output.
$ 

```

Go to «System -> Preferences -> Sessions» and add it as a «Startup Program»
Thanks

it works... really nice and simple :D

---

### Post by terrordrone on 2008-06-18
```


#!/usr/bin/env python
import os,random,gconf,time

i = 1

# Change this to the folder where your wallpapers are stored
folder= os.path.expandvars("/media/sda6/wallpapers/widescreen")

gconf_path= "/desktop/gnome/background/picture_filename"

while i<=1:
        wallpapers= os.listdir(folder)
        wallpaper= os.path.join(folder, random.choice(wallpapers))
        gconf.client_get_default().set_string(gconf_path, wallpaper)
        time.sleep(1800)


```


changes your wallpaper every 30 mins :guitar::lolflag:

---

