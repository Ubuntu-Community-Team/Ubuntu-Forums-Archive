---
title: "HP ProLiant ML370 G4 | No video output / Tried intergraded &amp; PCIx &quot;card&quot;"
date: 2021-01-26
forum: General Help
---

### Post by charitosha on 2021-01-26
Hello Everybody.

Hope that everyone is in good health.

Recently i was given a server, specifically HP ProLiant ML370 G4.
In short my problem is that i receive no video output (Cannot even see the BIOS, thus if intergraded GPU is inactivated i cannot do anything about it ).

Before writing this post, i just want to tell that, i have downloaded the maintenance and service guide for this server (manual) and made some troublehsooting on my own

In short, let me tell you what i have tried:
        -  At the beginning i tried to use the inter-graded GPU:  

[LIST]
[*]All internal components are connected correctly. I am saying this because the internal system health LED is green, the RAMs LED are off (thus connected in a correct manner - as stated in the manual), CPU LEDs, PPM LED are all off thus connected correctly as well 
[*]I have also tried the minimal boot up: with one CPU and two memory sticks installed. All error LEDs are off but still no Video output 
[/LIST]
        -  Then i used a graphics card, because i could not find a PCIx graphics card i bought a pcix to pcie converter (used a DDR3 graphics card). Still could not get a video output. Have tried the minimal boot up as well but with no fruitful results 

In all cases, the power supply was working correctly. I am saying because all fans were working, initial buzzer sound was working as well, and even when i tried my GPU card, its fans were spining.

I mean obviously the machine is in operational condition but i am missing something and do not know what exactly.

Can anybody help me in any way?

Thank you,
Hariton

---

### Post by grahammechanical on 2021-01-26
only guesses and stating the obvious.

Is the monitor working? Is the monitor cable faulty? What video output to monitor? VGA? HDMI? Something else? The machine's BIOS will output a low resolution video mode. Is the monitor specified to display that resolution and frequency?

These kind of problems force a person to try anything. Even things that others would dismiss as unnecessary. There should be some video output. The BIOS should show error messages even if items of hardware are not installed. Such as CPU, memory or keyboard and OS. Some BIOS use bleeps as warnings that things are not right.

An unlikely suggestion is to find out if a Ubuntu live session loads and shows video output. At least it will test the video signal through the motherboard to the monitor.

Not much help. sorry. 

Regards

---

### Post by charitosha on 2021-01-27
Just to note the monitors, i tried two, were working perfectly.
i tried an old LED monitor and even older LCD monitor. both in an operating condition.
As for cables, i have tried VGA and DVI d cable. Both working and operational.

The server is way too old for HDMI, but with the cables i tried i dont think that i have as a resolution gap

---

### Post by mastablasta on 2021-01-27
try live USB  and desktop. see if anything shows. you may need to guess what you are pressing to get it to boot.

could be that pcix is faulty.

also i had an older motheboard and i wanted to add new PCIe GPU to replace the default AGP one (board had both options). but i got nothing. no output. card worked well, monitor worked well. just no output no matter what output or cable i tried. i guess the card was not supported by the old motherboard for some reason.  i returned the card and had ot put the old one back in. until finally i got tired of all issues and got a new PC.

---

