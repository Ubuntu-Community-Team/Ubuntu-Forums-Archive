---
title: "Ubuntu freezing ! HELP!!!!!"
date: 2007-07-08
forum: General Help
---

### Post by czepluch on 2007-07-08
My Ubuntu is freezing just after i've done my username and password the little jingle plays, the screen becomes orange and the mouse is in the middle of the screen and then... nothing happens ! Please HELP me !! Desperately need help !!!!

---

### Post by Toufik on 2007-07-08
More informations would be nice (instead of yelling) :

Is it a fresh install?
Have you done an upgrade?
Did it work before? or never?
Have you change something?
What kind of compputer do you have?
Do you have a graphic card?
...

In the meanwhille, press CTRL+ALT+F1, you are now in a non graphical (but fully operational) ubuntu. Try to log in there. Does it works?

If you can, could you post some files:
/var/log/Xorg.0.log
/etc/X11/xorg.conf

---

### Post by czepluch on 2007-07-08
> **Toufik said:**
> More informations would be nice (instead of yelling) :

Is it a fresh install?
Have you done an upgrade?
Did it work before? or never?
Have you change something?
What kind of compputer do you have?
Do you have a graphic card?
...

In the meanwhille, press CTRL+ALT+F1, you are now in a non graphical (but fully operational) ubuntu. Try to log in there. Does it works?

If you can, could you post some files:
/var/log/Xorg.0.log
/etc/X11/xorg.conf

The install is a month old. Dont know if i've upgraded at least not the last 4 days. It has worked just perfectly until now. I installed compix fusion yesterday, but i've rebooted a lot of times since that. I've got an Acer travelmate 4060. centrino 1.60 mhz processor, 1272 ram, Intel GMA 915 onboard graphic.

What do you mean by posting some files?

---

### Post by czepluch on 2007-07-08
Bump

---

### Post by ZapperJet on 2007-07-08
Hi,

I'm a top level newbie to Ubuntu. It appears I am having the same problem, and just recently too!

The story:

As I was switching out one video card for another (ATI Radeon 9000 in stead of FX5200) I booted up, went through the Xorg process, and started the X Server.

I made it all the way to the login screen. However, after entering my password and username, I was greeted by a blank Maroon screen with a cursor in the middle.

So.... I went through the process of trying different cards (3dfx cards, voodoo, etc). No avail.

The only changes I made to the OS prior to the problem in question were as follows:

a) uninstalled nvidia drivers and dev packaged via SPM
b) marked ATI Radeon drivers and driver tools for installation
c) marked ATI backlight driver (for laptops, I'm running a desktop) for uninstallation

My Ubuntu system specs:

Intel Pentium Pro 500Mhz CPU
320mb 100mhz SDRAM
ATI Radeon 9000 128mb Video
SoundBlaster Live! 16-bit
10GB Quantum Fireball HDD

(this is a leftover secondary machine, I have a fully operational WinXP machine)

Cheers,
John

---

### Post by ZapperJet on 2007-07-08
Some additional info:

When opening the command console Ubuntu (Ctrl-Alt-F1) I get error messaged for /dev/wacom. I assume it's looking for files for a Wacom Tablet or some specific Wacom firmware. However, since I don't have a Wacom anything this is particularly strange.

The other part of the messages include procedural information for my RADEON video  card. This doesn't seem out of the ordinary and there is nothing that points to any errors. The last line says "OK, Leaving Now...". I'm not sure what that means.

Cheers,
John

---

### Post by czepluch on 2007-07-08
PLease guys? I really need help on thsi one

---

### Post by czepluch on 2007-07-08
I uninstalled compiz but it didn't work the first time i rebooted, so i did the Ctrl+Alt+Backspace when it frooze and now it works again. So thats fine :):) But now i would like to know why it suddenly works ?

---

