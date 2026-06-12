---
title: "Touchpad stops working (tap and scroll) after some minutes"
date: 2017-02-15
forum: General Help
---

### Post by matrooswolf on 2017-02-15
Hi everybody,

Yesterday I upgraded from 14.04 to 16.04 LTS. Everything went smooth, except for one problem.

My touchpad (on a HP Probook 6570b) works fine when I log in. But after some minutes, click on tap and scrolling stops working. I can still move the mouse around with the touchpad. So it is detected as a device, it is only the tap on click and scrolling (on the edge) that stops working...

Any ideas on how to debug and fix this? I am used to tapping and scrolling with the touchpad and now feel handicapped...

---

### Post by matrooswolf on 2017-02-16
It still happens and I have no idea why. Takes about a minute and scrolling and tapping stops functioning.

This however works:
```
sudo  modprobe -r psmouse && sudo modprobe psmouse
```

Does anybody know how I could assign this command to a hotkey?

---

### Post by matrooswolf on 2017-03-02
Well, this is a persistent problem.

Nobody else who has this? Or who know a more permanent solution?

Each time I start up the driver fails after one or two minutes. Restarting the driver fixes it, but why?

---

### Post by knerlington on 2017-08-04
Using an XPS 9550 and Ubuntu 17.04. Just made a thread about it. Have the same issue, but for me restarting the psmouse module does nothing. 
If you run "xinput list" as a command in a terminal how many touchpads do you have listed?

---

### Post by matrooswolf on 2017-12-22
Hi knerlington,

Sorry for the late response.

Problem is still the same.

This is what I get when running ```
xinput list
``````
Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                      	id=11	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; HP HD Webcam [Fixed]                    	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]
    &#8627; HP Wireless hotkeys                     	id=13	[slave  keyboard (3)]
    &#8627; HP WMI hotkeys                          	id=14	[slave  keyboard (3)]
```

---

