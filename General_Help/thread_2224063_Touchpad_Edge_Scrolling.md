---
title: "Touchpad Edge Scrolling"
date: 2014-05-14
forum: General Help
---

### Post by cessanfrancisco on 2014-05-14
Hi,

I am using Ubuntu 14.04 and, as always, no matter what version I use, and no matter which computer I use it on (I have a variety of them), the "Mouse & Touchpad" settings do absolutely nothing.  Having said that, at the moment I am using a Lenovo Z580 and by default edge scrolling is enabled, on the touchpad.  Does anyone know how to disable edge scrolling?  I have tried using dconf editor and the built in "Mouse & Touchpad" settings, all to no avail.  Everything else, "disable touchpad while typing," "touchpad sensitivity," etc, I have been able to write a start-up script, but cannot figure out one for edge scrolling.

Thanks in advance.

---

### Post by mikewhatever on 2014-05-14
You could try the following in a terminal window:
> synclient VertEdgeScroll=0

Also, it's useful to know how the touchpad is recognised (if at all), so you should add the output of **xinput list** to the OP.

---

### Post by cessanfrancisco on 2014-05-15
Thanks.  Here is the result of "xinput list":  

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; Lenovo EasyCamera                           id=10    [slave  keyboard (3)]
    &#8627; Ideapad extra buttons                       id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]


Let me know if that tells you anything important.

Thanks.

---

### Post by cessanfrancisco on 2014-05-15
Sorry.  That might have been hard to read.  Here it is again.

```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; Lenovo EasyCamera                           id=10    [slave  keyboard (3)]
    &#8627; Ideapad extra buttons                       id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]


```

---

### Post by cessanfrancisco on 2014-05-15
Thank you.

Yes, ```
synclient VertEdgeScroll=0
``` works great.

---

### Post by monkeybrain20122 on 2014-05-15
If you enable two finger scrolling in Mouse and Touchpad, edge scrolling will be disabled. I don't know why you want to disable something so useful. I like to use both and my touchpad supports both but somehow stupid gnome settings only allow one and I have to use a stratup script to enable both. :)

---

### Post by cessanfrancisco on 2014-05-15
I like the two-finger scrolling but find the edge scrolling just gets in the way.  Oddly, I have the opposite issue in that no matter what I enable/disable in "Mouse & Touchpad" settings both two-finger and edge scrolling are enable by default, and I cannot disable them.  Therefore I have to write a start-up script.  As a matter of fact, nothing under "Mouse & Touchpad" setting works.  Everything is enabled and to disable or adjust these settings I have to write scripts.  This is how it's been for me with the last three or so releases, on three different computers.

---

