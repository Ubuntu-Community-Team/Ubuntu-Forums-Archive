---
title: "HELP!! Changed Motherboard- Won't Boot"
date: 2007-05-10
forum: General Help
---

### Post by CheeseQueen452 on 2007-05-10
I'm attempting to upgrade my hardware from an intel P3 1 ghz to an intel P4 2.8 ghz. After changing the motherboard, I get an error that my grahical interface is not properly set up & X Server won't start. Please help ASAP!!!

---

### Post by CheeseQueen452 on 2007-05-10
Anyone?

---

### Post by CheeseQueen452 on 2007-05-10
Can someone please help?

---

### Post by CheeseQueen452 on 2007-05-10
Help!!!!

---

### Post by Xeor on 2007-05-10
Wich version of ubuntu have you got?

You can try "xf86config" to reconfigure your X.

---

### Post by CheeseQueen452 on 2007-05-10
I have Feisty.

> **Xeor said:**
> Wich version of ubuntu have you got?

You can try "xf86config" to reconfigure your X.

---

### Post by Xeor on 2007-05-10
You will have re-configure your "/etc/X11/Xorg.conf" file (sudo gedit /etc/X11/Xorg.conf)

First do a backup of it. (sudo cp /etc/X11/Xorg.conf /etc/X11/Xorg.conf.backup)

---

### Post by Xeor on 2007-05-10
Obviously you are using an onboard graphic card and the driver isn't the same than before. By changing your motherboard, you changed the graphic card.

---

### Post by CheeseQueen452 on 2007-05-10
How can I do that if it doesn't boot?

> **Xeor said:**
> You will have re-configure your "/etc/X11/Xorg.conf" file (sudo gedit /etc/X11/Xorg.conf)

First do a backup of it. (sudo cp /etc/X11/Xorg.conf /etc/X11/Xorg.conf.backup)

---

### Post by Xeor on 2007-05-10
you can try this to reconfig your system in text mode:
# sudo dpkg-reconfigure xserver-xorg

---

### Post by Xeor on 2007-05-10
Yep, I assumed you were falling back on the text mode after the error message.

If you have the cd you could maybe try and choose the option repair your system.

---

### Post by CheeseQueen452 on 2007-05-10
There's no on-board graphic card.

> **Xeor said:**
> Obviously you are using an onboard graphic card and the driver isn't the same than before. By changing your motherboard, you changed the graphic card.

---

### Post by CheeseQueen452 on 2007-05-10
I don't have the CD.

> **Xeor said:**
> Yep, I assumed you were falling back on the text mode after the error message.

If you have the cd you could maybe try and choose the option repair your system.

---

### Post by DoktorSeven on 2007-05-10
To do any of the previously mentioned methods you either have to boot into safe mode (from the GRUB menu when you boot) or just hit CTRL+ALT + F1 or F2 (one of the first few function keys) to get to a textmode login.

the sudo dpkg-reconfigure xserver-xorg Xeor mentioned should be the most reliable method.  When it's done, reboot into normal mode.

---

### Post by CheeseQueen452 on 2007-05-10
Where/when exactly do I type that command?

> **Xeor said:**
> you can try this to reconfig your system in text mode:
# sudo dpkg-reconfigure xserver-xorg

---

### Post by Xeor on 2007-05-10
Do you reach up to the Grub menu and are you able to choose the recovery mode for exemple?

---

### Post by CheeseQueen452 on 2007-05-10
Ok, so when I type that command, what next? Will it do the job on its own?

> **DoktorSeven said:**
> To do any of the previously mentioned methods you either have to boot into safe mode (from the GRUB menu when you boot) or just hit CTRL+ALT + F1 or F2 (one of the first few function keys) to get to a textmode login.

the sudo dpkg-reconfigure xserver-xorg Xeor mentioned should be the most reliable method.  When it's done, reboot into normal mode.

---

### Post by Xeor on 2007-05-10
No, it won't make the work for you; you will need to find out more about your system in order to choose the right options. If you haven't the manuals of your motherboard you can easily find one one the web.

---

### Post by CheeseQueen452 on 2007-05-11
Ok, I followed the instructions I was given, & I got my new system working :) A lot of hardware changes had to be made, but it works better with the 2.8ghz processor & 1gb of memory :D

---

### Post by steve_k on 2007-05-17
> **Xeor said:**
> you can try this to reconfig your system in text mode:
# sudo dpkg-reconfigure xserver-xorg

If you're having to do this before being able to get into a Terminal (ie. the splash screen errors and you're left with an almost blank screen*) you should use **nano **instead of sudo, eg:

# nano dpkg-reconfigure xserver-xorg

I've had this problem on a number of occasions when I've mucked up my nVidia drivers/settings. Last time it happened I was frantically typing sudo and tearing my hair out wondering why it wouldn't work!

*Apologies for the lack of technical jargon, but I still class myself as a newbie. ;)

---

