---
title: "Ubuntu refuses to recognize one of my mouse buttons, links others together"
date: 2008-05-19
forum: General Help
---

### Post by Tken on 2008-05-19
I have a Logitech LX7, which has a tilt-wheel and two extra buttons, for a total of 9 buttons (left click, right click, left tilt, right tilt, mwheelup, mwheeldown, mouse wheel click, and the two buttons).  My xorg.conf file reflects this:

```
Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5"
	Option      "Buttons" "9"	
	Option 	    "Emulate3Buttons" "true"
	Option      "Protocol" "ExplorerPS/2"
	Option      "ButtonMapping" "1 2 3 6 7 8 9"
EndSection
```

Using xev (and/or imwheel -c, they gave the same results), I was able to find out that the left tilt and the first extra button are both mapped to 6, the second extra button is 7, and right tilt does not register at all.  Everything else is mapped logically, and there does not seem to be an 8 or 9 (though changing Buttons to 7 in xorg.conf changes nothing).

How can I get Ubuntu to register my right tilt wheel, and how can I make it so my two extra buttons actually *are* extra buttons, not just copies of other buttons?  I've been googling all night to no avail.

Thanks in advance.

---

### Post by Shazaam on 2008-05-19
I use an app called btnx to change the buttons on my MX 1000. There are other ways to do it. Search the How-To sub-forum, there are a couple of threads that deal with configuring Logitech mice.

---

### Post by Tken on 2008-05-19
> **Shazaam said:**
> I use an app called btnx to change the buttons on my MX 1000. There are other ways to do it. Search the How-To sub-forum, there are a couple of threads that deal with configuring Logitech mice.

Isn't btnx just for binding functions/keys to buttons?  That wouldn't help me, since Ubuntu doesn't even recognize the existence of a button.  If I can just fix that, binding is the easy part.

---

### Post by Tken on 2008-05-19
I've spent a few hours now fiddling with xorg.conf with nothing to show for it, and as suspected btnx can't help because it has no event to catch from my pressing the tilt wheel.  Anyone have an idea?

---

