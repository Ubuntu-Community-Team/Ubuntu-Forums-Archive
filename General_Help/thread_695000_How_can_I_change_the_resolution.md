---
title: "How can I change the resolution?"
date: 2008-02-12
forum: General Help
---

### Post by Leapmanster on 2008-02-12
I Installed PSUbuntu, it all went fine...
only thing is my resolution, its really tiny, I cant see the whole thing, How can I change the resolution? I cant find any tool or anything from what I can get to...
Is it done through something in the background? why is it like this?
I'm completely new to linux in general, so dont roast me alive

thanks in advance,
Daniel

---

### Post by x1a4 on 2008-02-12
Hi,  welcome to the forum. 

Use your GUIs control centre to change resolution. Or just change it by hand.  Start a terminal and open /etc/X11/xorg.conf for editing like so: 

```
sudo nano /etc/X11/xorg.conf
```

and in the "Screen" section remove the resolutions you don't want and restart X like so: 
```
sudo /etc/init.d/gdm restart
```

The part of the /etc/X11/xorg.conf file in question should look something (though not exactly) like this: 
```

Section "Screen"
     Identifier     "Default Screen"
     Device         "GeForce FX 5200"
     Monitor        "DefaultMonitor"
     Defaultdepth   24
     Option         "NvAGP" "3"
     Option         "Accel" "on"
     Option         "RenderAccel" "on"

   ... *(more options here)*

     SubSection     "Display"
          Depth          24
          Modes          "1024x768_75" "1024x768_70" "1024x768" "800x600_75" "800x600_70" "800x600" "640x480"
     EndSubSection
     SubSection     "Display"
          Depth          16
          Modes          "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection      "Display"
          Depth          15
          Modes          "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection      "Display"
         Depth           8
         Modes           "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

---

### Post by Rocket2DMn on 2008-02-12
You should just be able to go to System->Preferences->Screen Resolution and select your preferred size.  If the options aren't listed that you're looking for, you can automatically reconfigure X with
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then restart X with CTRL+ALT+BACKSPACE (make sure everything is saved and closed first as this will restart your GUI.

---

### Post by Leapmanster on 2008-02-13
I dont have any of those subsections...
I dont have any resolutions other than whats on the GUI.
I'm stuck...

---

### Post by Rocket2DMn on 2008-02-13
Ok, you're going to need to reconfigure X manually, so here is a guide to help you: [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760) (it's not too difficult, just takes a few minutes).
If you have any questions, definitely post them.

---

