---
title: "Incorrect resolution"
date: 2016-01-24
forum: General Help
---

### Post by slavikg on 2016-01-24
I installed Lubuntu on a Dell Inspiron mini 10. The panel native resolution is 1024x600, but for some reason both BIOS and Linux think it is 1024x600. I have figured out how to add the 1024x600 resolution. The problem is that when I set the resolution to 1024x600 (using xrandr), the desktop appears to be lowered by 128 pixels, resulting in a black bar at the top. Is there a way to instruct xrandr to move the desktop up 128 pixels? (I couldn't figure this out from google searches and from the man page).

---

### Post by ajgreeny on 2016-01-24
> **slavikg said:**
> I installed Lubuntu on a Dell Inspiron mini 10. The panel native resolution is 1024x600, but for some reason both BIOS and Linux think it is 1024x600. I have figured out how to add the 1024x600 resolution. The problem is that when I set the resolution to 1024x600 (using xrandr), the desktop appears to be lowered by 128 pixels, resulting in a black bar at the top. Is there a way to instruct xrandr to move the desktop up 128 pixels? (I couldn't figure this out from google searches and from the man page).
I'm afraid you have lost me totally as all your resolution figures seem to be the same so no error should be showing anywhere unless you have a hardware fault.  Did the live OS run and display properly?.

Is this netbook, ie a small old laptop?

---

### Post by slavikg on 2016-01-24
It's a netbook. LiveCD experiences the same thing. I have found through a random Amazon review of a replacement screen that this is due to a faulty connection to the LCD. I pushed the connector in and it worked as it should've. Also, using get-edid I got different results between when the screen connector was fully in and pushed in, vs not.

---

