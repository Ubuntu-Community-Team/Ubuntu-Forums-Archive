---
title: "Changing how many lines a mouse scrolls"
date: 2014-06-27
forum: General Help
---

### Post by boris6 on 2014-06-27
I'm using a USB mouse and Xubuntu and i have a weird issue - i can only scroll a few lines at a time and i haven't been able to figure out how to increase it. 

Has anyone come across a solution?

---

### Post by Nutria on 2014-06-27
> **boris6 said:**
> I'm using a USB mouse and Xubuntu and i have a weird issue - i can only scroll a few lines at a time and i haven't been able to figure out how to increase it. 

Has anyone come across a solution?

I would call that a feature.  In fact, I wish that rotating the mouse wheel would scroll *fewer* lines: 1 or 2.

Better if it were configurable.

---

### Post by tgalati4 on 2014-06-27
tgalati4@Mint14-Extensa ~ $ man xinput
tgalati4@Mint14-Extensa ~ $ xinput --list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; Acer CrystalEye webcam                  	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]
tgalati4@Mint14-Extensa ~ $ xinput --list 11
SynPS/2 Synaptics TouchPad              	id=11	[slave  pointer  (2)]
	Reporting 7 classes:
		Class originated from: 11. Type: XIButtonClass
		Buttons supported: 12
		Button labels: "Button Left" "Button Middle" "Button Right" "Button Wheel Up" "Button Wheel Down" "Button Horiz Wheel Left" "Button Horiz Wheel Right" None None None None None
		Button state:
		Class originated from: 11. Type: XIValuatorClass
		Detail for Valuator 0:
		  Label: Rel X
		  Range: 1472.000000 - 5472.000000
		  Resolution: 78000 units/m
		  Mode: relative
		Class originated from: 11. Type: XIValuatorClass
		Detail for Valuator 1:
		  Label: Rel Y
		  Range: 1408.000000 - 4448.000000
		  Resolution: 120000 units/m
		  Mode: relative
		Class originated from: 11. Type: XIValuatorClass
		Detail for Valuator 2:
		  Label: Rel Horiz Scroll
		  Range: 0.000000 - -1.000000
		  Resolution: 0 units/m
		  Mode: relative
		Class originated from: 11. Type: XIValuatorClass
		Detail for Valuator 3:
		  Label: Rel Vert Scroll
		  Range: 0.000000 - -1.000000
		  Resolution: 0 units/m
		  Mode: relative
		Class originated from: 11. Type: XIScrollClass
		Scroll info for Valuator 2
		  type: 2 (horizontal)
		  increment: 100.000000
		  flags: 0x0
		Class originated from: 11. Type: XIScrollClass
		Scroll info for Valuator 3
		  type: 1 (vertical)
		  increment: 100.000000
		  flags: 0x0

---

