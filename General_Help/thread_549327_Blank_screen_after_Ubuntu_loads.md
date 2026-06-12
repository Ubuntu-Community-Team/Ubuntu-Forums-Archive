---
title: "Blank screen after Ubuntu loads"
date: 2007-09-12
forum: General Help
---

### Post by dracojames on 2007-09-12
Hey, I'm new to the forums, but I'm starting a class in which we're going to be using Unix and Linux based computers and do some programming, so I figured I might as well install Linux on my home computer.

After finding Wubi I installed it, and when I rebooted I got the boot screen.  After making sure my windows install still worked, I rebooted again, this time into Ubuntu.  It finished its install, then rebooted again, and now when I choose Ubuntu at the boot selection screen, I get the Ubuntu loading screen (the Ubuntu logo with the load bar below it), but as soon as it finishes loading, my screen goes completely blank, and the hard drive indicator doesn't seem to light up at all.  If I press my power button, the hard drive light flickers and it takes a few seconds before it shuts down (sounds like its going through a controlled shut down to me), which makes me think Ubuntu's running, but the display isn't working.

Does anyone have any ideas as to what might cause this?  I'm running Vista as my original Windows Install, on a Dell Inspiron laptop, in case that info helps.

Thanks,
-James

---

### Post by ajgreeny on 2007-09-12
Do you see a blinking cursor or absolutely nothing?  Perhaps if nothing your graphic card needs a different driver.  What card is in the machine?

---

### Post by tuxcantfly on 2007-09-12
> **dracojames said:**
> Hey, I'm new to the forums, but I'm starting a class in which we're going to be using Unix and Linux based computers and do some programming, so I figured I might as well install Linux on my home computer.

After finding Wubi I installed it, and when I rebooted I got the boot screen.  After making sure my windows install still worked, I rebooted again, this time into Ubuntu.  It finished its install, then rebooted again, and now when I choose Ubuntu at the boot selection screen, I get the Ubuntu loading screen (the Ubuntu logo with the load bar below it), but as soon as it finishes loading, my screen goes completely blank, and the hard drive indicator doesn't seem to light up at all.  If I press my power button, the hard drive light flickers and it takes a few seconds before it shuts down (sounds like its going through a controlled shut down to me), which makes me think Ubuntu's running, but the display isn't working.

Does anyone have any ideas as to what might cause this?  I'm running Vista as my original Windows Install, on a Dell Inspiron laptop, in case that info helps.

Thanks,
-James

You'll need to install the graphics drivers for your card.

If you're using an ATI card:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

If you're using an Nvidia card:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

If you're using an Intel card:

[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

---

### Post by dracojames on 2007-09-12
Thanks for the quick responses.

To answer your questions, there's no cursor; the screen is completely black.  Also, there's an NVIDIA GeForce 8400M GS in the laptop, which is unfortunately not on the list of supported cards on the Binary Driver How To NVIDIA page.  Does this mean I'm out of luck until a driver is released?

Thanks,
-James

---

### Post by lvleph on 2007-11-18
How does one install the graphics drivers, if all one sees is a blank screen?

---

### Post by ago on 2007-11-19
Ctl + Alt + F2

---

### Post by lvleph on 2007-11-19
I guess mine is not the video drivers. I didn't notice that it didn't start loading drivers. Mine hung in the very beginning. I pressed ctrl+alt+f1 on accident and it started loading everything. Not sure what that means. 

Forgive me for not knowing what things are called, but...
When I select Ubuntu from my boot menu it begins loading. I see the splash screen with the process bar. Then the screen goes blank when I normally would see drivers loading. Once, I pressed ctrl+alt+f1 things load just fine, but it seems obvious that I terminated something, but am not sure what. So far what I have seen that doesn't work when everything has loaded is my Wifi. I try to connect and everything locks up. I have to hold the power button down to shut things down. Also, my num lock and caps lock lights begin flashing when it is locked. 

Let me know any information that is needed to make this diagnosis easier. If I should post in a different thread let me know.

---

### Post by antimatter15 on 2007-11-19
> **lvleph said:**
> I guess mine is not the video drivers. I didn't notice that it didn't start loading drivers. Mine hung in the very beginning. I pressed ctrl+alt+f1 on accident and it started loading everything. Not sure what that means. 

Forgive me for not knowing what things are called, but...
When I select Ubuntu from my boot menu it begins loading. I see the splash screen with the process bar. Then the screen goes blank when I normally would see drivers loading. Once, I pressed ctrl+alt+f1 things load just fine, but it seems obvious that I terminated something, but am not sure what. So far what I have seen that doesn't work when everything has loaded is my Wifi. I try to connect and everything locks up. I have to hold the power button down to shut things down. Also, my num lock and caps lock lights begin flashing when it is locked. 

Let me know any information that is needed to make this diagnosis easier. If I should post in a different thread let me know.
I believe that's a usplash issue. Go to /boot/grub/menu.lst and take out all refrences to "splash"

---

### Post by anon2243 on 2007-11-19
i believe editing usplash.conf and changing the parameters to 1024x768 
then running mkinitramfs -o /boot/initrd.img-`uname -r`

can make the boot screen show up again

this happened to me

---

### Post by Ederico on 2008-02-06
I have a similar problem, when I select Ubuntu from the GRUB menu I get the Ubuntu logo and the progress bar and then nothing else but a blank screen.

---

### Post by ago on 2008-02-06
See [http://ubuntuforums.org/showthread.php?t=685926](http://ubuntuforums.org/showthread.php?t=685926)

---

### Post by BURNINGRANGER on 2008-02-07
Same here, except I restarted when the first blank screen occured. The next attempt it did, for some reason, boot up with the correct resolution and refresh rate, but the default account wasn't present on the machine and was instead replaced by one named 'ubuntu'. Further attempts at rebooting yielded the blank screen again. I'm going to go attempt a reinstall and see if the problem crops up again.

Meanwhile, some of my WinXP icons lost their transparency after installing Wubi:
[img]http://i32.tinypic.com/2wob1uc.png[/img]

But only some of them, as you can see. A System Restore did nothing to fix this.

---

### Post by ago on 2008-02-09
Try chckdsk /r from windows

---

