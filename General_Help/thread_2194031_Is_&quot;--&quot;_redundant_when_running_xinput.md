---
title: "Is &quot;--&quot; redundant when running xinput?"
date: 2013-12-16
forum: General Help
---

### Post by vasa1 on 2013-12-16
When I run [FONT=Courier New]xinput --list[/FONT] I get this:
```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; PixArt USB Optical Mouse                	id=10	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                              	id=12	[slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; Integrated_Webcam_1.3M                  	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                        	id=14	[slave  keyboard (3)]

```
But I get the same result with [FONT=Courier New]xinput list[/FONT].

So why is the "--" redundant?

---

### Post by vasa1 on 2013-12-16
[http://unix.stackexchange.com/q/105364/15760](http://unix.stackexchange.com/q/105364/15760)

---

