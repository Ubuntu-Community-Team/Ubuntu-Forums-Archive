---
title: "Piklab... or alternative?"
date: 2007-02-24
forum: General Help
---

### Post by hvymtlsteve on 2007-02-24
Hi there. Anyone familiar with Piklab at all? I would like to use it to program with my PICKit 2 device on my new machine, I don't want to have to boot up my old Windows machine which is being phased out. 

When I started up the program, I got this:
```
Piklab version: 0.13.3 (rev. distribution)
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
ScimInputContextPlugin()
```

I saw that by default the program was setup for a parallel programmer, so I poked around and figured out how to change it to PICKit 2. 

However, now when I try to do anything, I get this error:
```
USB Port: Error resetting USB device. (err=could not reset: Operation not permitted).
```

According to the sourceforge site, the 2.x firmware is not supported, and I do have the newest firmware, so I suspect I may need to downgrade.. is there any way to do this?
Or is there some alternative software I can use?

Any help is much appreciated,

Steve

---

### Post by louis_nichols on 2007-02-24
Hi! I once wrote a [howto about piklab]("http://ubuntuforums.org/showthread.php?t=123481"). It might help. Incorrect installation might be the source of some problems.

As for the errors above, the first block of errors doesn't have anything to do with piklab. They are just about input peripherals that are not found. I get them too and they are completelly ignorable. The second error suggests it needs root privileges to run. So you should start it with kdesu in front. Either that, or change access permissions to the USB device, which I dunno how to do.

---

### Post by hvymtlsteve on 2007-02-25
Thanks, I did see your thread and used that info to get up and running. 

Also the newest firmware is not supported so I think I'm going to have to downgrade my firmware somehow....

Thanks for the answer!

Steve

---

### Post by stanigator on 2007-09-02
Hi hvymtlsteve,

Which PIC microcontrollers does downgrading the firmware to v1.x work for?

stanigator

---

### Post by hvymtlsteve on 2007-09-15
> **stanigator said:**
> Hi hvymtlsteve,

Which PIC microcontrollers does downgrading the firmware to v1.x work for?

stanigator

Microchip keeps a list of what is compatible... too much for me to list here, and I haven't really kept track of it. I think you might lose compatibility with some dsPIC stuff or 24F (16-bit) things, but I'm not sure. 
I don't think there's that much missing from the compatibility that it's a big issue, not for me anyway. 
I generally use the PIC16F687 or 16F690 for everything I do and those work fine... I also built a little perfboard with a 40-pin DIP socket to connect to the PicKit2,  and verified recognition of a 40-pin 16F917 in Piklab. 

Hope that helps!

Steve

---

