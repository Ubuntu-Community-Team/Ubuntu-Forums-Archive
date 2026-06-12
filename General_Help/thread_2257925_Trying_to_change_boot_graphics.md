---
title: "Trying to change boot graphics"
date: 2014-12-23
forum: General Help
---

### Post by GARoss on 2014-12-23
Maybe I got side tracked?  My monitor is 1920x1200 & the grub text is very small so I wanted to enlarge the text.  Then I ran across rEFInd & decided that would not only fix the small text but add a nice graphic touch to my newly installed 14.04 64-bit dual boot with Windows 7 64-bit computer.  Ubuntu Software Centre says it's installed but says it runs from the terminal.  All that does is opens the boot dialogue for editing.  I guess I've had too much Windows because I was looking for a custom graphic to select how it would look.  Did something not install properly or is other rEFInd software needed?  My system is a new install so maybe something didn't install correctly.  I have been experiencing errors trying to install various software.  

It seems to of done everything but install but to be honest, I'm not confident of my computer skills.  Below is a screen grab from Windows Disk Management.  I'm not sure which Windows boot I have UEFI or BIOS so maybe that's the problem.  

[ATTACH=CONFIG]258751[/ATTACH]

---

### Post by grahammechanical on 2014-12-23
UEFI or BIOS? There is no way of telling from that screenshot. But, I guess that if we have BIOS, then rEFInd is not for us. But I may be wrong about that. But I do not think so.

> [COLOR=#000000][FONT=Times New Roman]Under Linux, by contrast, things can get complicated. As detailed on my [/FONT][/COLOR][Managing EFI Boot Loaders for Linux]("http://www.rodsbooks.com/efi-bootloaders/index.html")[COLOR=#000000][FONT=Times New Roman] page, several different EFI boot loaders for Linux exist, and all of them require configuration. If you're lucky, your distribution will have set up a Linux boot loader in a sensible way, in which case rEFInd should detect it and it will work as easily as a Windows or Mac OS X boot loader. [/FONT][/COLOR]

[http://www.rodsbooks.com/refind/linux.html](http://www.rodsbooks.com/refind/linux.html)

I do not think that rEFInd is designed to provide a graphic image as a background to the boot menu screen. You have to make a decision. Do you want help to increase the font size in the Grub boot menu? Or do you want help understanding what rEFInd can do? I would be wasting my time explaining how to change the font size of Grub or how to put an image as the background to the Grub menu if you are no longer using Grub as the boot loader.

Regards.

---

### Post by GARoss on 2014-12-23
> **grahammechanical said:**
> UEFI or BIOS? There is no way of telling from that screenshot. But, I guess that if we have BIOS, then rEFInd is not for us. But I may be wrong about that. But I do not think so.



[http://www.rodsbooks.com/refind/linux.html](http://www.rodsbooks.com/refind/linux.html)

I do not think that rEFInd is designed to provide a graphic image as a background to the boot menu screen. You have to make a decision. Do you want help to increase the font size in the Grub boot menu? Or do you want help understanding what rEFInd can do? I would be wasting my time explaining how to change the font size of Grub or how to put an image as the background to the Grub menu if you are no longer using Grub as the boot loader.

Regards.

I rebooted to check which boot I have.& I have BIOS so I've un-installed rEFInd.  Thanks for your help.

---

