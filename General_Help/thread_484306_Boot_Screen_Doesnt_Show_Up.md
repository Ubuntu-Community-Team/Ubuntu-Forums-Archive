---
title: "Boot Screen Doesnt Show Up"
date: 2007-06-25
forum: General Help
---

### Post by sidprak on 2007-06-25
Hey every1
I have a problem with the ubuntu boot screen.  When i put the install cd into the drive, boot from it and press enter on the first option (Start or Install Ubuntu), the boot screen is blank, it is just a black screen for a while until it loads.  Even after I install it, the boot screen is still blank.  My specs are:

Intel Pentium 4 1.8
512 RAM
Intel 845 Integrated Graphics

---

### Post by jimbob on 2007-06-25
After you installed it will it boot OK after the blank screen shows up for a while?

What is the first thing you see after it comes out of the blank screen?
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by rklauco on 2007-06-25
Try to run the installer in safe mode graphics - the second option in the live CD.
This should give you text-only startup and then nice old Gnome with full graphics (don't worry, only the startup is in text...).
After the installation it will be ok - I had the same case on old IBM laptop and on a strange ATI card (some Radeon 9250SE or sth like that).

---

### Post by sidprak on 2007-06-25
> **jimbob said:**
> After you installed it will it boot OK after the blank screen shows up for a while?

What is the first thing you see after it comes out of the blank screen?
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

After the blank screen show up for a while, it shows a little bit of text and then goes back to the blank screen. Then, it goes to the login screen.

After that, it just boots normally.

---

### Post by rklauco on 2007-06-25
Seems like your system does not work with pre-defined resolutions for the start up screen.
Check 
[https://help.ubuntu.com/community/USplashCustomizationHowto](https://help.ubuntu.com/community/USplashCustomizationHowto)
Especialy point 6 with the grub settings - try different resolutions. Should help.

---

### Post by sidprak on 2007-06-25
> **rklauco said:**
> Seems like your system does not work with pre-defined resolutions for the start up screen.
Check 
[https://help.ubuntu.com/community/USplashCustomizationHowto](https://help.ubuntu.com/community/USplashCustomizationHowto)
Especialy point 6 with the grub settings - try different resolutions. Should help.

I tried all of the resolutions, with no luck!! Any other suggestions??

---

### Post by strabes on 2007-06-25
sudo aptitude install usplash-theme-ubuntu

---

### Post by sidprak on 2007-06-25
> **strabes said:**
> sudo aptitude install usplash-theme-ubuntu

still showing the black screen

when i installed, it said 0B were downloaded and 0B will be installed

---

### Post by sidprak on 2007-06-25
> **sidprak said:**
> I tried all of the resolutions, with no luck!! Any other suggestions??

It says, you have not defined a valid resolution code on all of the resolutions.  Then it gives me options to try other resolutions like 80x25, etc. or scan.

---

### Post by proplaya23 on 2007-06-26
> **sidprak said:**
> It says, you have not defined a valid resolution code on all of the resolutions.  Then it gives me options to try other resolutions like 80x25, etc. or scan.

i have a similar problem when i was installing ubuntu from Livecd i had to Press F4 to choose my resolution to 1024x768 so i can atleast see whats going on and it installed fine. But after the resart and attempt to reboot back into ubuntu iget the blank screen again with monitor light turning from green to orange.... is there anyway to change res from boot line?????

---

### Post by sidprak on 2007-06-26
> **proplaya23 said:**
> i have a similar problem when i was installing ubuntu from Livecd i had to Press F4 to choose my resolution to 1024x768 so i can atleast see whats going on and it installed fine. But after the resart and attempt to reboot back into ubuntu iget the blank screen again with monitor light turning from green to orange.... is there anyway to change res from boot line?????

when i press F4 after booting from my live cd there are only two options:
VGA and 640x480

---

### Post by SpamBadger on 2008-03-31
I have a similar problem, only if i plug in a secondary moitor, the graphic shows up on the second monitor, but not the laptop LCD.  

IBM T30
ATI 7500 mobility

---

