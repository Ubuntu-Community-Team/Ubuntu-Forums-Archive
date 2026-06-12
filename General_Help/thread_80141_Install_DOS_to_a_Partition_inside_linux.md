---
title: "Install DOS to a Partition inside linux?"
date: 2005-10-21
forum: General Help
---

### Post by termin8tor on 2005-10-21
Alright so I flashed my DVD drive within windows (windows crashed) which caused my drive to die, now as I don't have a floppy drive I have no way to boot dos (which I need) to fix my dvd drive using the repair utility the DVD Drive manufacturer provided.

So I was hoping there is a way I can install Dos to a Fat16 partition from within linux, and then configure GRUB to boot into dos.

So far I tried simply copying all the DOS floppydisk files onto a fat16 partition and having GRUB boot into it using a chainloader, however I get a no operating system found type error.

Any help or alternate solutions to my problem would be awesome.

---

### Post by termin8tor on 2005-10-21
Please excuse me, I hate doing this but BUMP

---

### Post by Gandalf on 2005-10-21
why dont you try to launch the patcher via wine :roll:

---

### Post by termin8tor on 2005-10-21
Because I cant plug the DVD Drive in whiles the computer is on Or i wont get past the post screen. The way i need to do it is boot dos and reflash the drive from within dos (boot dos, plug ide cable in whilest the p.c is on and flash.)

<edit> I'd like to thank you for that VHCS script you made for hoary, it got my VHCS working under breezy =)

---

### Post by Gandalf on 2005-10-21
[QUOTE=termin8tor]Because I cant plug the DVD Drive in whiles the computer is on Or i wont get past the post screen. The way i need to do it is boot dos and reflash the drive from within dos (boot dos, plug ide cable in whilest the p.c is on and flash.)

<edit> I'd like to thank you for that VHCS script you made for hoary, it got my VHCS working under breezy =)[/QUOTE]
:shock: this can't be done, you cant flash a drive Bios did not detect it on booting, am i wrong? :shock:

Oh No problem :D

---

### Post by BIGtrouble77 on 2005-10-21
You're probably gonna need to get a usb floppy drive.  None of the machines I build for work or home have floppies, but I always have my usb floppy drive close by for bios updates and raid configuring.

One thing you may be able to do is boot from a usb flash drive to dos.  I haven't tried doing that yet, but here's some instructions:
[http://www.weethet.nl/english/hardware_bootfromusbstick.php](http://www.weethet.nl/english/hardware_bootfromusbstick.php)

You'll need to find a windows machine to do the above.

-BT

---

### Post by Ocxic on 2005-10-21
I can tell you for fact that you will not be able to plugin your cdrom AFTER the computer is turend on, scince the bios has not detect you cdrom, you will never be able to access it, unless your recovery software is telling you different, if your comp freezes at POST when it's unpluged, all i can say is that i hope your warrenty covers
the screw up.... AND NEVER FLASH ANYTHING IN WINDOWS EVER.... your only asking for trouble, do it in dos mode,, ONLY dos mode.

---

### Post by BIGtrouble77 on 2005-10-21
[QUOTE=Ocxic]I can tell you for fact that you will not be able to plugin your cdrom AFTER the computer is turend on, scince the bios has not detect you cdrom, you will never be able to access it, unless your recovery software is telling you different, if your comp freezes at POST when it's unpluged, all i can say is that i hope your warrenty covers
the screw up.... AND NEVER FLASH ANYTHING IN WINDOWS EVER.... your only asking for trouble, do it in dos mode,, ONLY dos mode.[/QUOTE]

Now that I think about it, the only way he'd be able to pull that off is if he had another identical drive and swapped them after booting.  And that's if the machine doesn't lockup or reboot in the process.  

I've heard of people swapping bios chips while the machine was on to flash the bad one, but a dvd drive is another story because you have power going to it.

---

### Post by Donza on 2005-10-21
[QUOTE=Ocxic]I can tell you for fact that you will not be able to plugin your cdrom AFTER the computer is turend on, scince the bios has not detect you cdrom, you will never be able to access it, unless your recovery software is telling you different, if your comp freezes at POST when it's unpluged, all i can say is that i hope your warrenty covers
the screw up.... AND NEVER FLASH ANYTHING IN WINDOWS EVER.... your only asking for trouble, do it in dos mode,, ONLY dos mode.[/QUOTE]

It depends on the flashing programm but theoreticaly you can do it. I have done it. After boot I plugged my dead DVD-burner's ide-cable in and the flashing program allowed me to just chose if it was primary or secondary and slave or master. The flashing program needed just that h/w address where the drive was plugged in and voila I had a working DVD-burner.

---

### Post by Dr. Nick on 2005-10-21
Do you have a cdburner hooked up to a windows pc loaded with nero? You may look into just making a cd bootable and copying the flash files onto the cd and booting off of it, I have had to do this to flash a video card bios. The reason I reccomend nero is just because it has a version of dos included for making stuff bootable.

---

### Post by graigsmith on 2005-10-22
get a second drive, connect both to power, connect ide to good drive. boot, connect ide to bad drive, and flash.  might work, might break things...  

Also, Never play with power cords while the computer is on.  you probably wont shock yourself, but there is a very high chance you might FRY the dvd drives.  those power cords are NOT made to be hot swappable.

---

### Post by graigsmith on 2005-10-22
[QUOTE=Ocxic]I can tell you for fact that you will not be able to plugin your cdrom AFTER the computer is turend on, scince the bios has not detect you cdrom, you will never be able to access it, unless your recovery software is telling you different, if your comp freezes at POST when it's unpluged, all i can say is that i hope your warrenty covers
the screw up.... AND NEVER FLASH ANYTHING IN WINDOWS EVER.... your only asking for trouble, do it in dos mode,, ONLY dos mode.[/QUOTE]
i have flashed things in windows 2000 and xp before, never had any problems doing it that way.   i have flashed things in dos before as well.  and once, dos actually froze in the middle of flashing my pentium 2 233's motherboard's bios.  i waited, waited and waited.  I was sad :(

---

### Post by termin8tor on 2005-10-22
Well I got it working, I opened my xbox and gerry rigged its DVD drive (while it was still inside the xbox into the p.c, powered on the xbox to provide it with power, then powered on my p.c, I used a dr dos caldera bootdisk I had lying around in the xbox drive to boot into dos, I then used the manufacturer provided flash program (i swapped the ide from my xbox into my DVD drive as it was still all powered on and bham, working DVD drive again....

morale of the story? microsoft products have their uses!

---

