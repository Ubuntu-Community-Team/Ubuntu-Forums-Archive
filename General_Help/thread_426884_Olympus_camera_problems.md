---
title: "Olympus camera problems"
date: 2007-04-28
forum: General Help
---

### Post by Quartlow on 2007-04-28
Ok after much reading lots of editing I still can't get it to work.
Running feisty, camera is an olympus C3000Z

I plug in the USB cable, it detects it as a C2100UZ with this error message

```
An error occurred in the io-library ('Error updating the port settings'): Could not release interface 0 (Invalid argument).
```

I have edited /etc/udev/rules.d/40-permissions.rules. Changed 
```
SUBSYSTEM=="usb_device", MODE="0644"
```
to
```
SUBSYSTEM=="usb_device", MODE="0666"
```

also edited /etc/udev/rules.d/45-libgphoto2.rules
changed
```
BUS!="usb*", GOTO="libgphoto2_rules_end"
```
to
```
SUBSYSTEM!="usb_device", GOTO="libgphoto2_rules_end"
```.

I've read up on it here
[https://launchpad.net/ubuntu/+source/libgphoto2/+bug/91250]("https://launchpad.net/ubuntu/+source/libgphoto2/+bug/91250")

and everything I could find here on the forums searching Olympus and camera.

I also tried to downgrade libgphoto2-port0 and libgphoto2-2 with synaptic but the force version is grayed out. If I boot from my Dapper live CD the camera works fine. Yes I know I could use a card reader but I would prefer to leave the memory card in the camera if at all possible

---

### Post by Quartlow on 2007-04-29
Or, anyway to force libgphoto2-port0 and libgphoto2-2 to an earlier version with the command line?

---

### Post by terrellf on 2007-05-01
Exact same camera and problem here.  I tried the usb* to usb_device thing but that did not work.   I see you tried the others also to no avail.   Glad to know a lot of other people have the same problem and it not just "me" ;-)

I'll probably just have to wait till it gets figured out.  Not a big deal here as long as it will work again someday soon...  Since the first few fixes are not working, probably best to wait till the dust settles.

Terry

---

### Post by Quartlow on 2007-05-05
At least I'm not alone!! :lolflag:

---

### Post by mordalo on 2007-08-18
Has there been any resolution to this problem?
I'm having the same problem with my C-2100UZ.

Worked fine in Dapper...

---

