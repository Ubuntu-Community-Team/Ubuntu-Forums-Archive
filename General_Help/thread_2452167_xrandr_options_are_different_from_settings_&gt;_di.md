---
title: "xrandr options are different from settings &gt; displays on gnome / ubuntu 20.04"
date: 2020-10-17
forum: General Help
---

### Post by lucasgvarela on 2020-10-17
```
$ xrandr
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 32767 x 32767
HDMI-0 disconnected (normal left inverted right x axis y axis)
eDP-1-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1920x1080     60.05 +  60.01*   59.97    59.96    59.93  
   1680x1050     59.95    59.88  
   1600x1024     60.17  
   1400x1050     59.98  
   1600x900      59.99    59.94    59.95    59.82  
   1280x1024     60.02  
... others options

```

xrandr man page says: if invoked without any option, it will dump the state of the outputs, showing the existing modes for each of them, with a '+' after the preferred modes and a '*' after the current mode.
Based on that xrandr output I'm assuming my monitor is using 60Hz, but my gnome settings > displays is showing me I'm using 120Hz.


[https://ibb.co/qxcjP66](https://ibb.co/qxcjP66)  - Image of gnome settings > displays > refresh rate

[IMG]https://ibb.co/qxcjP66[/IMG]

```
$ cat ~/.config/monitors.xml
<monitors version="2">
  <configuration>
    <logicalmonitor>
      <x>0</x>
      <y>0</y>
      <scale>1</scale>
      <primary>yes</primary>
      <monitor>
        <monitorspec>
          <connector>eDP-1-1</connector>
          <vendor>AUO</vendor>
          <product>0x61ed</product>
          <serial>0x00000000</serial>
        </monitorspec>
        <mode>
          <width>1920</width>
          <height>1080</height>
          <rate>120.01551055908203</rate>
        </mode>
      </monitor>
    </logicalmonitor>
  </configuration>
</monitors>

```

My question is: Which is right? My monitor doesn't support 120Hz and is using 60Hz based on xrandr or it's really using 120Hz based on gnome settings and ~/.config/monitors.xml ?

---

