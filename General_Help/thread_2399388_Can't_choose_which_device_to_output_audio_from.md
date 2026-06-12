---
title: "Can't choose which device to output audio from"
date: 2018-08-24
forum: General Help
---

### Post by devilkhaled on 2018-08-24
Hello guys so i just installed Ubuntu 18.04 everything works fine except this so i have both the speakers and headphones plugged in to my computer but there is no option to choose which device to output audio from in the settings if both are connected i only get audio through the headphone i need to unplug the headphones in order to get audio from the speakers how to fix it ?

---

### Post by tea for one on 2018-08-24
Sound output varies depending on your hardware. I.e. internal or external speakers, PC or Laptop, HDMI or Displayport etc. 

Nevertheless, I would advise that you install a little sound utility with a GUI

```
sudo apt install pavucontrol
```

This should give you more control over and above the basic sound settings.

---

### Post by Yellow Pasque on 2018-08-25
> if both are connected i only get audio through the headphone

This is called "Auto-Mute" and it is the intended behavior. Most people want the speaker to mute when they plug in headphones. Look in alsamixer to see if there is a setting to disable it:
```
alsamixer
```

---

### Post by him610 on 2018-08-28
If your speaker and headphones both have 3.5 mm connectors, get yourself one of those 3.5 mm Y-splitters where both your headphones and speaker can connect to. Sound will emanate from both until you turn your speaker off. It does have an On/Off switch, right?

---

