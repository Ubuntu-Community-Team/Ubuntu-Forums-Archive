---
title: "How do I make the volume wheel on my headphones work?"
date: 2015-01-22
forum: General Help
---

### Post by eliminate1337 on 2015-01-22
I have a G930 Headset which works fine except the volume wheel on the side seems to be bound to the mouse wheel. Is there an easy way to make it work to change the volume?

---

### Post by tgalati4 on 2015-01-22
You should be able to assign the Wheel-up and Wheel-down to VolumeUp and VolumeDown respectively in Keyboard Shortcuts in your Control Panel.  However, you will lose the mouse wheel functionality for all other programs--like scrolling up and down in a webpage.

Open a terminal and post the output of:

```
xinput --list
```

If you have two mousewheels defined then you may be able to use *xinput* to define one for scrolling, leaving the other for volume control.

---

