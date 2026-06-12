---
title: "Can't get Ubuntu to Save Settings"
date: 2007-06-04
forum: General Help
---

### Post by quaunaut on 2007-06-04
So, every time I start my computer, I consistently have to do two things:

Re-input my secondary DNS, and go into terminal, put in nvidia-settings, and set my resolution to 1680x1050@60hz.

On the DNS page, I don't know how to save that stuff- and it stays there for the rest of my session. My resolution however, I try to hit the button labled "Save to X Configuration", and I figure it saves, and 1 error goes into the terminal in the background: Couldn't save backup.

So, how could I make sure both of these save, so I don't have to put them in every time I start up Ubuntu?

---

### Post by Wim Sturkenboom on 2007-06-04
With regards to the video:
You need root privileges, so you have to use sudo in front of the command.

Else you can add the resolution manually to /etc/X11/xorg.conf (again, use sudo in front of the command that invokes your editor). Look for something like
```
    SubSection     "Display"
        Depth       24
        Modes      "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection

``` and add the required resolution as the first one in the list. There are a couple of lines like this, check for the one where the depth matches your default depth (usually 24).

PS you can make a backup of your original xorg.conf by issuing the following command in a terminal: *sudo cp /etc/X11/xorg.conf /etc/X11/xorg.mybackup.conf*

---

### Post by quaunaut on 2007-06-04
So sudo assumes root? Huh, neat.

I did that with NVidia settings: No error. Gonna restart to check, check the edit. <3

Edit: Before I do that, what command do I input to reinstall the backed up xorg?

---

### Post by Rui Pais on 2007-06-04
> **quaunaut said:**
> So, every time I start my computer, I consistently have to do two things:

Re-input my secondary DNS, and go into terminal, put in nvidia-settings, and set my resolution to 1680x1050@60hz.

On the DNS page, I don't know how to save that stuff- and it stays there for the rest of my session. ...
Hi,
about your secondary DNS. It's not there after a reboot probabily because it's overwritten by dhcp. 
you can try:
```
gksudo gedit /etc/dhcp3/dhclient.conf
```
(or instead of gedit, kate for kubuntu, mousepad for xubuntu) and add a line with:
```
prepend domain-name-servers xxx.xxx.xxx.xxx,XXX.XXX.XXX.XXX;
```
where xxx.... and XXX.... are your 1st and 2nd DNS IPs.

Save and check if its there now.


> **quaunaut said:**
> ... what command do I input to reinstall the backed up xorg?

just copy the backup file:
```
sudo cp /etc/X11/xorg.mybackup.conf /etc/X11/xorg.conf
```

and if you want to keep a copy of the new version:
do first:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.mynewversion.conf
```

---

### Post by quaunaut on 2007-06-04
Oh boy. Now I've got issues.

The DNS thing I've not tried yet, but holy crud, the change with the resolution has been volatile.

So, I restart, and: Nothing, at all, has a title bar. Gaim, Firefox, the freakin' Home Folder, nothin'. Firefox, when maximized, has a space the size of the title bar...at the bottom, empty, showing the desktop.

But here is my problem: I can't access the terminal. I guess I'm gonna have to do it from Recovery Mode, but the Terminal comes up as a big white square. Nothing more.

Oi vei. 3 weeks to get Linux working, and its beginning to go downhill again -.-

---

### Post by Rui Pais on 2007-06-04
you obviously edit something wrongly... it's strange that affects windows bars and terminal, but.

Press Ctrl+Alt+F1 (to F5) should give a console. 
move the backup again as xorg.conf and enter:
```
sudo /etc/init.d/gdm restart
```
to restart X server (or reboot)

Save a copy of your present xorg.conf to us to check it ok?

---

### Post by quaunaut on 2007-06-04
Well, I re-put in the backup, and it didn't fix anything. But its funny to note that its still defaulting me to the new resolution, and when it starts, even has a NVIDIA screen before the login.

And I did that before you asked to save, so I think I lost that thing. ><

---

### Post by Rui Pais on 2007-06-04
> **quaunaut said:**
> Well, I re-put in the backup, and it didn't fix anything. But its funny to note that its still defaulting me to the new resolution, and when it starts, even has a NVIDIA screen before the login.

And I did that before you asked to save, so I think I lost that thing. ><

One question, are using beryl, compiz or the Desktop effects turn on?

Have you restart gdm or rebooted? Can you put the content of your xorg.conf (the actual, since you don't have the new) Can you remember what you changed?

---

### Post by quaunaut on 2007-06-04
The only change I actively put into my xorg file is whatever NVidia had it put in, since I sudo'd the nvidia-settings command.

I can't print it here 'cause I can't access it without a terminal.

Right now, I've got Desktop Effects on, but my Beryl is off(it was on when I first went to restart). Turning Beryl on doesn't fix it.

And for the record, I was rebooting completely.

Turning Desktop Effects back off brings back my menu bars...and yup, Terminal is back. Current xorg:

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Thu Nov  9 17:56:12 P$

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "ViewSonic VX2025wm"
    HorizSync       30.0 - 82.0
    VertRefresh     50.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7900 GT/GTO"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "1680x1050_60 +0+0; 800x600 +0+0; 640x480 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

Edit: Enabling Beryl OR Desktop Effects brings the title bar away.

---

### Post by Rui Pais on 2007-06-04
ok, your window menubar issue is related with composite manager (the desktop effects), not X server directly.

Beryl/compiz are beta products and quite unstable for a lot of users. 
You should play with them always with that on mind, specially If you are not very experimented with Linux. 
You may need to delete some conf file that got broken to allow composite/beryl to work again. I cannot help with that since i don't use such things, but if you search you will find several topics on the subject.

Back to your xorg.conf. Here some changes that can be made:
Replace:
> Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
with:
> Modes      "1600x1050" "1280x1024" "1024x768" "800x600" "640x480"

you can comment the lines (put a symbol # on the beginning of the line):
> Option         "metamodes" "1680x1050_60 +0+0; 800x600 +0+0; 640x480 +0+0"
and:
> Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection 
they are only needed if you have several monitors connected simultaneously.

You can add:
>     Option         "NoLogo" "true"
to the section Device if you don't want to see the Nvidia splash.

And if you still want to use compositor manager adding (again to the section Device):
> Option         "RenderAccel" "true"
   	Option 		"AllowGLXWithComposite" "true" 	
can be good choices (or even solve the issue).

Hope that helps.

---

### Post by quaunaut on 2007-06-04
Okay:

I've got the DNS staying there on restart, and no more Window issues. Just had to put a certain command in the device section for Beryl to let the Window Manager(emerald) do its work:

```
Option         "AddARGBGLXVisuals" "True"

```

And thanks for the earlier DNS settings trick: The Prepend worked perfectly. <3

---

### Post by Rui Pais on 2007-06-04
he he
you have 3 problems solved in one thread ;)

have fun

---

