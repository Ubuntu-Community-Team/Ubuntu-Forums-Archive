---
title: "using removable usb media"
date: 2008-04-04
forum: General Help
---

### Post by jacjimus on 2008-04-04
i've been used to mounting and unmounting my usb flash in terminal but the lighting indicator doesnt go off as in windows.what do i do not to spoil it?

---

### Post by keratos on 2008-04-04
elaborate please

---

### Post by LaRoza on 2008-04-04
If it is unmounted, it is safe to remove. If there is data to be written, it would notify you.

Not all computers/operating systems turn off the light, not sure why.

---

### Post by keratos on 2008-04-06
driver can be driven by an interface into the firmware, from userspace apps, or can be standlone within the device - i.e is not driven through the driver module. 

I would suggest this is a firmware driven feature given that it "works" in Windows (through obviously an interface in the windows proprietary driver (DLL) file however  under linux, its proably using a generic interface that does not understand how to drive the feedback (the light).

As said above, if its unmounted, its not in use!

---

### Post by DexterLB on 2008-04-06
In the common case, usb removable media devices use 'human' interface. And you just must plug it in, and ubuntu will mount it for you. If it doesn't have 'human' interface, you must search the net for a linux driver for this media.

---

### Post by keratos on 2008-04-06
> **DexterLB said:**
> In the common case, usb removable media devices use 'human' interface. And you just must plug it in, and ubuntu will mount it for you. If it doesn't have 'human' interface, you must search the net for a linux driver for this media.

Erm, that's total rubbish and misleading.

The HID interface is designed to support Man-Machine interfaces particularly gaming devices, joysticks, mice, keyboards, pens, touch screens etc. HID is simply a device class on the USB subsystem and devices can register themsevles as being part of this class in order to gain access to predefined functions and avail themselves to userspace thrugh the same functions that the HID class provides. In linux, just because a device registers itself through HID does not mean it will function, and invariably it will not unless the USB firmware has also been loaded by the kernel.

It is totally incorrect to suggest that drivers are not required or even that usb hard drives register themselves under the HID class. They might well do, but  quite why god only knows. USB drives would typically register under the "Removable Mass Storage" class (re. kernel space driver support)

HID is a different USB class than USB Mass Storage.

I am sorry to inform you that with regret, you are totally incorrect.

---

### Post by jacjimus on 2008-04-08
thanks for your post! but yet satisfied its correct that when i plug in my !GB DDR2,it gets mounted automatically(visible on desktop)on right-clicking i can u mount it and icon disappears but when i turn to Places-Mycomputer ,i found it mounted in disks.im assuming like in Windows it should NEVER be visible at any location!please help...

---

### Post by jacjimus on 2008-04-08
[you got the challege! mounting should be better programmed  than  the case in Windows..i cant trace the USB 1GB DDR2 in Windows after unmounting it.. then why in Ubuntu? please help:

---

### Post by keratos on 2008-04-08
sorry ,

i do not understand your english.

please re-explain.

---

