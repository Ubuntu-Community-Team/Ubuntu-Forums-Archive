---
title: "My computer is freezed!!!!"
date: 2007-07-21
forum: General Help
---

### Post by kic_pp on 2007-07-21
I'm using Ubuntu 7.04.
I've downloaded driver for my graphic card (Nvidia Geforce MX4400) from restricted drivers applet from System-Administration-...

After success installation, I've restarted the computer, then when Ubuntu was booted, my computer has freesed in middle of work.

I have very important presentations in my computer, how can I uninstall this driver.

I can work only 5 or 6 seconds, after thah.....my computer is freesed.

---

### Post by dougfractal on 2007-07-21
press [ctl]+[alt]+[f1] to goto treminal
login
type

```

sudo cp  /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo gedit /etc/X11/xorg.conf

```

change in "section Device"
Driver "nvidia" to Driver "nv"

This will load the os nv driver and not the nvidia driver.



If you still need to uninstall nvidia
```
sudo apt-get remove nvidia-glx-new
```




press [ctl]+[alt]+[f7] to goto graphical

---

### Post by kic_pp on 2007-07-21
> **dougfractal said:**
> press [ctl]+[alt]+[f1] to goto treminal
login
type

```

sudo cp  /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo gedit /etc/X11/xorg.conf

```

change in "section Device"
Driver "nvidia" to Driver "nv"

This will load the os nv driver and not the nvidia driver.



If you still need to uninstall nvidia
```
sudo apt-get remove nvidia-glx-new
```




press [ctl]+[alt]+[f7] to goto graphical

A little problem here.


after writing this line 
```

sudo gedit /etc/X11/xorg.conf

```
On my screen is shown (couldnt show....) and there is something written without encoding in my language Macedonian so I can't understand it.

Then I've written this line 

```
sudo apt-get remove nvidia-glx-new
```
and it was shown that is removed succesfully.
But after logging in, again my computer was freezed 

Another way....?

---

### Post by dougfractal on 2007-07-21
> **dougfractal said:**
> press [ctl]+[alt]+[f1] to goto terminal
login
type

"sudo gedit /etc/X11/xorg.conf"

change in "section Device"
Driver "nvidia" to Driver "nv"

press [ctl]+[alt]+[f7] to goto graphical


should have been 
```
 sudo nano /etc/X11/xorg.conf
```

open in console ctrl+o save,   ctrl+x exit

change in "section Device"
Driver "nvidia" to Driver "nv"

---

