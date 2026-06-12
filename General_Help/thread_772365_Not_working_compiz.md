---
title: "Not working compiz"
date: 2008-04-28
forum: General Help
---

### Post by jzibrat on 2008-04-28
Hy,

I tried the code: compiz --replace

but i get this message:

my@my-laptop:~$ compiz --replace
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

Does any one know what i must do?

Thank you for your answer

Best regards.

---

### Post by Zorael on 2008-04-28
Is your videocard supported? See the sticky for some more information on blacklisted drivers.
[http://ubuntuforums.org/showthread.php?t=765875](http://ubuntuforums.org/showthread.php?t=765875)

---

### Post by vkennedy85 on 2008-04-28
My video card (intel default video card) doesn't seem to be black listed but I'm having similar issues.  My window snapping options seems to work.  My other options seem to work, but I can't use the cube, nor can I even switch desktops with ctrl+alt+right/left arrows or by clicking on any of the 4 (yes there are 4) desktop icons on the bottom right part of the screen.

Ideas?

---

### Post by Ponomous on 2008-04-28
What version of ubuntu are you running?  I had this problem after messing around with my gcard drivers on 7.10 and couldnt find a good fix, I unfortunately had to do a clean install...

---

### Post by vkennedy85 on 2008-04-28
I'm running 8.04, it was a fresh install last night.  Then I used the package manager to download the compiz-settings-manager to install the package.  I've got the options editor like I did in 7.10 when it worked, and now it doesn't.

---

### Post by alsamman on 2008-04-28
Is your graphics card enabled under System>Admin>Hardware Drivers?

---

### Post by vkennedy85 on 2008-04-29
It appears that would be the problem, how do I go about fixing it?

---

### Post by cmendoza on 2008-04-30
I have the same problem as vkennedy85, i just installed compiz-fusion and everything works but the cube and the switch desktop thing, the 4 desktops say Desktop 1, when i executed compiz --replace i got this output:


```

Checking for Xgl: not present.
Detected PCI ID for VGA: 01:00.0 0300: 10de:01d8 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present.
Checking for FBConfig: present.
Checking for Xgl: not present.
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12  image format

```

As it says, I'm using a nvidia card and just upgraded to Hoary, I'm using Kubuntu

Any help will be appreciated, thanks in advance

---

### Post by cmendoza on 2008-04-30
Well, I got some help from here [http://ubuntuforums.org/showthread.php?t=509775]("http://ubuntuforums.org/showthread.php?t=509775")
but I still would like to know how to make the desktops independent, because if I change the wallpaper from one desktop, it happens the same with all the other desktops, same with the apps open in one desktop appear in all, it's more like a copy of the same Desktop 1, how can i make desktops independent with compiz?

---

### Post by Zorael on 2008-05-01
> **cmendoza said:**
> I have the same problem as vkennedy85, i just installed compiz-fusion and everything works but the cube and the switch desktop thing, the 4 desktops say Desktop 1, when i executed compiz --replace i got this output:


```

Checking for Xgl: not present.
Detected PCI ID for VGA: 01:00.0 0300: 10de:01d8 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present.
Checking for FBConfig: present.
Checking for Xgl: not present.
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12  image format
```

As it says, I'm using a nvidia card and just upgraded to Hoary, I'm using Kubuntu

Any help will be appreciated, thanks in advance
Well, um, that seems to be working? :>

Don't mind the error message.

---

### Post by tripple_face on 2008-05-01
mine too..
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4c66 (rev 01) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (1024): Failed.
aborting and using fallback: /usr/bin/metacity 

when i go to System->Preference->Appearance,i click extra visual effects. A window pop-up saying Desktop Effects cannot be enabled..

need help here :(

---

### Post by redbob on 2008-05-01
Maybe you will need to edit your xorg.conf manually, like I've got to do for my video rotate screen. Type this command> sudo /etc/X11/xorg.confso type this line> Section "Module"
        Load            "glx"
EndSection


---

### Post by tripple_face on 2008-05-01
i tried it.. but its still 
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4c66 (rev 01) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (1024): Failed.
aborting and using fallback: /usr/bin/metacity 

and desktop effects could not be enabled..
:(
i am on ATI Radeon Mobility 9200,Ubuntu Gutsy gibbon

---

### Post by tripple_face on 2008-05-01
thanks for you reply btw, redbob..

appreciate it :)

---

### Post by toobitz on 2008-05-02
> **tripple_face said:**
> 
```

[...]
Comparing resolution (1280x800) to maximum 3D texture size (1024): Failed.
[...]

```


Don't know if it works, but you may want to try to add the following to the "Screen" section in your /etc/X11/xorg.conf:
```
DefaultDepth 24
 SubSection "Display"
    Depth 24
    Virtual 1280 800
    Modes "1024x800"
  EndSubSection

```

If you're unsure about this, please post your xorg.conf here.

---

### Post by Saint Angeles on 2008-05-02
having ati problems? no direct rendering? try this:

[http://ubuntuforums.org/showpost.php?p=4749740&postcount=12](http://ubuntuforums.org/showpost.php?p=4749740&postcount=12)

---

### Post by Zorael on 2008-05-02
To get relevant Nvidia option tweaks in your /etc/X11/xorg.conf, do this.
```
$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.backup0805
$ sudo nvidia-xconfig -d 24 --allow-glx-with-composite --add-argb-glx-visuals --randr-rotation
```

---

### Post by tripple_face on 2008-05-02
i tried your way angel.. however,
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4c66 (rev 01) (prog-if 00 [VGA])
Checking for texture_from_pixmap: Segmentation fault (core dumped)
present. 
Checking for non power of two support: Segmentation fault (core dumped)
present. 
Checking for Composite extension: present. 
Segmentation fault (core dumped)
Comparing resolution (1280x800) to maximum 3D texture size (1024): Failed.
aborting and using fallback: /usr/bin/metacity

---

### Post by toobitz on 2008-05-02
OK, as stated, I don't know whether this works, but you could try the following: open your xorg.conf, go to line 97 and change the following section...
```

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x800"
	EndSubSection
EndSection

```
... so that it reads as follows:

```

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
[COLOR="Red"]                Depth 24
                Virtual 1280 800
                Modes "1024x800"[/COLOR]
	EndSubSection
EndSection

```

---

### Post by tripple_face on 2008-05-02
i tried that and it doesnt work as well..

i attached my original xorg conf

---

