---
title: "Compiz not working at all (everything's missing)"
date: 2008-05-22
forum: General Help
---

### Post by muschen on 2008-05-22
First, when I started compiz, there was no pictures at all. And in system > preferences it wouldn't let me set it to high effects. So I tried reinstalling it.

Now when I start compiz, there's only the search box and the Preferences thing, as you can see on the picture.

I've tried to reinstall it, but that didn't do anything.


Do I really have to reinstall hardy? :(

---

### Post by Sam Lars on 2008-05-22
Have you installed
```
compiz-fusion-plugins-main
compiz-fusion-plugins-extra
```

Also, could you do a
```
compiz --replace
```
in a terminal, and see if it tells you anything about missing plugins?

---

### Post by muschen on 2008-05-23
> **Sam Lars said:**
> Have you installed
```
compiz-fusion-plugins-main
compiz-fusion-plugins-extra
```

Also, could you do a
```
compiz --replace
```
in a terminal, and see if it tells you anything about missing plugins?

When typing 
```
compiz --replace
```
It told me, that it wasn't installed. So I installed it, as it suggested, with the apt-get command, and then installed the two plugins you mentioned.
Then I opened compiz, but all the pictures are missing? They're showing up as "broken" images, like the one on the screenshot I posted in the first post...
Anyway to fix it?

Edit: Some of the functions in compiz are missing, like windows decorations(the most annoying), enabling moving windows, the svg(?) graphics thing, and so on.

---

### Post by Sam Lars on 2008-05-23
If you look in Synaptic for compiz, do you have all related packages installed?

---

### Post by muschen on 2008-05-23
As in every package with compiz-something?

---

### Post by Sam Lars on 2008-05-23
Yeah, you can always remove them if they don't work.

---

### Post by muschen on 2008-05-24
Okay, I've installed all the packages todo with compiz, except for the KDE ones, and the pictures still doesn't show up. The functions, such as window decorations, are there now, but I can't enable them.

---

### Post by Sam Lars on 2008-05-24
If you do a compiz --replace from a terminal, does it give you any errors about plugins on startup?  If you then try to enable a plugin, does it then give you any errors in the terminal?  Can you enable the effects to Normal or Extra in the Appearance preferences?

---

### Post by muschen on 2008-05-24
when typing compiz --replace it get this:
```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2592 (rev 03) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 

```

I am able to switch between none, normal and extra effects, but if it's on normal or extra, it won't let me enable the before mentioned effects. When trying to enable those, nothing shows up in the terminal...

---

### Post by lordievader on 2008-05-24
It complains for the missing Xgl, check if you have the package: xserver-xgl installed.
Else install, log out, log back in and maybe you see a change!

Edit: at my installation it needed this package to be able to run compiz.

---

### Post by pietjanjaap on 2008-05-24
If you are using 8.04 you should not install the xgl server.

Install compiz etc
then install envy, and remove and then install the video driver with envy.

---

### Post by muschen on 2008-05-24
> **pietjanjaap said:**
> If you are using 8.04 you should not install the xgl server.

Install compiz etc
then install envy, and remove and then install the video driver with envy.

could you give me the specific names of the packages, please?

---

### Post by Sam Lars on 2008-05-27
Theres envyng-core, and envyng-gtk.  You could try installing those.

---

### Post by muschen on 2008-05-29
I've tried installing envyng-core and envyng-gtk, but it doesn't seem to help? :/

---

### Post by Sam Lars on 2008-05-29
Did you run the program and remove and reinstall your drivers?

---

### Post by muschen on 2008-05-31
Yes, I did

---

### Post by Sam Lars on 2008-06-02
Have your tried reinstalling everything?  All the compiz, compiz-fusion, and compizconfig packages?

---

### Post by muschen on 2008-06-05
Yes, I have, and that didn't really help much :(

---

### Post by Sam Lars on 2008-06-05
Sorry if this has already been asked/mentioned, but what video card do you have?

---

### Post by muschen on 2008-06-08
I've got an Intel Corporation Mobile 915GM/GMS/910GML, if that's what you mean.

I've got an IBM thinkpad t43...

---

### Post by Forlong on 2008-06-08
Please post the output of [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

As well as ```
dpkg -l | grep compiz
``` and use the forum's [noparse][CODE][/noparse] tag please (# button)

---

### Post by muschen on 2008-06-09
Here we go...
compiz-check:
```
Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

```

dpkg -l | grep compiz
```
ii  compiz                                     1:0.7.4-0ubuntu6                                   OpenGL window and compositing manager
ii  compiz-bcop                                0.7.4-0ubuntu1                                     Compiz option code generator
ii  compiz-check                               0.4-1                                              Script to check if it's possible to run Comp
ii  compiz-core                                1:0.7.4-0ubuntu6                                   OpenGL window and compositing manager
ii  compiz-dev                                 1:0.7.4-0ubuntu6                                   OpenGL window and compositing manager - deve
ii  compiz-fusion-plugins-extra                0.7.4-0ubuntu1                                     Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.7.4-0ubuntu5                                     Collection of plugins from OpenCompositing f
ii  compiz-gnome                               1:0.7.4-0ubuntu6                                   OpenGL window and compositing manager - GNOM
ii  compiz-plugins                             1:0.7.4-0ubuntu6                                   OpenGL window and compositing manager - plug
ii  compizconfig-backend-gconf                 0.7.4-0ubuntu1                                     Settings library for plugins - OpenCompositi
ii  compizconfig-settings-manager              0.7.4-0ubuntu2                                     Compiz configuration settings manager
rc  emerald                                    0.7.2-0ubuntu2                                     Decorator for compiz-fusion
ii  libcompizconfig0                           0.7.4-0ubuntu1                                     Settings library for plugins - OpenCompositi
ii  libcompizconfig0-dev                       0.7.4-0ubuntu1                                     Development file for plugin settings - OpenC
ii  libemeraldengine0                          0.7.2-0ubuntu2                                     Decoration engines for compiz-fusion
ii  python-compizconfig                        0.7.4-0ubuntu1                                     Compiz configuration system bindings

```

---

### Post by Forlong on 2008-06-09
Why do you have compiz-bcop and compiz-core installed? Did you try to compile Compiz from source?

---

### Post by muschen on 2008-06-12
Uhm, I don't think so? I've not compiled anything myself. But I've tried to install the extra compiz plugins, and then removed it again.

---

### Post by Forlong on 2008-06-12
> **muschen said:**
> But I've tried to install the extra compiz plugins, and then removed it again.
How did you do that?

---

### Post by muschen on 2008-06-14
I tried uninstalling it by using a command from the thread about it. 

```
sudo compiz-git --uninstall
sudo apt-get remove compiz-git

```

---

### Post by Forlong on 2008-06-14
So you did compile Compiz from source after all.

Please do not use some random script you found on the internet if don't know exactly what you are doing!

I'm afraid you have to take the whole problem to the guy who wrote that script, because I can't know what it did to your system.

---

### Post by muschen on 2008-06-14
Then I'll do that. Thanks for your help and time.

---

### Post by boneywasawarrior on 2008-06-14
Try this

SKIP_CHECK=yes compiz --replace ccp &

---

### Post by muschen on 2008-06-16
Still doesn't work =/

---

