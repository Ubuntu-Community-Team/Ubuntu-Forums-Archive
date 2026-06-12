---
title: "Reactivate Touchpad On/Off Key"
date: 2016-06-03
forum: General Help
---

### Post by hailholyghost on 2016-06-03
Hello,

I want a keyboard solution to activate and deactivate the touchpad in Xfce in Ubuntu, I've seen some solutions here [http://askubuntu.com/questions/537002/how-to-quickly-enable-disable-touchpad-in-xubuntu-14-04-without-installing-other](http://askubuntu.com/questions/537002/how-to-quickly-enable-disable-touchpad-in-xubuntu-14-04-without-installing-other) but they still rely on the ability to use the cursor (and I can't get them to work anyway)

Why is my function key to turn the touchpad off/on disabled?  How can I get this key working again?
:confused::confused:

---

### Post by QDR06VV9 on 2016-06-03
Well lets take a peek at what is shown in "xinput list"
```
xinput list
```
Paste back what is shown.

---

### Post by hailholyghost on 2016-06-03
> **runrickus said:**
> Well lets take a peek at what is shown in "xinput list"
```
xinput list
```
Paste back what is shown.

```
con@Inspiron-3521:~$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)    id=9    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_HD                 id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=13    [slave  keyboard (3)]
```

thank you runrickus

---

### Post by QDR06VV9 on 2016-06-03
can you use these two commands?:

Disable:
```
xinput set-prop 12 "Device Enabled" 0

```

Enable:
```
xinput set-prop 12 "Device Enabled" 1

```

---

### Post by hailholyghost on 2016-06-03
Hi,

thanks, that works!

on this link [http://askubuntu.com/questions/65951/how-to-disable-the-touchpad#67724](http://askubuntu.com/questions/65951/how-to-disable-the-touchpad#67724)

I see how someone did "The commands can be added into Xfce launchers."

and then had nice images of diable/enable touchpad icons, how can I do that?

---

### Post by QDR06VV9 on 2016-06-03
Sure we just had to find the code before we did that...Now right click on your panel and choose add new items..then select launchers and add and name them as I showed the code to enable and disable.
Screenshot to help.

---

### Post by QDR06VV9 on 2016-06-03
Just in case I assumed too much....Right click on the top panel and select Panel>Add New items> Then Select Launcher> Click that and Add.
Now A new launcher is created..again right click on the newly created launcher and select properties> Now you will see a "**+"** on the the right Click that...Now you will have some choices to choose from scroll down to mouse and touchpad and click that and Add to panel... Now you can follow the instructions from the link you show in your earlier post Askubuntu.
If you still need help just post back.

---

### Post by hailholyghost on 2016-06-04
I should rephrase the question, is there a way I can turn the touchpad off via a hardware switch, instead of manually deactivating it every time I log in? I have been doing this in GNOME for years, I am not sure why this doesn't work in Xfce.

---

