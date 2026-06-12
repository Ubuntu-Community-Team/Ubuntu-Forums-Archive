---
title: "Bios/Keyboard Problem"
date: 2019-06-20
forum: General Help
---

### Post by jgw on 2019-06-20
Today I thought I would take a look at my bios setup.  I re-booted my machine, pressed Del and got to the bios.  I pressed the right arrow to move through the options.  The problem is that nothing happened.  After a couple of minutes the cursor suddenly moved.  I tried the down arrow and nothing moved, then, after a couple of minutes it moved.  Basically the keyboard, which I am using right now with no problem, doesn't want to work real well when in the bios.  This was pretty strange.  I then brought out another keyboard, plugged it into a usb port and that worked fine but behaved exactly like this keyboard.  

So, I obviously have a problem with the bios setup (don't think this is a keyboard problem).  I have no idea what I can do about this one.

Thank you............

---

### Post by CatKiller on 2019-06-20
Two things occur to me, which may or may not be applicable to your case:

Keyboards and mice generally behave strangely when plugged into USB 3 ports. I'm not entirely sure exactly why.

There is generally a "Legacy USB Support" option in the BIOS to help when there isn't a modem OS to take care of input devices.

---

### Post by jgw on 2019-06-21
Thank you for the reply.

I have tried 2 keyboards, one is plugged into a usb port and works fine and the other is plugged into a kvm.  Both work just fine.  My problem is that something happens when I am dealing with my bios.  In that case they keyboard (either one) seems to be seriously in some kind of strange time loop where a pressed key is only recognized after about a minute or so.

Here is my bios (have no idea if this has anything to do with it):
[CODE]
        Vendor: American Megatrends Inc.
        Version: 0502   
        Release Date: 11/18/2016
        Address: 0xF0000
        Runtime Size: 64 kB
        ROM Size: 2048 kB
        Characteristics:
                ISA is supported
                PCI is supported
                PNP is supported
                APM is supported
                BIOS is upgradeable
                BIOS shadowing is allowed
                ESCD support is available
                Boot from CD is supported
                Selectable boot is supported
                BIOS ROM is socketed
                EDD is supported
                5.25"/1.2 MB floppy services are supported (int 13h)
                3.5"/720 kB floppy services are supported (int 13h)
                3.5"/2.88 MB floppy services are supported (int 13h)
                Print screen service is supported (int 5h)
                8042 keyboard services are supported (int 9h)
:
[CODE]

---

