---
title: "How to accelerate the touchpad and the trackpoint on Thinkpad? set-prop not working"
date: 2021-12-05
forum: General Help
---

### Post by orengolan on 2021-12-05
# How to accelerate the touchpad and the trackpoint on Thinkpad? set-prop commands stopped working!

## Reproducing the issue

xinput set-prop 11 325 0.4

```
property '325' doesn't exist, you need to specify its type and format
```

xinput set-prop 14 325 0.8

```
X Error of failed request:  BadAccess (attempt to access private resource denied)
Major opcode of failed request:  131 (XInputExtension)
Minor opcode of failed request:  57 ()
Serial number of failed request:  20
Current serial number in output stream:  21
```

## More Information

cat /etc/lsb-release

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=20.10
DISTRIB_CODENAME=groovy
DISTRIB_DESCRIPTION="Ubuntu 20.10"
```


xinput list 11

```
SYNA8004:00 06CB:CD8B Touchpad          	id=11	[slave  pointer  (2)]
	Reporting 7 classes:
		Class originated from: 11. Type: XIButtonClass
		Buttons supported: 7
		Button labels: "Button Left" "Button Middle" "Button Right" "Button Wheel Up" "Button Wheel Down" "Button Horiz Wheel Left" "Button Horiz Wheel Right"
		Button state:
		Class originated from: 11. Type: XIValuatorClass
		Detail for Valuator 0:
		  Label: Rel X
		  Range: -1.000000 - -1.000000
		  Resolution: 0 units/m
		  Mode: relative
		Class originated from: 11. Type: XIValuatorClass
		Detail for Valuator 1:
		  Label: Rel Y
		  Range: -1.000000 - -1.000000
		  Resolution: 0 units/m
		  Mode: relative
		Class originated from: 11. Type: XIValuatorClass
		Detail for Valuator 2:
		  Label: Rel Horiz Scroll
		  Range: -1.000000 - -1.000000
		  Resolution: 0 units/m
		  Mode: relative
		Class originated from: 11. Type: XIValuatorClass
		Detail for Valuator 3:
		  Label: Rel Vert Scroll
		  Range: -1.000000 - -1.000000
		  Resolution: 0 units/m
		  Mode: relative
		Class originated from: 11. Type: XIScrollClass
		Scroll info for Valuator 2
		  type: 2 (horizontal)
		  increment: 15.000000
		  flags: 0x0
		Class originated from: 11. Type: XIScrollClass
		Scroll info for Valuator 3
		  type: 1 (vertical)
		  increment: 15.000000
		  flags: 0x0
```

xinput list 14

```
TPPS/2 Elan TrackPoint                  	id=14	[slave  pointer  (2)]
	Reporting 7 classes:
		Class originated from: 14. Type: XIButtonClass
		Buttons supported: 7
		Button labels: "Button Left" "Button Middle" "Button Right" "Button Wheel Up" "Button Wheel Down" "Button Horiz Wheel Left" "Button Horiz Wheel Right"
		Button state:
		Class originated from: 14. Type: XIValuatorClass
		Detail for Valuator 0:
		  Label: Rel X
		  Range: -1.000000 - -1.000000
		  Resolution: 0 units/m
		  Mode: relative
		Class originated from: 14. Type: XIValuatorClass
		Detail for Valuator 1:
		  Label: Rel Y
		  Range: -1.000000 - -1.000000
		  Resolution: 0 units/m
		  Mode: relative
		Class originated from: 14. Type: XIValuatorClass
		Detail for Valuator 2:
		  Label: Rel Horiz Scroll
		  Range: -1.000000 - -1.000000
		  Resolution: 0 units/m
		  Mode: relative
		Class originated from: 14. Type: XIValuatorClass
		Detail for Valuator 3:
		  Label: Rel Vert Scroll
		  Range: -1.000000 - -1.000000
		  Resolution: 0 units/m
		  Mode: relative
		Class originated from: 14. Type: XIScrollClass
		Scroll info for Valuator 2
		  type: 2 (horizontal)
		  increment: 15.000000
		  flags: 0x0
		Class originated from: 14. Type: XIScrollClass
		Scroll info for Valuator 3
		  type: 1 (vertical)
		  increment: 15.000000
		  flags: 0x0
```

---

