---
title: "USB-boot-up failure......"
date: 2013-02-02
forum: General Help
---

### Post by pingaan on 2013-02-02
Hi,
 
I´ve been trying for a few hours now and I can´t sort this one out.
When booting up from an Ubuntu usb start-up-stick I´m getting as far as the Grub menu; I get to select if I wan´t to install or go on without installing (trying it out) or continue doing nothing it all.. 
No matter what I choose the screen goes black! 
 
I need some advice.. I need a copy of D next to Win7! :S

---

### Post by Bashing-om on 2013-02-02
pingaan; Hi !

No graphics driver loaded ?
Give this a try and see if you get "try ubuntu" available.

Boot up ubuntu, at the purple splash screen (stick figure and keyboard at bottom of screen) depress any key -> language screen, escape key to accept the default ->boot options screen -> f6 for a list of preset options -> try the "nomodeset" option; f10 to continue the boot into ubuntu. 
12.04 version :launcher ->system settings -> additional drivers: install the recommended driver.
12.10 launcher -> ubuntu software center -> software sources (task bar menu) -> additional drivers (tab).
[INDENT][INDENT][INDENT][INDENT]hth

[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by pingaan on 2013-02-03
Tried everything that you suggested, nothing happens. :-P

What do you mean by loading the graphics driver? How do I load it? 

Hmm.. Would it be different if I created an Ubuntu "alternativ" install drive? Those are with out any special graphics.

Regards.

edit: I tried alternate, same thing; blank screen without reactions from esc, F6 or F10.

---

### Post by pingaan on 2013-02-03
I just noticed, there is a brief message saying 'error: "prefix" not set'. It's just there for half a second.
The message is before Grub.

---

### Post by Bashing-om on 2013-02-03
pingaan;

That  "there is a brief message saying 'error: "prefix" not set'." is weird to me. With Windows 7 on board your system, is "UEFI" booting a factor ?
How is Windows booting, in BIOS mode or in EFI mode? You can find out by typing "bcdedit" in a Windows Administrator Command Prompt window and looking for the "path" line in the "Windows Boot Loader" section. If this line refers to winload.efi, then you're booted in EFI mode; if it refers to winload.exe, then you've booted in BIOS mode.

Have you also confirmed you have a good copy of the .iso file and have burned it as an "image" to the usb device ?

[INDENT][INDENT]try'n to help

[/INDENT][/INDENT]

---

### Post by pingaan on 2013-02-03
I got it sorted a while ago, haven't had time to reply.
 It was UEFI that messed it up! Turned it off and it booted up, right away! :-)

Thanks a ton for taking your time to help me out.

Cheers.

---

### Post by Bashing-om on 2013-02-03
pingaan; Glad ya got it sorted out.

UEFI is the root of many difficulties; I am relieved that I do not have to cope with it on any of my systems. ( my time is coming as I work on other's systems and install ubie as often as I can)

Please mark this thread as solved - thread tools above the posting - aiding others seeking a solution, and saves the aides' time not looking over a solved situation.

[INDENT][INDENT]happy ubuntu'n

[/INDENT][/INDENT]

---

### Post by pingaan on 2013-02-04
I should learn how to bite my toungue! Hehe.. I got passed this issue but soon after I encoubtered a new one! It looks for the files in the cd path, rather than the USB! :-P

They've solved it here but I'm not sure where I should enter the commando.. 

I'll mark the thread as solved as soon as it has been installed! ;-)

Cheers!

---

### Post by pingaan on 2013-02-04
After a bit of browsing the forums I've come to understand that dd is used for creating the actual usb-stick.
Is this correct?

---

### Post by pingaan on 2013-02-04
I just noticed I missed pasting the link I'm talking about. 
[http://ubuntuforums.org/showthread.php?t=2052939](http://ubuntuforums.org/showthread.php?t=2052939)

---

### Post by pingaan on 2013-02-04
I sorted out the boot USB drive now, but I can't seem to boot up the install since it's ISO9660. Is this something you're familiar with?

'edit: Linuxiso.bin missing or corrupt'

---

