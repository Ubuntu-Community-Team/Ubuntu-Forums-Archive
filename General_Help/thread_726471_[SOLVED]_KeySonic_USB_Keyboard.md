---
title: "[SOLVED] KeySonic USB Keyboard"
date: 2008-03-16
forum: General Help
---

### Post by jeffhills on 2008-03-16
I have bought a KeySonicACK-540RF Keyboard for my HTPC (mythbuntu 7.10) I pluged it in and-nothing.
I have tryed setting the Bios to USB keyboard and mouse, but after I do this Mythbuntu will not load, it just hangs on the splash. The keyboard works fine on my windows M/C, Mythbuntu works fine again after setting the BIOS back to disable USB. I have Googled for hours and I cannot find anybody with the same problem. Any ideas out there please
Jeff

---

### Post by gobbles414 on 2008-03-18
> **jeffhills said:**
> I have bought a KeySonicACK-540RF Keyboard for my HTPC (mythbuntu 7.10) I pluged it in and-nothing.
I have tryed setting the Bios to USB keyboard and mouse, but after I do this Mythbuntu will not load, it just hangs on the splash. The keyboard works fine on my windows M/C, Mythbuntu works fine again after setting the BIOS back to disable USB. I have Googled for hours and I cannot find anybody with the same problem. Any ideas out there please
Jeff

I searched Google and it says that your keyboard can do wireless. Is that correct? If so, you might try using the wireless option. If you want to use USB, you can try a female USB to male PS/2 adapter. Click [here]("http://www.amazon.com/StarTech-GC46FMKEY-StarTech-com-keyboard-adapter/dp/B000A0K2JO") for an example.

Does this help?

---

### Post by jeffhills on 2008-03-18
Thanks for reply. The keyboard is wireless transmitting to a reciever in a usb port. My real problem is I have only managed to load mythbuntu onto this new computer by setting the bios to 'fail-safe defaults',
this turns off the usb ports, as soon as I enable the ports (manually, by BIOS reset or 'load optimized defaults') to use them for anything, mythbuntu will not load from hardrive or disc.
I have unpluged all non-essentials from the MoBo to no effect I really am stuck, Its as if there is a compatability problem with the new MoBo. My experimetal rig, using old bits worked fine, now I have spent a fortune to put together the 'big one' it wont load.
I have
Abit IP35
1 Tb WD SATA HD
Pioneer SATA DVD
2 x 512 667 mem
Intel 6750
8600 GTS
Leadtek DTV200H
2 x Hauppague Nova T 500

Jeff
PS The keyboard workin the BIOS menu just fine

---

### Post by gobbles414 on 2008-03-18
> **jeffhills said:**
> Thanks for reply. The keyboard is wireless transmitting to a reciever in a usb port. My real problem is I have only managed to load mythbuntu onto this new computer by setting the bios to 'fail-safe defaults',
this turns off the usb ports, as soon as I enable the ports (manually, by BIOS reset or 'load optimized defaults') to use them for anything, mythbuntu will not load from hardrive or disc.
I have unpluged all non-essentials from the MoBo to no effect I really am stuck, Its as if there is a compatability problem with the new MoBo. My experimetal rig, using old bits worked fine, now I have spent a fortune to put together the 'big one' it wont load.
I have
Abit IP35
1 Tb WD SATA HD
Pioneer SATA DVD
2 x 512 667 mem
Intel 6750
8600 GTS
Leadtek DTV200H
2 x Hauppague Nova T 500

Jeff
PS The keyboard workin the BIOS menu just fine

Are there any BIOS updates available for your new PC? If you were using normal Ubuntu, I'd advise you to try installing from an Alternate CD instead of a LiveCD. But I don't know if there is an Alternate CD for Mythbuntu or not. I'll have to think about your issue for a while. Meanwhile, perhaps someone else can suggest a solution.

---

### Post by jeffhills on 2008-03-19
Thanks
I have a standard Ubuntu 7.10 CD. I will try load this, will let youi know what happens.
Jeff

---

### Post by jeffhills on 2008-03-19
Trying to load Ubuntu 7.1 gives same result as trying to load Mythbuntu after about 1 min of splash (with DVD whirring) following
[ 183.609530]  ata4.00:exeption Emask 0x0 SAct 0x0 actio 2x2 frozen
[ 183.609567]  ata4.00 cmd a0/00:00:00:20/00:00:00:00:00/a0 tag0 cdb 0x12 data36in
[ 189.749691]  xxxx(as 1st line)
[ 189.749691]  xxxxxxxx(as 2nd line)
[ 200.412189] Buffer I/O error on device fdq logicalblock 0
the loads of liones different number same message


