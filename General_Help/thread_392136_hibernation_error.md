---
title: "hibernation error"
date: 2007-03-24
forum: General Help
---

### Post by stavpal on 2007-03-24
Hi
I have installed ubuntu 6.10. At first hibernate worked. Now though, after I'v e installed nvidia drivers & beryl I get an error on resume:
Something like this (about 4 lines): "usb device (something) descriptor read/64 (something) error -71" etc...
and then a black screen
I've tried the solutions written on this forum about hibernating, but I get the same errors
Does anyone know a solution to this? (windows xp hibernation works fine so there isn't a problem with the pc)

---

### Post by godd4242 on 2007-03-24
> **stavpal said:**
> Hi
I have installed ubuntu 6.10. At first hibernate worked. Now though, after I'v e installed nvidia drivers & beryl I get an error on resume:
Something like this (about 4 lines): "usb device (something) descriptor read/64 (something) error -71" etc...
and then a black screen
I've tried the solutions written on this forum about hibernating, but I get the same errors
Does anyone know a solution to this? (windows xp hibernation works fine so there isn't a problem with the pc)

I have the same problem only without the weird USB references or text at all.
Could you tell me what other solutions you used?
I'd like to try them myself.

---

### Post by stavpal on 2007-03-28
I just searched for "hibernate" in the forums
My swap file is 1gb (ram=512) Maybe it's too low for hibernating ?)

edit: nope, increased it to 1.5gb, still the same (-71) errors

There has got to be a solution....

---

### Post by godd4242 on 2007-03-28
> **stavpal said:**
> I just searched for "hibernate" in the forums
My swap file is 1gb (ram=512) Maybe it's too low for hibernating ?)

edit: nope, increased it to 1.5gb, still the same (-71) errors

There has got to be a solution....

Try making it equal to your RAM?

---

### Post by stavpal on 2007-03-29
nah,,...don't think so. I don't think that the swap size is why it doesn't resume. I'm gonna try suspend2

---

### Post by stavpal on 2007-03-29
ok: for some reasons (partition got f-ed up) I had to re-install linux. Currently (NO NVIDIA DRIVERS INSTALLED), hibernates works, but suspend (to ram) doesn't work, but it doesn't work in windows - so i guess no big deal.
I suspect that nvidia drivers break in a way I don't know the hibernation. (Currently usb  etc work despite these errors I had before the reinstall).

---

### Post by godd4242 on 2007-03-29
> **stavpal said:**
> nah,,...don't think so. I don't think that the swap size is why it doesn't resume. I'm gonna try suspend2

Give it a try for me.
What swap does
As far as I know
Is just save all your open session data to your RAM and stops the HDD so you don't burn power.
Maybe if you're having the swap call on more than is neccasrily there, the computer has a logic error.

Dunno but give it a try for me...

---

### Post by stavpal on 2007-04-01
It's confirmed: nvidia drivers break hibernation. Before I install them hibernate worked perfectly and after the install it doesn't work. Is there a fix or should I try suspend2 or something else

edit: possible fix found

(via google) I found this [https://launchpad.net/ubuntu/+source/acpi-support/+bug/34043](https://launchpad.net/ubuntu/+source/acpi-support/+bug/34043)
and changed my xorg.conf a bit (added these lines pci 1:0:0....and the important "nvAGP" "1"

```

Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
    Driver         "nvidia"
    BusID 	"PCI:1:0:0"
    Option "AddARGBGLXVisuals" "True"
    Option "NvAGP" "1"
EndSection

```

Now hibernation works (STRAM still doesn't but it didn't work before I installed nvidia drivers)
Give it a try. You might solve your hibernation issue.

---

### Post by stavpal on 2007-04-02
edit again. Installed beryl and hibernation broke again!

---

