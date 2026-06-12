---
title: "Nvidia settings reset on startup"
date: 2007-08-07
forum: General Help
---

### Post by daniele.g on 2007-08-07
I'm using Ubuntu 7.04. I enabled the Nvidia driver in the Restricted Drivers panel. Everything works fine, but every time I reboot my computer all the Nvidia-related settings are lost. So i have to run nvidia-settings and manually set the resolution to 1280x960 again.
I exported the xorg.conf file from the nvidia-settings utility and copied it to /etc/X11 (the utility can't save in that directory because it doesn't run as root). Anyway, when i rebooted, all the settings were lost again. The "nvidia-settings --load-config-only" wordaround in Preferences > Sessions doesn't work either.

---

### Post by oldos2er on 2007-08-07
Run nvidia-settings using sudo:

 sudo nvidia-settings

reset the resolution and save it.

 Hope this helps.

---

### Post by hikaricore on 2007-08-07
Nvidia settings must be made manually upon startup.  Even though they are saved. (for some reason)

This is to prevent unbootable systems in cases of misconfiguration.

The best thing to do is to make a bash script like such (**DO NOT USE MY SETTINGS**):

setnvidia.sh
```

#! /bin/bash
nvidia-settings -a GPUOverclockingState=1 -a GPU2DClockFreqs=285,400 -a GPU3DClockFreqs=325,400 -a Gamma=1.5

```

save it somewhere like your home directory, and chmod it to be executable:

```

chmod +x ~/setnvidia.sh
```

Then add it to your startup session.  ^_^

For full details on how to pass settings with nvidia-settings through command line or bash script read the man pages:

```
man nvidia-settings
```

---

### Post by daniele.g on 2007-08-08
> **oldos2er said:**
> Run nvidia-settings using sudo:
 sudo nvidia-settings
reset the resolution and save it.
 Hope this helps.
I already tried. It didn't work.

> **hikaricore said:**
> Nvidia settings must be made manually upon startup.  Even though they are saved. (for some reason)

This is to prevent unbootable systems in cases of misconfiguration.

The best thing to do is to make a bash script like such (**DO NOT USE MY SETTINGS**):

setnvidia.sh
```

#! /bin/bash
nvidia-settings -a GPUOverclockingState=1 -a GPU2DClockFreqs=285,400 -a GPU3DClockFreqs=325,400 -a Gamma=1.5

```

save it somewhere like your home directory, and chmod it to be executable:

```

chmod +x ~/setnvidia.sh
```

Then add it to your startup session.  ^_^

For full details on how to pass settings with nvidia-settings through command line or bash script read the man pages:

```
man nvidia-settings
```

Could you tell me which attribute I should use to set the resolution? I couldn't find it anywhere.

---

### Post by hikaricore on 2007-08-08
> **daniele.g said:**
> 
Could you tell me which attribute I should use to set the resolution? I couldn't find it anywhere.

Actually resolution should be set in your **/etc/X11/xorg.conf** file.

From a terminal:

```

sudo pico /etc/X11/xorg.conf
```

Scroll down to where the "Screen" section is (be sure to see what it's set to 16 or 24 bit colour depth)

Then scroll down to the appropriate depth section like this one:

>     SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection

Add the needed lines in text as needed.  And save the file. Ctrl+o then Ctrl+x to close.

Restart your X session and you should be able to set the resolution from the normal display dialog under Settings.

----

You can also add the correct resolutions with a CLI based walk-through:

```
sudo dpkg-reconfigure xserver-xorg
```


In my personal opinion it's always best to know more than one way to accomplish a task.  ^_^

---

### Post by daniele.g on 2007-08-08
> **hikaricore said:**
> Actually resolution should be set in your **/etc/X11/xorg.conf** file.

From a terminal:

```

sudo pico /etc/X11/xorg.conf
```

Scroll down to where the "Screen" section is (be sure to see what it's set to 16 or 24 bit colour depth)

Then scroll down to the appropriate depth section like this one:



Add the needed lines in text as needed.  And save the file. Ctrl+o then Ctrl+x to close.

Restart your X session and you should be able to set the resolution from the normal display dialog under Settings.

----

You can also add the correct resolutions with a CLI based walk-through:

```
sudo dpkg-reconfigure xserver-xorg
```


In my personal opinion it's always best to know more than one way to accomplish a task.  ^_^

Manually editing the xorg.config file (to set resolution and refresh rate) didn't work at first. Eventually that CLI-based walkthrough was of help.

---

### Post by rdargent on 2008-02-20
Hi, I am facing the same problem : resolution 1440x900 is reset on startup. I have tried the CLI-based walkthrough but it's still the same. So can you tell what you did to solve your problem ?
Maybe the BusId is misconfigured ? What should I look for to set it ? (because lspci give lots of Nvidia !)

---

### Post by rdargent on 2008-03-05
I finally got it !
The login window was using the correct resolution (1440x900) but after login in, the display changed to a lower resolution 800x600. Using System>Admin>Screens and Graphics, I could change the resolution to 1440x900 without any problem, but after each reboot, I had to set it again.
I finally found that the parameter was not set in gdm configuration.
To solve it, I had to set the field /desktop/gnome/screen/default/0/resolution to 1440x900 using gconf-editor.

Now it's working perfectly :)

---

