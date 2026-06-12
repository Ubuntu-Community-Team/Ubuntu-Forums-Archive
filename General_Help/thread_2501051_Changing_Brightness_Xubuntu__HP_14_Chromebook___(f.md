---
title: "Changing Brightness Xubuntu  HP 14 Chromebook   (falco)"
date: 2024-09-20
forum: General Help
---

### Post by 90ninety2 on 2024-09-20
So I have a chromebook with the Mrchromebox BIOS , allowing to install Linux .. I previously used Galium OS , which worked fine but is discontinued .. 

So I tried the next easiest thing , XUBUNTU 24.04.1

I am having difficulty getting the brightness keys working .. All other shortcut keys work 

I used the xkb-data_2.12-1ubuntu1-galliumos8_all.deb   here [http://apt.galliumos.org/pool/main/x/xkeyboard-config/](http://apt.galliumos.org/pool/main/x/xkeyboard-config/) , to get the 'Chromebook' keyboard option 

The brightness keys are recognized when pressing in the 'Application Shortcuts' when adding a new shortcut  .. Though I dont know what to type in the command part 

On another note , im interested if anyone recommends another Debian flavour OS .. I couldn't get the keyboard shortcuts working in Mint either

---

### Post by him610 on 2024-09-21
This works for me on a stubbornly bright monitor...
```
 xrandr --output HDMI-1 --brightness 0.8
```
You may have to experiment with the values to brighten/dim display
*xrandr* alone will indicate the display you are using

---

