---
title: "First Time Ubuntu Needs Help"
date: 2008-01-29
forum: General Help
---

### Post by dominator24 on 2008-01-29
Hi i am a regular Windows user - and i thought id give ubuntu a try - and i cant get it to work properly yet never mind look around it.

i have a daewoo 19" widescreen model NO - HL920WA

HIS HD2600XT - Graphics card

My Resolution is stuck on 800 X 600 - as my monitor model does not show - also when i chose a standard 1440 - 900 LCD my picture goes all funny. and still stays at 800 X 600

My graphics card does not show - i see RADEON i click it and the colour goes funny.

I have installed all updates and the restricted drivers it says

ATI ACCELERATED GRAPHICS DRIVER - I have enabled it.

Everything Worked Fine On The LIVE CD - But Not When I Have Installed It

--------------------

I have also downloaded the ATI driver for linux fle name - ati-driver-installer-8-01-x86.x86_64

This File Will Not Run - Says -

gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

Please Help - I Want To Like This OS

Thanks

I AM USING UBUNTU 7.10

---

### Post by dominator24 on 2008-01-29
Anything Anyone? Please Im Sat Here Looking At Ubuntu Dont Know What To Do

---

### Post by UltraAnders on 2008-03-14
Did you ever find a solution to this? I also have this monitor.

I've enabling the Nvidia drivers in System -> Administration -> Restricted Drivers Managers, but under Screen and Graphics the highest refresh rates offered are in the fifties, e.g. 55Hz at 1152x864.
--edit--
:) I found the answer while searching how to enable dual display (Nvidia graphics card).

Before fiddling, I backed up xorg.conf using this command:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```
Then I followed [these]("http://ubuntuforums.org/showthread.php?p=1773584") instructions.

It's unlikely I'm sure, but please don't confuse me with someone who's knows what they are doing with Linux! ;)

---

