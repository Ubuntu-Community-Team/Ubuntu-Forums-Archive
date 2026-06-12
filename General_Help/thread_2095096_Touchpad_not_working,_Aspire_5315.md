---
title: "Touchpad not working, Aspire 5315"
date: 2012-12-15
forum: General Help
---

### Post by Steam. on 2012-12-15
The touch[ad is not working since the install.The keyboard runs just fine, but the touchpad doesn't.

xinput list gives out this<:

```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Areson USB Device                       	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Areson USB Device                       	id=11	[slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                	id=14	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                              	id=15	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; Acer CrystalEye webcam                  	id=12	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=13	[slave  keyboard (3)]

```

But it still does not work.It's not disabled or anything via the keys on the keyboard, it just does not work.Help?

---

### Post by Steam. on 2012-12-16
Wow, no one had this issue with any ALPS touchpad?

EDIT: Started working since I installed this two times(reinstall the 2nd time)the first time it gave out a Bad Error of some sort, but it worked after the 2nd install.

Everything works.

[http://www.mediafire.com/?8g45r1krv6kn685](http://www.mediafire.com/?8g45r1krv6kn685)

```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                              	id=12	[slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; Acer CrystalEye webcam                  	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]
```

---

