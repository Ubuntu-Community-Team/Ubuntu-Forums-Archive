---
title: "Grub does not take over as bootloader (7.10)"
date: 2007-10-19
forum: General Help
---

### Post by Quby on 2007-10-19
The situation here is as follows:
I have had vista installed for a while, and with the new 7.10 kubuntu release i decided to reinstall kubuntu.
I had heard about grub problems before where grub would not see vista, but i figured i would just read a guide on how to fix this..

first problem was that the livecd sometimes did not go to the GUI when i selected the run kubuntu / install 
instead most of the time it would just go to a command line and give me some failed to start xfer error.. 
seems trying over and over i finally just got it to start up like it should, random luck i guess.

So i went through the installation process, making a partition on the same hard drive that contained vista.. when the installation was done, i took out the restarted and took out the cd..
however, no grub bootloader appeared!  The computer booted straight into vista.
How should i go about enabling grub if i cannot even get into linux..?

if you need more info, specs on the computer possibly.. those would be:
ABIT IP-35Pro motherboard
Intel Q6600 Core 2 Quad (2.4ghz)
Sound Blaster X-Fi xtreme gamer (Last time i checked ALSA doesnt cover this sound, no sound for me i guess)
GeForce 8800GTX
2gb ddr2 800mhz..

any clues to this mystery? :confused:

---

### Post by thelocust on 2007-10-20
Sometimes during the install grub doesn't rewrite the MBR so download your self the [Super GRUB disk]("http://geocities.com/supergrubdisk/") and install it that way.

---

### Post by Quby on 2007-10-20
okay, thanks.
I figured i might need to use supergrub.. i just didnt know if it was necessary.

---

