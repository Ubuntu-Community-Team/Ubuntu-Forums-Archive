---
title: "Error With Wallpapoz"
date: 2007-06-06
forum: General Help
---

### Post by kdarkentity on 2007-06-06
i get this error while trying to run wallpapoz

Failed to execute child process "wallpapoz" (No such file or directory)

what files am i missing and how can i get them?

---

### Post by ikonia on 2007-06-06
Is there any chance you can type in english rather than "street" like "wallpapoz" - the error says "Wallpaper" not "wallpapoz"

If the error does say "wallpapoz" then what 3rd party software have you installed ?

---

### Post by dustigroove on 2007-06-06
First hit under Google says that Wallpapoz is a "Gnome Desktop Wallpaper Configuration Tool". [http://wallpapoz.akbarhome.com/](http://wallpapoz.akbarhome.com/).

Now that's street!  Word to ya mutha.  :p

Unfortunately, never used it and haven't yet tried installing so I'm just as much help. Sorry!

Cheers

---

### Post by ikonia on 2007-06-06
why would you need a tool for changing the wallpaper - right click and select the change desktop wall paper option

---

### Post by kdarkentity on 2007-06-06
Yea to those who dont know (like Ikonia) Wallpapoz (not misspelled) is supposed to be a tool that allows you to have multiple desktop backgrounds on each side of a cube (if you have it enebled) and also it might even allow multiple workspace backgrounds...

---

### Post by dustigroove on 2007-06-06
[SIZE=2][COLOR=Black][FONT=Arial]At the office at the moment so can't play, I'll give it a whirl on the home machine tonight or tomorrow and see if I can be of help.

Cheers

[/FONT][/COLOR][/SIZE]

---

### Post by kdarkentity on 2007-06-06
ok thanks

---

### Post by dustigroove on 2007-06-06
[FONT=Arial][SIZE=2][COLOR=Black]I installed version 0.4.1 from [http://wallpapoz.akbarhome.com/download.html](http://wallpapoz.akbarhome.com/download.html) using the directions in the included README with no issue.

[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Black]```
wget http://wallpapoz.akbarhome.com/files/wallpapoz-0.4.1.tar.bz2

tar -jxvf wallpapoz-0.4.1.tar.bz2

cd wallpapoz-0.4.1

sudo python setup.py install
```[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Black] 
Interesting program. I do like the concept of individual wallpapers for each workspace. However this particular implementation does not work very well, it is quite slow to change the selected wallpaper when changing workspaces, and the options and interface could use some refinement.

Cheers

[/COLOR][/SIZE][/FONT]

---

### Post by kdarkentity on 2007-06-07
i got this error after running the command  sudo python setup.py install 


Checking dependencies...

Required dependencies:

    PyGTK ........................ OK
    Python Glade ................. OK
    !!! Python Imaging Library ...  Not found
    Gnome Python ................. OK

Could not find all required dependencies!
Please install them and try again.

---

### Post by FuturePilot on 2007-06-07
> **kdarkentity said:**
> i got this error after running the command  sudo python setup.py install 


Checking dependencies...

Required dependencies:

    PyGTK ........................ OK
    Python Glade ................. OK
    !!! Python Imaging Library ...  Not found
    Gnome Python ................. OK

Could not find all required dependencies!
Please install them and try again.
Search in Synaptic for python-imaging. It's a python image library and it's most likely not installed.

---

### Post by kdarkentity on 2007-06-08
woohoo thanks to you both i know have wallpapoz working ...its kinda slow but hey it works ...now does anyone know how to make it launch at start-up?

---

### Post by jaimedavila on 2007-06-12
To start wallpapoz automatically:
Start->System->Preferences->Sessions.
Then in the Startup programs tab, click New, and add a new entry with command=/usr/local/bin/daemon_wallpapoz.py

---

### Post by kdarkentity on 2007-06-13
im not sure why but every time i try this the settings do not save

---

### Post by leap on 2007-10-01
you need to hit the restart to get it to start up

---

### Post by kdarkentity on 2007-10-01
wow thanks but i posted that like forever ago and made a how to: to install it lol

---

