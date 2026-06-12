---
title: "Help - Installing 12.04, need low graphics mode"
date: 2013-01-02
forum: General Help
---

### Post by Quarkrad on 2013-01-02
I've just bought a new PC that has a gigabyte ga-h61m-s2pv motherboard.  It is an intel core i3 machine with a H61 chipset. Although I'm 99.9% ubuntu I first install win7 so I have two OSs.  When I come to install 12.04 the graphics is really bad - I can recognise some of the install screens, including choosing the partition I have set aside for 12.04 but it is impossible to continue the process.  My hope is if ..........  I can get 12.04 installed I can choose the additional drivers feature and install the appropriate driver.  But ... so far not much luck with the install because of the bad graphics 'out of the box'.  Is it possibe to go through the install process in some sort of low graphics mode so at least I could see what I'm doing rather than guessing?

---

### Post by grahammechanical on 2013-01-02
You can try this.

1) At the first purple screen press enter.
2) select language. English is the default so you may press Enter.
3) Press F6 and scroll down and highlight nomodeset. Press Enter.
4) Press Esc to get back to the TRY - INSTALL screen.
5) Go from there.

Regards.

---

### Post by Quarkrad on 2013-01-02
Graham - that did it.  Very much appreciated.

---

### Post by Quarkrad on 2013-01-02
Spoke too soon!  The graphics were good and I managed to install. However, when I boot - towards the end of the boot process the screen goes blank for about 1 sec, the mauve ubuntu screen appears and then they toggle on and off.  If I start in recovery mode and choose S**tart in failsafe graphics** I get a window that says **The system is running in low-graphics mode** with a OK box in the lower left corner for me to click on.  But at this stage my mouse and keyboard are not working.  I've tried both usb and direct connect mouse but everything seems locked up.  Can I do everything by going to the root command prompt?

---

### Post by Quarkrad on 2013-01-02
I think I've solved it - recovery mode, repair broken packages.  I'll come back if it all install/updates correctly.

---

### Post by Quarkrad on 2013-01-03
No I didn't!!!  Yesterday I managed to get to the desktop, do a sudo apt-get update and a sudo apt-get install ubuntu-restricted-extras.  This morning two things have happened.

After grub screen mauve screen and then eventually the words ubuntu appears and the dots underneath but they are not flashing just static.  After about 3 minutes the screen toggles off(black)/on in 2 sec cycles untill eventually I get a black screen and a window (I guess from my monitor) saying no signal.

The other thing is similar to above but after the initial toggling I get the light ubuntu screen (but no icons/text/bars) and this toggles on/off and eventually gives up to a black screen.

Looks to me ubuntu is still struggling with the graphics chip.

Could it be bios setting?

---

### Post by Quarkrad on 2013-01-03
I guess this is sort of solved.  I needed to get this machine up and running so I installed 12.10 and it looks to be very happy - 'out of the box'.  I prefer the long releases but at least I have a working PC.

---

### Post by cwsnyder on 2013-01-03
At the GRUB menu, press E to edit the GRUB entry.  Edit the line which starts with 'vmlinuz'.  Replace the **quiet splash** with **nomodeset**. This should take you into Ubuntu desktop.

Ubuntu-restricted-extras does NOT install the proprietary graphics drivers for your graphics card.  Go into the Ubuntu Software Center and install the correct drivers for your graphics card, then reboot.

If it goes in the bucket again, use the same method outlined in the first paragraph until you can get a suitable graphics driver, or edit (as root) /etc/default/grub to change the entry which has the quiet splash options to nomodeset and then do a sudo update-grub.

---

