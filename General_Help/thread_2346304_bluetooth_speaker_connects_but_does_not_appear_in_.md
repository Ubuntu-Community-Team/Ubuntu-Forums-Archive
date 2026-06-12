---
title: "bluetooth speaker connects but does not appear in sound settings"
date: 2016-12-13
forum: General Help
---

### Post by boatcat on 2016-12-13
I am able to connect my bluetooth speaker to my laptop but it does not show up as an output option in sound settings. It used to work just fine but stopped after a software upgrade. 

Not sure what other info (if any) you might need. 

Thanks for any help!

---

### Post by jeremy31 on 2016-12-13
Post results for ```
pactl list short | grep blue
```

---

### Post by boatcat on 2016-12-13
Hi, 

that gives me 

> ~$ pactl list short | grep blue
8    module-bluetooth-policy        
9    module-bluetooth-discover        
10    module-bluez5-discover    

---

### Post by jeremy31 on 2016-12-14
Have you attempted to delete the pairing and then pair again as I am sure there was a recent change to pulseaudio

---

### Post by boatcat on 2016-12-14
I tried that a couple of times a few days ago and it didn't do anything. I've just tried it now and it worked.....:oops:

---

### Post by jeremy31 on 2016-12-14
You may still have some issues reconnecting the headphones and trying to use A2DP audio and sometimes it may just be quicker to delete and redo the pairing

But you could look through the [bug report](https://bugs.launchpad.net/ubuntu/+source/indicator-sound/+bug/1577197) as somebody made a python script that does work for me after I connect to my headset, the script needs to be run manually as it does require some user input

---

