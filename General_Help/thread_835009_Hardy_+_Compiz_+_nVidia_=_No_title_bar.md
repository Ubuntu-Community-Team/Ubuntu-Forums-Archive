---
title: "Hardy + Compiz + nVidia = No title bar"
date: 2008-06-20
forum: General Help
---

### Post by pwhitted on 2008-06-20
I'm a Linux/Ubuntu NOOB. Running an HP Pavilion zd7010 with the nVidia GeForce4 448 Go card, with driver version 96.43.05. It had been working fine with Extra Visual Effects enabled, but I was exploring how to use Compiz. I followed the installation/activation instructions on the Compiz site ([http://compiz.org/How_to_compile_and_run_Compiz_for_nvidia_card_users](http://compiz.org/How_to_compile_and_run_Compiz_for_nvidia_card_users)). After the step that told me to run this in the terminal window:
```
compiz --replace gconf & gtk-window-decorator --replace &
```
I no longer had title bars, I can no longer see the menu bar on most apps, and ALT+TAB doesn't toggle me through open windows. The only way I can get back is to disable Visual Effects. I found a thread that described this problem and said to install xserver-xgl, but that just hosed me, so I had to uninstall it. How do I fix this?

---

### Post by Kabezon on 2008-06-20
Compiz is already installed by default since the release of Gutsy Gibbon (7.10); there was no need to install it some other way. All you needed to do was to install the CompizConfig Settings Manager (sudo apt-get compizconfig-settings-manager).

Also, make sure your gpu drivers are the right ones (Do this before trying anything else, it might fix it). It's a lot easier if you just use [Envy]("http://www.albertomilone.com/nvidia_scripts1.html") to install them; two clicks an it will do it all for you. Let envy automatically configure X at the end, and then restart your machine.

---

### Post by pwhitted on 2008-06-21
I was pretty sure I was already using the correct nVidia driver, but I figured I'd go ahead and give envy a shot. It didn't auto-detect my card, so I tried all three drivers installed manually. THe middle one is the one I was already running. The other two wouldn't let me set resolution to 1440x900, so I went back to the one I was running before. I guess I just don't get special effects until somebody comes up for a fix for this.

---

### Post by startherepodcast on 2008-06-21
Ok, I think the missing title bars are not a graphics card problem or anything but simply a config thing:

First fire up a Terminal and type ```
metacity --replace
``` to get your title bars back to fix the whole thing.

Then get a terminal and type ```
sudo apt-get install fusion-icon
```

This is a little applet that installs itsself into the taskbar, very handy when playing around with compiz.

Right click it, select compiz as a window manager and select your desired window decorator (i.e. get the borders back). I use GTK Window Decorator, it is more ubuntu-like IMO

Hope this works for you!

Leon

---

### Post by Ub1476 on 2008-06-21
The following option is necessary to make window borders visible with nvidia driver versions prior to 100.xx.:

 Option  "AddARGBGLXVisuals"  "True" 

```
gksudo gedit /etc/X11/xorg.conf
```

Add under the section where you find your graphic card.

---

### Post by Victormd on 2008-06-21
Type ALT+F2 and type this:
```
metacity --replace
```
Or if you want to use emerald:
Install it:
```
sudo apt-get install emerald
```
Go to [http://gnome-look.org/](http://gnome-look.org/) and download some nice themes
System>Preferences>Emerald Theme Manager and import the theme you just downloaded
Then Alt+F2 and type:
```
emerald --replace
```
In Hardy, emerald won't startup automatically so you'll need to add it under System>preferences>Sessions, click the ADD button and for the command, type
```
emerald --replace
```

And you're ready to go.

---

