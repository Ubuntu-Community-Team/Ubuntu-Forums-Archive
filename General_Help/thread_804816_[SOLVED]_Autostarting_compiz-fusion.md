---
title: "[SOLVED] Autostarting compiz-fusion?"
date: 2008-05-23
forum: General Help
---

### Post by betamaxman on 2008-05-23
Hardy Heron 8.04 64 bit, two xfx geforce gt cards in sli. Compiz runs fine, and I have compiz --replace, and fusion-icon in sessions. However though the icon is on my taskbar at atartup compiz is not started. I must either right click the icon and select 'reload window manager' or run compiz --fusion manually. And all is fine from there. Anyone an idea why compiz is not starting when compiz --replace is listed in sessions and yes compiz --replace is entered as the command. And yes I tried checking  'Extra' in appearance, visual effects, but it is unchecked with each restart.

---

### Post by Forlong on 2008-05-23
What's the output of ```
compiz
``` in a terminal?

---

### Post by betamaxman on 2008-05-23
andy-ubuntu@ubuntu:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0421 (rev a1) (prog-if 00 [VGA controller])
03:00.0 0300: 10de:0421 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /home/andy-ubuntu/wallpapers/Caps

Compiz-check 'command not found'
Compiz works fine it is autostarting it that is trouble. Worked fine with gutsy 64bit. Thanks for trying though.
Oh compiz-check, got it downloading it and will run.

---

### Post by betamaxman on 2008-05-23
Nice scrypt, and thanks.
However it doesn't work for sli.

andy-ubuntu@ubuntu:~$ chmod +x compiz-check
andy-ubuntu@ubuntu:~$ ./compiz-check

 More than one graphics card detected -- sorry, the script can't handle that.
 Aborting.

---

### Post by Forlong on 2008-05-23
Why do you want to have Fusion-Icon loaded on startup?

It obviously interferes with the gconf value.
Try removing everything related to Compiz from your autostart and make sure something is enabled in *System &#8594; Preferences &#8594; Appearance &#8594; Visual Effects*

Then log out and back in and see if it helped.

---

### Post by betamaxman on 2008-05-23
I have enabled 'Extra' System &#8594; Preferences &#8594; Appearance &#8594; Visual Effects several times to no avail. It is cleared again on next startup, will try removing fusion icon.

---

### Post by betamaxman on 2008-05-23
Works when simply restarting X however not if rebooting. Seems compiz will restart with gnome but not with the system.

---

### Post by Forlong on 2008-05-23
Do you still have any other compiz-related programs in your autostart?
What's the output of
```
ls $HOME/.config/autostart
```

---

### Post by betamaxman on 2008-05-23
compiz-2.desktop  fusion-icon.desktop
compiz.desktop    Screenlets Daemon.desktop

---

### Post by Forlong on 2008-05-23
> **betamaxman said:**
> compiz-2.desktop  fusion-icon.desktop
compiz.desktop
Why didn't you remove those?

Did you at least disable them?
```
for i in $(ls $HOME/.config/autostart | grep "compiz\|fusion") ; do grep X-GNOME-Autostart-enabled $HOME/.config/autostart/$i ; done
```

---

### Post by betamaxman on 2008-05-23
Yes I did and tried to use 'aperance, visual efects, Extra to have it autostart it however compizconfig settings would not stick so enabled both again. I will try your suggestions again.

---

### Post by betamaxman on 2008-05-23
Got it, I guess what worked, for me anyway since feisty doesn't seem to with hardy. Thanks again.

---