BusyBox v1.1.3 (Debian 1:1.1.1.3-5ubuntu7} Built-in shaell {ash}
Enter 'help' for a list of built in commands.
(initramfs)

Is it possible that the the hard drive is not being seen? I cant see how enabling USB would do this.
are there any other MoBO's that have 3PCI slots out there?
Jeff

---

### Post by gobbles414 on 2008-03-19
> **jeffhills said:**
> Trying to load Ubuntu 7.1 gives same result as trying to load Mythbuntu after about 1 min of splash (with DVD whirring) following
[ 183.609530]  ata4.00:exeption Emask 0x0 SAct 0x0 actio 2x2 frozen
[ 183.609567]  ata4.00 cmd a0/00:00:00:20/00:00:00:00:00/a0 tag0 cdb 0x12 data36in
[ 189.749691]  xxxx(as 1st line)
[ 189.749691]  xxxxxxxx(as 2nd line)
[ 200.412189] Buffer I/O error on device fdq logicalblock 0
the loads of liones different number same message


BusyBox v1.1.3 (Debian 1:1.1.1.3-5ubuntu7} Built-in shaell {ash}
Enter 'help' for a list of built in commands.
(initramfs)

Is it possible that the the hard drive is not being seen? I cant see how enabling USB would do this.
are there any other MoBO's that have 3PCI slots out there?
Jeff

Yes, there are several motherboard out there that have 3 PCI slots, although that would obviously leave less room for PCI Express slots. Someone a lot smarter than me can probably identify all of those error messages for you. Maybe it would be worth your time to try an Ubuntu Alternate CD and/or the most recent build of Ubuntu 8.04.

BIOS updates...?

---

### Post by jeffhills on 2008-03-19
Next installment.
I Have changed the HDD to an old 200GB PATA and it all works fine, from what I have Googled there are some SATA management problems with this MoBo and Ubuntu, but generally from guys trying to mix SATA and IDE!
I have loaded Windows XP, this runs just fine (including the keyboard) on the SATA HDD.
Can anybody suggest a MoBO with 3 PCI slots no blocked by a double graphics card to use a 6750?
I will try to update the BIOS, I have never done this before, the instructions call for a floppy, I havent had a floppy drive for years, can it be done with a CD?
Jeff

---

### Post by gobbles414 on 2008-03-20
> **jeffhills said:**
> Next installment.
I Have changed the HDD to an old 200GB PATA and it all works fine, from what I have Googled there are some SATA management problems with this MoBo and Ubuntu, but generally from guys trying to mix SATA and IDE!
I have loaded Windows XP, this runs just fine (including the keyboard) on the SATA HDD.
Can anybody suggest a MoBO with 3 PCI slots no blocked by a double graphics card to use a 6750?
I will try to update the BIOS, I have never done this before, the instructions call for a floppy, I havent had a floppy drive for years, can it be done with a CD?
Jeff

Some motherboards can be updated with a CD and/or USB flash drive. It mostly depends on the manufacturer. Also, many newer motherboards and towers have built-in FireWire and USB 2.0 ports. So you may not need to use PCI cards for those.

---

### Post by jeffhills on 2008-03-22
BIOS updated no change, I dont want to admit defeat but I think I will just buy a new MoBo with a different chipset

---

### Post by jeffhills on 2008-03-22
Got it at last, I wish I knew how, but the BIOS update AND switching to SATA 5 and 6 ( the higherst numbers available has done it!

---

### Post by gobbles414 on 2008-03-22
> **jeffhills said:**
> BIOS updated no change, I dont want to admit defeat but I think I will just buy a new MoBo with a different chipset

Both Mythbuntu and regular Ubuntu recently released a beta of version 8.04 -- which can be found on the respective homepages. Before you spend more money on new hardware, I suggest that you try the beta.

---

### Post by gobbles414 on 2008-03-23
> **jeffhills said:**
> Got it at last, I wish I knew how, but the BIOS update AND switching to SATA 5 and 6 ( the higherst numbers available has done it!

Congratulations! Perhaps your workaround won't be necessary in version 8.04.

---

