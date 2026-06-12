---
title: "How to correct an erratic mouse pointer"
date: 2013-10-30
forum: General Help
---

### Post by acodea on 2013-10-30
In Ubuntu 12.04, when I return to the computer after being away for a time, the mouse pointer is out of control, jiggling erratically, and I have to press ctrl, alt and del to log off and when I log back in the problem has corrected itself.

---

### Post by rencemc on 2013-10-30
Is it a track pad ? I had that issue on laptop a while back and had to decrease the touch sensitivty.
It started happening in the winter when it was very dry in the house thus creating more static electricity.

---

### Post by acodea on 2013-10-30
> **rencemc said:**
> Is it a track pad ? I had that issue on laptop a while back and had to decrease the touch sensitivty.
It started happening in the winter when it was very dry in the house thus creating more static electricity.

That made a lot of sense to me. A track ball could build up a magnetic or electrostatic charge and that transferred,
but this isn't the same. No this is a logictech mouse, but there is a touchpad I never use. I will look into that, because I didn't. (oops)

DL

---

### Post by rencemc on 2013-10-30
You can disable the trackpad if you are using a mouse to eleiminate that from the picture.

---

### Post by acodea on 2013-10-30
> **rencemc said:**
> You can disable the trackpad if you are using a mouse to eleiminate that from the picture.

How's that?

---

### Post by rencemc on 2013-10-30
Well, my laptop has a button at the top of the touchpad that disables it. I'm not sure what your setup is.
There has to be a way to disable it though - maybe in system settings.

---

### Post by acodea on 2013-10-30
```
synclient TouchPadOff=1
```

thanks rencenmc. Helpful and you'll get credit. Us noobs have to help each other out.

---

### Post by tgalati4 on 2013-10-30
Is this a USB mouse or a wireless mouse?  If USB, then change the port.  Could be dust inside the machine causing stray signals.  If wireless, could be a weak battery.

---

### Post by acodea on 2013-10-30
> **tgalati4 said:**
> Could be dust inside the machine causing stray signals.  If wireless, could be a weak battery.
Good info
It's a usb mouse. Okay. I will blow the dust out of the port and if that doesn't work; I'll give  the mouse its own port.

---

### Post by acodea on 2013-10-31
all of you, thanks, but none of the above answers are the answer. It must be a mouse driver and I'll look for one online. 

This was due to the mouse-tweaks. Uninstalling it corrected the problem.

---

### Post by merlyn2748 on 2013-10-31
It's probably not the mouse driver.  Anymore those drivers are pretty universal.  However, have you verified that your graphics drivers are up to date?

---

