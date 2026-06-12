---
title: "bluetooth mouse Logitech MX Master 3S"
date: 2024-03-10
forum: General Help
---

### Post by ValentynPrumers on 2024-03-10
I can connect the mouse through bluetooth and it works. But when i dont touch it for a few seconds, and then start moving the mouse. The mouse
pointer pauses for a fraction of a second and re-appears on screen 1-2cm in the direction i moved the mouse. As long as i keep moving the mouse everything works fine. 

I tried to install blueman. But the problem remains. Btw now i have 2 bluetooth icons in my statusbar. If anyone knows how to disable the standard bluetooth manager that would also be helpfull.

---

### Post by ValentynPrumers on 2024-03-11
Tried to install the Solaar package. And that seemed to work. But alas..same problem. Every time I let the mouse rest for 10 seconds..there is a short lag
when i resume movement.

---

### Post by ValentynPrumers on 2024-03-11
I tried this solution:

[https://www.reddit.com/r/Ubuntu/comments/ji5oin/bluetooth_mouse_lagging/](https://www.reddit.com/r/Ubuntu/comments/ji5oin/bluetooth_mouse_lagging/)

And up till now it actually works :) So it seems to be a USB auto suspend problem. Don't know why its called usb, as its a bluetooth device,

The solaar package works great btw. I managed to program all buttons (except for the thumb button).

EDIT: can confirm this fixed the lag completely.

---

