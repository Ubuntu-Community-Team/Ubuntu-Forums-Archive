---
title: "Skinning Grub"
date: 2007-02-14
forum: General Help
---

### Post by Spr0k3t on 2007-02-14
This is going to sound like an odd request, but I can assure you that this is not for me, but others who will be accessing the computer.

Currently, I have a dual boot on a work laptop that I would like to hide the linux side of.  Essentially, set up the device so that without either a keypress or key qualifier, the boot looks like a normal "boot.ini" request load.  Is this possible?

---

### Post by Kateikyoushi on 2007-02-14
There are a few ideas in this thread. [LINK]("http://ubuntuforums.org/showthread.php?t=266488&highlight=hide+grub")

You could also restore the ntloader and load linux from it but that's more complicated.

---

### Post by logos34 on 2007-02-14
I thought you could just uncomment 'hiddenmenu' line in /boot/grub/menu.lst...although maybe something from grub still flashes on the screen

---

### Post by drivel on 2007-02-14
How to make Grub with Ubuntu looks like the Suse's?

---

### Post by yabbadabbadont on 2007-02-14
> **drivel said:**
> How to make Grub with Ubuntu looks like the Suse's?

[http://www.ubuntuforums.org/showthread.php?t=208855](http://www.ubuntuforums.org/showthread.php?t=208855)

---

### Post by drivel on 2007-02-14
> **yabbadabbadont said:**
> [http://www.ubuntuforums.org/showthread.php?t=208855](http://www.ubuntuforums.org/showthread.php?t=208855)

Thanks.
The Suse's is pretty beautiful.

---

### Post by Spr0k3t on 2007-02-14
> **logos34 said:**
> I thought you could just uncomment 'hiddenmenu' line in /boot/grub/menu.lst...although maybe something from grub still flashes on the screen

Yeah, something from grub still flashes on the screen.  I'd like to hide any evidence of Linux installed on the system... after all... this is my company's laptop, not mine.

---

### Post by logos34 on 2007-02-14
> **Spr0k3t said:**
> Yeah, something from grub still flashes on the screen.  I'd like to hide any evidence of Linux installed on the system... after all... this is my company's laptop, not mine.

Why not make a grub boot floppy?  (not sure how to erase grub from the mbr, though)
(Edit: half asleep here...after you make grub floppy just restore widows ntldr/bootloader by booting into recovery console on windows install cd and 'fixmbr').

[https://help.ubuntu.com/community/GrubHowto/BootFloppy](https://help.ubuntu.com/community/GrubHowto/BootFloppy)

*if you get an error when trying to boot the main kernel, take out 'savedefualt' option

---

### Post by Spr0k3t on 2007-02-14
> **logos34 said:**
> Why not make a grub boot floppy?  ...

Bootfloppy won't work.  The only reason I was able to get ubuntu installed was through PXE installer.  The laptop is so small, it doesn't even have room for a CD/DVD drive.  This thing is prabably the closest to a palmtop you can get without microsozing the keys.  To use a floppy boot, would require some sort of dongle hanging out of this laptop.  Considering how much I am on the go, it's not the best of choices.

Dimensions: 5/8" x 11-1/8" x 7" (HxWxD).  Smaller than a spiral notebook.

---

### Post by logos34 on 2007-02-14
> **Spr0k3t said:**
> Bootfloppy won't work.  The only reason I was able to get ubuntu installed was through PXE installer.  The laptop is so small, it doesn't even have room for a CD/DVD drive.  This thing is prabably the closest to a palmtop you can get without microsozing the keys.  To use a floppy boot, would require some sort of dongle hanging out of this laptop.  Considering how much I am on the go, it's not the best of choices.

Dimensions: 5/8" x 11-1/8" x 7" (HxWxD).  Smaller than a spiral notebook.

Hmm...if there's no optical drive and even a slim usb floppy drive isn't an option (which you can disconnect right after boot), then don't know what to suggest other than that there is a way apparently to use the windows ntldr to boot ubuntu by putting a kernel entry in the boot.ini file (search the forums)..never tried it myself...but you might be able to rig it for invisible mode

---

### Post by crysys on 2007-02-14
Can the laptop boot from a USB device?  You could put your MBR on a USB thumb drive and set the BIOS boot priority to USB first.  This should essentially leave the NT MBR untouched and the computer will automatically boot into windows unless the thumb drive is plugged in.  It's just the MBR so some tiny, throw away thumb drive should work fine and it won't have to be left plugged in once the laptop is booted.

---

### Post by Spr0k3t on 2007-02-15
I'm going to give that idea a shot.  For now I've hid grub and wait for response for 1 second but defaults to XP.  Gives me the option to boot Ubuntu still, perhaps the boot key will work.  I already have like three of these keys hanging around my neck most of the time, what's one more?

---

