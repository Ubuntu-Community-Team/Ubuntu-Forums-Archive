---
title: "STILL no title bars..."
date: 2008-05-02
forum: General Help
---

### Post by hatman on 2008-05-02
Done everything I can think of... Emerald is installed and set as the default window decorator, Window Decoration is enabled in CCSM and still I cant get the title bars back (except by opening a terminal and typing metacity --replace - which disables the compiz effects)...Typing emerald --replace in a terminal results in nothing happening...

---

### Post by Zorael on 2008-05-02
What videocard do you use?

What is the terminal output of the following?
```
$ compiz --replace &
$ emerald --replace &
```

---

### Post by hatman on 2008-05-02
I'm using a nVidia Geforce 5000 

From the emerald command I get 
> [1] 6127


from the compiz command I get 
> Checking for Xgl: [2] 6128
andy@downstairs:~$ not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0185 (rev c1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (resizeinfo) - Warn: Bind Pixmap to Texture failure
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (resizeinfo) - Warn: Bind Pixmap to Texture failure
and then the terminal just sites there waiting for something or other...

---

### Post by njparton on 2008-05-02
Try
 
```
metacity --replace
```
 
If that works then you could revert to using metacity as your default desktop manager but you'd lose the effects (which I consider to be a gimmick anyway).

---

### Post by Zorael on 2008-05-02
The terminal output from Emerald looks about right. The compiz output looks more alarming though.

[list][*]The terminal just sitting there means you didn't postpend the ampersand (&) to make it a child process of the terminal app. If you exit it by clicking the X it'll close compiz, but if you enter **exit** instead it'll keep going in the background.


[*]Is this in Hardy? A clean install or an upgrade?

If upgrade, you may have some Compiz remnants in the system from your earlier distro version. Pop up Synaptic, File -> Repostiories, make sure you don't have any third-party repositories enabled. Search for "compiz" and tag all relevant installed packages for **complete removal**. Then reinstall them.

Terminal way (assumes repositories disabled).
```
$ sudo aptitude purge ~ncompiz ~nberyl ~nemerald ~nlibdeco
$ sudo aptitude
$ sudo aptitude clean
$ sudo aptitude install compiz compizconfig-settings-manager emerald
```


[*]Your xorg.conf may lack necessary Nvidia options. Try entering these commands.
```
$ sudo cp /etc/X11/xorg.conf /etc/X11.xorg.backup0805
$ sudo nvidia-xconfig -d 24 --allow-glx-with-composite --add-argb-glx-visuals --randr-rotation
```
Save your work, restart X with Ctrl+Alt+Backspace


[*]As for compiz being a gimmick, that's a matter of preference and opinion. :>

I'm not sure I could stand not having the Expo plugin anymore. I'm hooked. And I just love the wobbling windows, though the cube has lost its novelty now after a year.[/list]

---

### Post by hatman on 2008-05-02
I'll try that when I get home... most annoying thing is that everything is running great on my work PC... compiz, the effects, the lot... although tbh, the PC at work is an upgrade while te one at home is a clean install....

And I agree about the gimmick, it iIS a gimmick, but call me shallow, I love it!!!!  And it keeps the Windows users in the office on their toes as they look at the effects and go wow!!!... lol

---

### Post by Zorael on 2008-05-02
One must remember that while some plugins can be considered gimmicks, fluffing up already existing features (extra desktops/viewports), some introduce new stuff, while further others add accessibility features for those seeing-impaired. :>

And I can't stress how lovely Expo is, beats every panel applet - and beautiful, to boot.

---

### Post by hatman on 2008-05-02
woohoo!!! that worked a treat... Thanks ever so much...

---

