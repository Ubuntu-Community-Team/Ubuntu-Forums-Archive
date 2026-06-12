---
title: "Can not boot from CD! Please help."
date: 2008-05-02
forum: General Help
---

### Post by carl99fan on 2008-05-02
I can not get Ubuntu to start up when restarting the machine. It seems that my computer is not set up to boot from the cd-rom.
I was looking at my bios all night and can not figure it out. I tried EVERYTHING I know. I thought I would include the following Info in case this helps you see the problem, or solution. I also tried installing it "inside" of windows but to no avail. It stops about halfway through and tells me that something else is reading the disk. I looked, and only see explorer and my graphics card deal running. (ATI controller) Here are some of my #s

Vendor-Award software
Version-4.51pg
Release date-7/11/2000
Size- 256kb
Boot devices- floppy disk, hard disk, cd-rom, atapi zip, ls-120
Cap- flash bios, shadow dios, selectable boot, edd
Supported standards- dmi,apm,acpi,escd,pnp
Expansion cap- isa, pci, agp, usb

If you know any way I can get this to work tonight I would greatly apperatiate it.


Now I learned about ubuntu when my Windows ME lost it's "winsock" files and I have just had enough so I CAN NOT get online to fix any of this stuff!

Is there a way I can update the bios without getting online?
I tried to install from safe mode but there is no "d" drive when I am in safe mode. I also can not click on the start button, and it tells me some crap about active x and how I am not allowed, when I click on my computer the window opens but it is empty. What I do is I make a desktop toolbar from the launch area and navigate from there, (this only happens when I am in safe mode) 
If I can download an update and then put it on a floppy then I could update it.

I restarted about 20 times last night and Nowhere do I see anything bout the cd-rom till after windows has started up.
In the bios setting I get to by hitting ctrl h it only gives me one option and says the hdd is the only drive.
In a different screen, the one at the begining that says hit del for setup, Nowhere in any of the areas did I see anything about my cd-rom. It's crazy.
I was reading and I think I can not install it "inside" windows because I am using ME

---

### Post by kshane on 2008-05-02
From inside your BIOS you should see an option to set the boot sequence.  Just ensure that the CD-ROM is the first device, with your hdd being next.

Kevin

---

### Post by carl99fan on 2008-05-02
> **kshane said:**
> From inside your BIOS you should see an option to set the boot sequence.  Just ensure that the CD-ROM is the first device, with your hdd being next.

Kevin

I would but I don't see the cd rom anywhere.
In fact I don't see the cd rom till windows starts.
I am not very knowledgeable, this is the first time I ever paid any attention to bios are any thing else.

---

### Post by kingpoiuy on 2008-05-02
Perhaps this could help.

[HTML]http://www.phoenix.com/en/Customer+Services/BIOS/AwardBIOS/Setup+Information.htm[/HTML]

---

### Post by carl99fan on 2008-05-02
I just need to get online, so I can fix it this weekend!

Is there another way for me to get online with this computer so I can install updates.

Like can I get a simple linux that I can have on Floppys and boot from them till I get this figured out?

Any solution will be good!

---

### Post by koenn on 2008-05-02
from your bios info:

Boot devices- floppy disk, hard disk, **cd-rom,** atapi zip, ls-120
---

get cd-rom on top / in front of that list, or before hard disk in any case.

---

### Post by carl99fan on 2008-05-02
Thanks everybody....
I grabed a computer from work, swapped hard drives and it worked!!!!
Ubuntu is AWESOME!!!!!

it is slow right now but with only 533mhz I wonder if I can inprove it even with ram...
I also wonder if 8.04 might be 2 advanced... But I love it so far!!!

---

