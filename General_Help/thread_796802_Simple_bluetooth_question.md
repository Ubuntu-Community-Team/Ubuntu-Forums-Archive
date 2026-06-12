---
title: "Simple bluetooth question"
date: 2008-05-16
forum: General Help
---

### Post by gforster on 2008-05-16
I know the command ls usb gives me what my system detects as far as usb devices and the names it shows them as. lspci does a similar thing for pci interface devices. Is there something that will do the same for bluetooth?

*if you've seen any of my posts lately you might be able to tell the whole bluetooth gig is new to me.  Thanks for your patience.

---

### Post by SpaceTeddy on 2008-05-16
```
sudo hcitool scan
```

i don't know of the sudo is neccessary. It's been a long time since i have done this :)

---

### Post by gforster on 2008-05-17
Thank you, but when i enter it (with or without sudo) it says Scanninng. . . and then gives me another prompt.  funny, because I am currently using my bluetooth keyboard/mouse, but apparently it does not recognize them?  At least through this method. Maybe because they're already paired?

---

### Post by priegog on 2008-05-17
> **gforster said:**
> Maybe because they're already paired? Yeah, that command only shows devices which are in pairing mode. I do all my bluetooth stuff graphically with an app called [Blueman]("http://blueman.tuxfamily.org/"), so I wouldn't know. But try that out. It has a button that's called "list seen" that shows me all my devices, connected or not.

---

