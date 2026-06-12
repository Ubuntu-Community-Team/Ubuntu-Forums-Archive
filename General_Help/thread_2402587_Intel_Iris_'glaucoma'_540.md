---
title: "Intel Iris 'glaucoma' 540"
date: 2018-10-02
forum: General Help
---

### Post by carmichaelits on 2018-10-02
Hello folks,


 I am having a curious issue with a DELL XPS 13 9350


 With the correct Iris drivers installed, the computer will boot into a black screen; and only work with an external monitor.


 The issue goes: Bios (can see) > Boot logo (can see) > Login screen (black)


In Ubuntu. The desktop will only  load if grub has been set to nomodeset. If Ubuntu is installed on the  main drive, and nomodeset is enabled. Elements on the desktop load  really slow. Although, if nomodeset is enabled on the live installer, it  runs fairly smooth.

What I have done so far: ( computer was supplied with Ubuntu )


 
[LIST=1]
[*] Linux kernel was on 4.15 > reverted this back to 4.13 in grub = Worked

[*] Attempted to boot into 18.04 installer, to install 18.04 = Black screen on desktop - had to set to nomodeset

[*] Installed 18.04 on main disk with nomodeset enabled = ran really slow - tried updating and switching back, no joy.


[*] Installed Windows 10, Installed Dell Drivers = Black screen on desktop.
[/LIST]
       4a. Re-installed Windows 10, installed Intel Drivers = Black screen on desktop.

 
[LIST=1]
[*] Updated Dell BIOS to version 1.7 under Windows = Black screen on desktop.


[*] Switched from UEFI to Legacy, made sure I was on AHCI, switched  around some processor settings ( clutching at straws ) = Black screen at  desktop.


[/LIST]
 Now I am trying to install Ubuntu to then set the graphics driver to the one that works from the boot installation.


 I guess my next question would be, how do I set Linux to work with the generic graphics driver…? - as a potential work around…


 Thanks in advanced.

---

