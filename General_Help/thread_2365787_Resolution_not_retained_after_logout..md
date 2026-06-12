---
title: "Resolution not retained after logout."
date: 2017-07-10
forum: General Help
---

### Post by again? on 2017-07-10
I was playing around with nvidia-settings and xrandr to test different resolutions for a game.
My default monitor resolution is 1680x1050.

I switched between this res and 1024x768 using the nvidia-settings GUI and also with xrandr with the following commands.
```
xrandr --output DVI-I-2 --mode 1024x768
xrandr --output DVI-I-2 --mode 1680x1050
```

If I set it to 1680x1050 it keeps reverting back to 1024x768 when I log out and back in.
Same with a restart or reloading gnome-shell.
```
glen@GU17:~$ **xrandr -q**
Screen 0: minimum 8 x 8, current 1680 x 1050, maximum 16384 x 16384
DVI-I-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 disconnected (normal left inverted right x axis y axis)
DVI-I-2 connected primary 1680x1050+0+0 (normal left inverted right x axis y axis) 474mm x 296mm
   1680x1050     59.88*+  59.95  
   1280x1024     75.02    60.02  
   1280x960      60.00  
   1152x864      75.00  
   1024x768      75.03    70.07    60.00  
   800x600       75.00    72.19    60.32    56.25  
   640x480       75.00    72.81    59.94  
HDMI-0 disconnected (normal left inverted right x axis y axis)
DVI-I-3 disconnected (normal left inverted right x axis y axis)
```
I created a new user account to test and it loads ok to the default 1680x1050 res.
I didn't run anything with sudo and I can't find a config file in my home directory.

Any ideas????? :confused:

---

### Post by again? on 2017-07-11
Appears some where along the line with my fiddling, nvidia-settings had created the file **~/.config/monitors.xml**
```
<monitors version="1">
  <configuration>
    <clone>no</clone>
    <output name="DVI-I-2">
      <vendor>SAM</vendor>
      <product>SyncMaster</product>
      <serial>HMAQ200176</serial>
      [B]<width>1024</width>
      <height>768</height>[/B]
      <rate>75.028579711914062</rate>
      <x>0</x>
      <y>0</y>
      <rotation>normal</rotation>
      <reflect_x>no</reflect_x>
      <reflect_y>no</reflect_y>
      <primary>yes</primary>
      <presentation>no</presentation>
      <underscanning>no</underscanning>
    </output>
  </configuration>
</monitors>
```
Deleting the file solved it.

---

