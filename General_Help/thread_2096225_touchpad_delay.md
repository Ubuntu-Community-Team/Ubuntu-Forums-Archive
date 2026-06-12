---
title: "touchpad delay"
date: 2012-12-19
forum: General Help
---

### Post by zizzdude on 2012-12-19
My touchpad was working fine. There was no touchpad lag/delay before I upgraded packages with the xorg-edgers ppa to make steam games work for linux beta. 

I have this in my xorg.conf (before having the ppa):

```

Section "Device"
        Identifier      "Default Device"
        Option  "NoLogo"        "True"
EndSection

Section "InputClass"
        Identifier "touchpad catchall" 
        Driver "synaptics" 
        MatchIsTouchpad "on"
        Option "FastTaps" "1"
EndSection


```

It seems that it doesn't seem to work anymore. Is there any way to fix this?

---

### Post by Pjotr123 on 2012-12-19
You mean something like this?
[https://sites.google.com/site/easylinuxtipsproject/tips#TOC-Disable-the-touchpad-while-typing-and-adapt-the-delay](https://sites.google.com/site/easylinuxtipsproject/tips#TOC-Disable-the-touchpad-while-typing-and-adapt-the-delay)
(item 12, right column)

If so, you can adapt the delay in the example to (for instance) 0.1 or 0.5.

---

### Post by zizzdude on 2012-12-19
> **Pjotr123 said:**
> You mean something like this?
[https://sites.google.com/site/easylinuxtipsproject/tips#TOC-Disable-the-touchpad-while-typing-and-adapt-the-delay](https://sites.google.com/site/easylinuxtipsproject/tips#TOC-Disable-the-touchpad-while-typing-and-adapt-the-delay)
(item 12, right column)

If so, you can adapt the delay in the example to (for instance) 0.1 or 0.5.

It seems this solution deals with delay between keystroke and touchpad, which isn't what I'm looking for unfortunately. :( 

I'm talking about how long it takes for the computer to recognize a "tap" on the touchpad. Before the update, it reacts immediately with FastTaps set to 1, but afterwards, it reverts back to its delayed reaction. When I tried to reset FastTaps via synclient, it gives me a strange error:
```
Property for 'FastTaps' not available. Skipping.

```

Any ideas?

---

