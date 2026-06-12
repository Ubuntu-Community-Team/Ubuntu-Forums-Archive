---
title: "How to add a new display resolution."
date: 2014-02-26
forum: General Help
---

### Post by blazzer12 on 2014-02-26
I run the Xubuntu 13.10.

I have to display that I plug to VGA port (one at a time, I have only one VGA port)

1. **Samsung Monitor**

It works like a charm. It automatically goes to 1360x768 resolution. Even if it doesn't go to optimal resolution (unplug Toshiba TV and plug this), I can to go Display and select  "1360x768".

2. **Toshiba TV (Regza AV32)**

This is the problem one. When I start Xubuntu, the desktop resolution is set to 1024x768. TV can display up to 1920x1080 (checked in ubuntu, kubuntu), although I prefer 1280x768.

**Usually in Ubuntu or Kubuntu I would** :

a)  connect Toshiba TV 

b) run this script

```
#! /bin/bash


xrandr --newmode "1280x768_60.00"   79.50  1280 1344 1472 1664  768 771 781 798 -hsync +vsync
xrandr --addmode VGA1 "1280x768_60.00"

```

c) Go to display settings and choose "1280x768"


But this doesn't work in Xubuntu. After I select the resolution "1280x768" it ask if it shuold keep the resolution. When I select nothing happens. It only stay the same resolution (not 1280x768).


**Backstory...**

I created scripts to delete the following file during startup and shutdown :

```
~/.config/xfce4/xfconf/xfce-perchannel-xml/displays.xml
```

This is because when I connect Toshiba TV, the resolution is set to Samsung Monitor resolution (1360x768), thus giving a blank screen. I searched the forms and learned that deleting "displays.xml" does the trick.


On second thought I wanted to keep the displays.xml file and modify it accordingly.

displays.xml




```
<?xml version="1.0" encoding="UTF-8"?>
<channel name="displays" version="1.0">
  <property name="Default" type="empty">
    <property name="VGA1" type="string" value="Samsung Electric Company 19&quot;">
      <property name="Active" type="bool" value="true"/>
   

   <property name="Resolution" type="string" value="1360x768"/>
      <property name="RefreshRate" type="double" value="60.015162"/>
      <property name="Rotation" type="int" value="0"/>
      <property name="Reflection" type="string" value="0"/>
      <property name="Primary" type="bool" value="false"/>
      <property name="Position" type="empty">
        <property name="X" type="int" value="0"/>
        <property name="Y" type="int" value="0"/>
      </property>
    </property>
</channel>

```

As you can see on the line 6, the display connected is identifed (<property name="VGA1" type="string" value="Samsung Electric Company 19">). So I thought I could create another entry identifying my "Toshiba TV". So I ran **xrandr**.

```
toshiba tv


Screen 0: minimum 320 x 200, current 1024 x 768, maximum 32767 x 32767
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

---------------------------------------------------------------------------------------------------------

samsung monitor


Screen 0: minimum 320 x 200, current 1360 x 768, maximum 32767 x 32767
VGA1 connected 1360x768+0+0 (normal left inverted right x axis y axis) 410mm x 230mm
   1360x768       60.0*+
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     60.0  
   720x400        70.1  
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

```

I wasn't sure how to do that. They both looked the same.


[B]Requirement
[/B]
I cannot run a script to set lutionreso to 1280x768 because when I connect the Samsung monitor it doesn't support that resolution and I will end up with blank screen!

[B]So how do I add an entry (1280x768) in the resolution list of "Display Settings" so I can select that when I connect up Toshiba TV ? This is because xubuntu sets resolution to 1024x768 on startup. If the resolution is automatically set to 1280x768 that would be awesome!
[/B]
Please suggest a solution! :)

note :  I do not have a /etc/x11/xorg.config file.

---

### Post by ajgreeny on 2014-02-26
It may be worth writing your own xorg.conf file, adding your wanted resolutions, as shown in the basic version here, (which I had to use for my virtual machine of Trusty 14.04 to get the correct resolution), and putting it in /etc/X11 where it used to be required.  You will need to restart X by logging out and in again.

Good luck; I hope this works for you.
```
Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    SubSection "Display"
        Modes        "1360x768" "1280x768" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection
```

---

### Post by blazzer12 on 2014-03-02
It didn't seem to work. 

Should I do something to force xubuntu to use the xorg.conf file I created?

---

### Post by jp734 on 2014-03-02
you might want to try adding the [COLOR="#0000CD"]horizsync[/COLOR] and [COLOR="#0000CD"]vertrefresh[/COLOR] rates on your xorg.conf file under [COLOR="#0000CD"]Section "Monitor"[/COLOR].

---

