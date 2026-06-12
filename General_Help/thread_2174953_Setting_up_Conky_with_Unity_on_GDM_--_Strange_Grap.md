---
title: "Setting up Conky with Unity on GDM -- Strange Graphics Problems"
date: 2013-09-16
forum: General Help
---

### Post by zia.newversion on 2013-09-16
I started this thread to ask for help in setting up conky on my desktop. I have tried to install conky before, but I have never been able to run it perfectly. I have tried out:
[LIST]
[*]Several tutorials/guides on the internet
[*]Official documentation of Conky
[*]Configs from other users in forums or the internet and
[*]Applications such as ConkyGUI, Conky-Manager etc.
[/LIST]
There are many problems that I encounter. Which I'd like to discuss here step-by-step.

I have a laptop - **Dell Studio XPS 1645** - **Core i7 Q740M**, **4GB** and **ATI Radeon HD 5730**. I have **Ubuntu 13.04** installed. It is *not* a fresh install. I have several packages already installed, including *Gnome-Shell* from the Gnome3-Team ppa. I have *not*, however, installed any propreity graphics drivers yet. I don't know if I should. Anyway, right about an hour ago, I did:
```
$ sudo apt-get install conky-all
$ ### All the apt output, conky-all installed successfully etc etc.
$ conky
```

And It get this <see screenshots attached>.

[[IMG]http://imageshack.us/scaled/thumb/14/70n7.png[/IMG]](http://imageshack.us/photo/my-images/14/70n7.png/)
[[IMG]http://imageshack.us/scaled/thumb/38/n3k9.png[/IMG]](http://imageshack.us/photo/my-images/38/n3k9.png/)
[[IMG]http://imageshack.us/scaled/thumb/203/vp1h.png[/IMG]](http://imageshack.us/photo/my-images/203/vp1h.png/)

The first image reflects the immediate output. Notice how the desktop wallpaper is gone, and replaced by a light-grey (or white) background.
The second image reflects what happens when I drag windows around. This used to happen on Windows Xp whenever it got too slow and I liked to make fun of it. Now it has started happening with Linux. Is there something wrong with graphics?
The third image reflects what happens when I 'Ctrl+C' in the terminal and Conky stops. Notice that the wallpaper has come back up.

*Another thing, maybe related is, sometimes (recently more frequently) when I close or minimize a window, the desktop freezes for some time. The time duration depends. If I press "Ctrl+Alt+T" right when the desktop is frozen, the desktop starts working again and (because I used that shortcut) a console window jumps up. The same happens when I close the window that had just come up. If, instead I do nothing, the desktop stays frozen for anywhere from a few seconds to straight-up 20 minutes. If I drop to a tty and do ```
service gdm restart
```, and log in again, the same happens when I close a window next time! Does that happen to anyone else? Is it related to graphics drivers? Is there a solution? Is it documented somewhere?*

---

### Post by zia.newversion on 2013-09-17
Bump!

---

### Post by zia.newversion on 2013-09-18
I installed the propreity ATI drivers. I'm not facing the same issue anymore. But Conky still cannot draw a translucent window.

---

### Post by mishi2 on 2013-09-18
I'm still figuring Conky out myself, but I did experience the strange issue that's present in your first screenshot. For me, the issue was related to some of the settings in the .conkyrc file. Specifically "own_window_type" had to be set to "normal", if it was set to "desktop" I would experience graphical glitches. 


Here are a few settings in your .conkyrc file that you can add / modify and see if the results are any different. 
```

# set to yes if you want Conky to be forked in the background
background yes


# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_class Conky


# If own_window is yes, you may use type normal, desktop or override
own_window_type normal


# Use pseudo transparency with own_window?
own_window_transparent yes


# If own_window is yes, these window manager hints may be used
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager


# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

  
```

---

### Post by stinkeye on 2013-09-18
> **zia.newversion said:**
> I installed the propreity ATI drivers. I'm not facing the same issue anymore. But Conky still cannot draw a translucent window.
The pic in your first post shows the sample config from **/etc/conky/conky.conf** which is part of the conky install.

What conky draws on your screen is determined by a config file.
When you run **conky** it looks for the hidden config file **.conkyrc** in your home folder.
If this config file doesn't exist, it will load the sample config.

You need to download a config or create your own.
Downloaded configs may require additional fonts and scripts, and editing to your computing environment.

You can download one of my favourite basic conky configs from [**_[COLOR="#B22222"]HERE[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=281865&p=12628640&viewfull=1#post12628640")
In the terminal, run...
```
gedit ~/.conkyrc
```
Copy and paste the config from the link into gedit and save.
A couple of posts down you'll find fonts needed.

For cpu and hard drive temps you may need to install **lm-sensors** and **hddtemp**. See [**_[COLOR="#B22222"]HERE[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=281865&p=12700126&viewfull=1#post12700126")
The lines in the .conkyrc for **hddtemp** and **sensors** will probably need to be edited for your hardware. 

Then open a terminal and enter **conky** to check for any errors.

---

