---
title: "Synaptics Touchpad left/middle button bug"
date: 2017-03-19
forum: General Help
---

### Post by olegst90 on 2017-03-19
I run Ubuntu 16.04 on ThinkPad t520. A few days ago a strange thing happened.

The left button of the touchpad started to randomly act as a middle one. That is, now it delivers left click event, now middle one and the system reacts accordingly: from time to time instead of, say, ignoring left click in the command line it inserts clipboard content and so on.

What should I start from?

PS It started after I plugged an USB network adapter.

---

### Post by Keith_Helms on 2017-03-19
The synaptics driver has all kinds of multi-touch features and you may be running into some combo option where your palm touching part of the pad at the same time you're clicking a button does something extra.  I suspect a USB network adapter was just a coincidence.  

Open a terminal window and type 
```
synclient -l
```
to see what options are enabled for the touchpad.

---

