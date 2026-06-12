---
title: "Ubuntu 16.04 completely unable to reboot/shut down."
date: 2018-03-12
forum: General Help
---

### Post by Federico_Carta on 2018-03-12
Hi everybody,

I just installed Ubuntu 16.04 LTS on a laptop Lenovo Legion Y520, in parallel with Windows 10.
The installation of the Ubuntu operative system went completely fine until the last step, where (after getting a message of successful install) I was requested to reboot.
At this stage, everything froze. I waited more than 1h and 30 minutes, thinking that it was taking some time, but at the end I realized it was just frozen, so I did some hard power-off, by pressing the power button.

It is definitely not the first time I install Ubuntu on a machine, but it is the first time this happens to me.

After this fact, almost everything works fine. If I turn on the laptop grub lets me decide to start Windows or Ubuntu, as usual.
With Windows, no problem at all occur.

With Ubuntu, everything works fine as well (video, sound, keyboard, installing programs, etc) apart from one important fact:
The operative system is completely unable to shut down or reboot.
If I ask to shut down or reboot (either by clicking to the up-right corner symbol or by typing a command in the terminal) everything freezes and the only solution seems to do a hard power-off.

Does anybody know why this is happening, or how I can fix it?

This is the only problem I find, all the rest seems ok. But nevertheless, not beeing able to reboot seems like a major problem to me.
Any suggestions?

Thank you very much!!

(Apologies if I made mistakes in english. That is not my mother tongue language)

---

### Post by mg2003 on 2018-03-12
I assume you're using the GUI to shut down.  When you shut down from the terminal, does it give a useful error message or alert?

Command:
> sudo shutdown now

---

### Post by Federico_Carta on 2018-03-12
Even with 

```

sudo shutdown now

```

Nothing at all happens. No error message. Just everything freezes.

Any idea about how to deal with this?

---

### Post by oldfred on 2018-03-13
Have you tried REISUB?

 Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key) 
   Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is, and S can be before E, but others should be in order
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274) 


 Lenovo Legion Y520-15I  Installer does not detect SSD and HDD: Ubuntu 16.04 LTS
[https://ubuntuforums.org/showthread.php?t=2359208](https://ubuntuforums.org/showthread.php?t=2359208)

---

### Post by mastablasta on 2018-03-13
you could check the logs to see what is happening (with a log viewer or just browse the /var/log directory)

you can also try to switch to virtual console first (crtl+alt+F1), login, then do the reboot with command. see if that goes through or if it throws any error message.

---

### Post by krakatoacrack on 2018-03-17
> **Federico_Carta said:**
> Hi everybody,

I just installed Ubuntu 16.04 LTS on a laptop Lenovo Legion Y520, in parallel with Windows 10.
The installation of the Ubuntu operative system went completely fine until the last step, where (after getting a message of successful install) I was requested to reboot.
At this stage, everything froze. I waited more than 1h and 30 minutes, thinking that it was taking some time, but at the end I realized it was just frozen, so I did some hard power-off, by pressing the power button.

It is definitely not the first time I install Ubuntu on a machine, but it is the first time this happens to me.

After this fact, almost everything works fine. If I turn on the laptop grub lets me decide to start Windows or Ubuntu, as usual.
With Windows, no problem at all occur.

With Ubuntu, everything works fine as well (video, sound, keyboard, installing programs, etc) apart from one important fact:
The operative system is completely unable to shut down or reboot.
If I ask to shut down or reboot (either by clicking to the up-right corner symbol or by typing a command in the terminal) everything freezes and the only solution seems to do a hard power-off.

Does anybody know why this is happening, or how I can fix it?

This is the only problem I find, all the rest seems ok. But nevertheless, not beeing able to reboot seems like a major problem to me.
Any suggestions?

Thank you very much!!

(Apologies if I made mistakes in english. That is not my mother tongue language)

Hello Federico: 

I found your post after typing my exact same problem, LEGION Y520 new machine on Windows 10 and New installation of Ubuntu 16.04 LTS. I went through many solutions provided in this and other forums, for example editing grub, and many others. I am sorry I am not an advanced user of UBUNTU but have done many installations since many years ago and work regularly in UBUNTU. The solution that worked for me was changing the driver used for the NVIDIA GEFORCE GTX GRAPHIC CARD that comes with this laptop. If you go to Software and Updates, under Additional Drivers, You will see the NVIDIA binary driver and the X.org Xserver Nouveau open Source Driver. If you installed using third party drivers, it is probably that you will have de Open Source Noveau driver activated. I just changed from the Nouveau to the propietary NVIDIA driver to have the computer powering off correctly

HOWEVER, there is a catch, when I clicked for the change of driver, it required my password, and then it just kind of stood there for several minutes. After waiting a few minutes and I didn't see any change happening I closed the window, When I opened the window again, the Driver was again the Open Source Noveau. 

Problem is that when you click to change the driver the progress bar doesn't move and there is no sign of anything happening, After 10 minutes or so (perhaps because of slow internet connection) the progress bar moved and the after 15 minutes the change ocurred AND CONFIRMED to the NVIDIA proprietary driver. Then it all worked fine. From there. I hope this can fix your problem also. 

Saludos, 

K

---

