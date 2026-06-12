---
title: "bad screen"
date: 2013-01-07
forum: General Help
---

### Post by spiders on 2013-01-07
hi all

when i run get-edid i get this:
```

get-edid: get-edid version 2.0.0

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
    Function supported
    Call successful

    VBE version 300
    VBE string at 0x11100 "Intel(r) 82945G Chipset Family Graphics Chip Accelerated VGA BIOS"

VBE/DDC service about to be called
    Report DDC capabilities

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
    Function supported
    Call successful

    Monitor and video card combination does not support DDC1 transfers
    Monitor and video card combination supports DDC2 transfers
    0 seconds per 128 byte EDID block transfer
    Screen is not blanked during DDC transfer

Reading next EDID block

VBE/DDC service about to be called
    Read EDID

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
    Function supported
    Call successful

&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;0d!~"&#65533;&#65533;&#419;WJ&#65533;#OT&#65533;&#61441;&#65533;1
&#65533;OqJqO&#65533;4@Q
                @8@R&#65533;2N
P
      &#65533;             &#65533;17"LCDMONITORW

```so as you can see my monitor is corrupted but it will work just as long as the screen resolution doesn’t change, when it does it shows " no input" and to get it working you have to (in this order or it will not work) unplug cable from computer and turn off at **wall** and plug cord back in and then turn on at wall, however before i had ubuntu i had gentoo with kde and to stop it i run gentool --menuconfig and forced it to keep the same resolution  (or genkernal i forget the command) but i don't know how to do that in ubuntu.

also when i say so long as the screen resolution doesn’t change i mean that it "no inputs" from login screen after i type my password in and when i open up a wine application and things smiler to that

to finish up i know that the most sensible thing to do is buy a new screen but i am a not exactly a millionaire

any help would be appreciated

---

