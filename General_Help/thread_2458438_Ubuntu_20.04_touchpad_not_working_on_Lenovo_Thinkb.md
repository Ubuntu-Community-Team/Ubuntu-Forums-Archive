---
title: "Ubuntu 20.04 touchpad not working on Lenovo Thinkbook?"
date: 2021-02-24
forum: General Help
---

### Post by michlestarc61 on 2021-02-24
[COLOR=#1A1A1B][FONT=&amp]Ubuntu 20.04 touchpad not working on Lenovo Thinkbook.[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]I tried all the solutions on Ubuntu on [askubuntu.com]("https://askubuntu.com/") and everywhere still not working.[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]cat /proc/bus/input/devices[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]I tried [listing]("https://www.bestbuyninja.com/best-gaming-laptops-under-2000/") devices but its not showing input device like thinkpad.[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]Is that it has been 10 months since ubuntu 20.04 and bug is not fixed?[/FONT][/COLOR]

---

### Post by #&amp;thj^% on 2021-02-24
If you would also include this:
```
apt policy xserver-xorg-input-synaptics
```
I run about 5 different Lenovo products all work nicely.

```
xinput
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech M510                           	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Logitech K400                           	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Synaptics tm2964-001                    	id=15	[slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                   	id=16	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; Integrated Camera: Integrated C         	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=13	[slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                  	id=14	[slave  keyboard (3)]
    &#8627; Logitech K400                           	id=17	[slave  keyboard (3)]


```

---

### Post by ActionParsnip on 2021-02-24
What model Thinkpad do you have, please?

---

### Post by mrdc76 on 2021-02-24
Thinkpad is not the same thing as Thinkbook. Is the OP running the 5.4 kernel? It might be too old for the Thinkbook.

---

