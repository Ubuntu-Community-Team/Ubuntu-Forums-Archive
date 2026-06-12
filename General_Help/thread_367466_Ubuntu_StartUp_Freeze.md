---
title: "Ubuntu StartUp Freeze"
date: 2007-02-22
forum: General Help
---

### Post by fresch1 on 2007-02-22
Hi People..

I recently decided i wanted to try out ubuntu, and thanks for the great help on this forum so far.

I just got to the point where i wanted to start out by downloading Ubuntu 6.10, and burn it to a disc (The slowest i could burn was 8x).

When i insert the disc, turn on my computer, the pc boots from the disc, and i get a Menu with a Big ubuntu logo.

Now, when i select the "Start Ubuntu" option, the ubuntu logo appears, with a progress bar..
It runs for at minute or so, and then it freezez.
The progress bar dosent move or anything..

GREAT Ubuntu....  

My Pc is up to date, and every hardware part works as it should.
My system is

* AMD Athlon 64 3500+
* 1 GB Ram
* MSI K8N Neo4 Mainboard
* Ati Radeon x1950 pro

My Harddrives are sat up this way if that has anything to do with it:

Harddrive 1 - Seagate IDE 80 Gb.
Partition 1 - 20 gb: Windows Vista System
Partition 2 - 60 gb: Empty (Want to use this for Ubuntu)

Harddrive 2 - Seagate SATA 300 Gb
Partition 1 - 200 gb: Storage
Partition 2 - 100 gb: Storage

Harddrive 3 - Seagate SATA 300 Gb
Partition 1 - 300 gb: Storage


I hope you can help, as this really annoys me.. :/
Other people are having the same problem but noone seems to have a solution.
This is so wierd.
I Also tried to check the disc from the menu, and the dics was fine.
Safe Graphics mode did the same freeze as the normal startup.

Then heard that you could try to use som startup commands by pressing F6.
I tried to run the startup without the splash screen, and the startup froze at this point:

[IMG]http://frip.dk/helious/Ubuntu.jpg[/IMG]


A person asked my to try another startup command instead.
I tried the:  irqpool pci=noacpi noapic nolapic acpi=off, command, and that changed some things.

Now it freezes with this instead:

[IMG]http://frip.dk/helious/Ubuntu2.jpg[/IMG]


I dont know what to do..
I also tried to download the DVD version of Ubuntu 6.10, and when the Disc startet up, it gave me some new options prior to "Start or Install".
I tried the "OEM Install", and that worked so far. 
I installed ubuntu through some "DosLike" installer, and when the installation was finished it booted up the Grub(?) Boot manager.
I Chose Ubuntu, and it does the Exact same thing as with the Live cd.

Freezes the point, of the first screenshot, and when i put in the irqpool pci=noacpi noapic nolapic acpi=off command, it still gives me the screen from the second screenshot.

This really annoys me, as this is my first time EVER with linux.
.Please.. Can someone help?

---

