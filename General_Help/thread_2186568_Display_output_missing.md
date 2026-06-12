---
title: "Display output missing"
date: 2013-11-08
forum: General Help
---

### Post by Alan.Brown on 2013-11-08
I am using Xubuntu 13.10 on an Acer Aspire laptop.   I connected the laptop to a TV using a VGA cable and was able to watch on the TV a movie stored on the laptop.   Just what I wanted.
When I disconnected the VGA and rebooted the laptop all I get is a blank screen.   I can get in to the system if I use **"Recovery Mode"** then everything is normal.   I have checked the settings in **Settings Manager > Display** - OK - and in **Settings Editor** I unchecked **"xfce4-desktop > monitor1 > image-show"** (**monitor0** settings are OK).   I also saved the session settings.
After rebooting I still got the blank screen so I have destroyed some other settings elsewhere.  I can still get in through** "Recovery Mode"**
Any suggestions?

TIA

Alan

---

### Post by Toz on 2013-11-08
When you boot the computer, do you at least see the boot up splash screen, login screen (or anything) on the laptop screen? It sounds like its defaulting to the TV display, but any Xfce setting wouldn't take effect until you actually launch Xfce (after successful login). 

Do you have a** ~/.config/xfce4/xfconf/xfce-perchannel-xml/displays.xml** file or a **display** channel in "Settings Editor"? If so, can you post back the contents of the file?

---

### Post by Alan.Brown on 2013-11-08
**~/.config/xfce4/xfconf/xfce-perchannel-xml/displays.xml**  is -

<?xml version="1.0" encoding="UTF-8"?>

<channel name="displays" version="1.0">
  <property name="Default" type="empty">
    <property name="VGA1" type="string" value="___ 72&quot;">
      <property name="Active" type="bool" value="true"/>
      <property name="Resolution" type="string" value="1920x1080"/>
      <property name="RefreshRate" type="double" value="60.000000"/>
      <property name="Rotation" type="int" value="0"/>
      <property name="Reflection" type="string" value="0"/>
      <property name="Primary" type="bool" value="false"/>
      <property name="Position" type="empty">
        <property name="X" type="int" value="0"/>
        <property name="Y" type="int" value="0"/>
      </property>
    </property>
  </property>
</channel>
This looks wrong - VGA should not be there!  The details refer to the TV I was using.
I removed this file and it now boots up correctly!!

Thanks for your help

Alan

---

