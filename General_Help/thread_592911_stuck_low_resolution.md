---
title: "stuck low resolution"
date: 2007-10-26
forum: General Help
---

### Post by spexc31 on 2007-10-26
i just installed the new ubuntu 7.10.
i installed my display drivers i believe when i enabled the visual effects.
(my gpu is nvidia geforce4 mx)
i can't seem to change my resolution from 640x480. its the highest resolution selectable in the change screen resolution screen. i know my moniter is capable of showing higher resolution with xp.

this is my 1st ubuntu experience and with my resolution so small, everything is very very big and give me a headache just using it now. i would keep on trying to find answers mysef but my display is making me feel sick. =(
and when i tried looking up answers myself, but just got confused with all these xconfig terminal directions.

can someone walk me through how i can set my display to a higher resolution? any help would be greaty appreciatedd =)

---

### Post by kelbizzle on 2007-10-26
Here ya go...

First you must back up your xorg.conf file. It's good practice. Trust me it's helped me alot. Type these commands into terminal. or paste :-p
```
sudo cp /etc/X11/xorg.conf xorg.con.bak
```

Then you must open your xorg.conf file. 
```
gksudo gedit /etc/X11/xorg.conf
```

Find this section. It may look similar to yours with 640x480 resolution only
```
Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV25 [GeForce4 Ti 4200]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "640x480"
    EndSubSection
EndSection
```

Modify the Subsections "Display" to look like this

```
Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV25 [GeForce4 Ti 4200]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
``` 

Save the file... Just remember before you restart your computer that if this doesn't work
Type this command to restore the file we made changes to with the backed up copy.
```
sudo cp /etc/X11/xorg.conf.bak xorg.conf
```

---

