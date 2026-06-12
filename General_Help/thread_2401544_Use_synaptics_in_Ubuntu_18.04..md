---
title: "Use synaptics in Ubuntu 18.04."
date: 2018-09-19
forum: General Help
---

### Post by Akegata on 2018-09-19
I just upgraded my laptop from 16.04 to 18.04. With this upgrade, synaptics stopped working.
I have tried removing xserver-xorg-input-libinput, reinstalling xserver-xorg-input-synaptics and fiddling around with conf files in /etc/X11/xorg.conf.d/ and /usr/share/X11/xorg.conf.d/ but nothing works.

The synaptics drivers are not being loaded, leading "synclient" to give the error "Couldn't find synaptics properties. No synaptics driver loaded?".
How do I solve this issue? I would prefer to not have to use libinput since my synaptics setup was working perfectly before the upgrade.

---

### Post by &amp;KyT$0P# on 2018-09-19
What desktop environment are you using?

---

### Post by Akegata on 2018-09-19
i3

---

### Post by cmcanulty on 2018-09-19
are you trying synaptic from a shortcut? My shortcuts needed tweaking as now shortcuts use synaptic-pkexec instead of sudo or gksudo synaptic

---

### Post by Akegata on 2018-09-19
I'm not talking about the synaptic package manager, but the synaptics input driver. :)

---

### Post by mc4man on 2018-09-19
Don't use i3 here in 18.04 (using unity/compiz) but synaptics is working.
Maybe try installing lightdm & switch to it over gdm3.

---

### Post by Akegata on 2018-09-19
Like I said, I'm not talking about synaptic, I'm talking about synaptics.

---

### Post by mc4man on 2018-09-20
> **Akegata said:**
> Like I said, I'm not talking about synaptic, I'm talking about synaptics.
That's what I'm referring to...

~$ synclient -l
Parameter settings:
    LeftEdge                = 130
    RightEdge               = 3130
    TopEdge                 = 114
    BottomEdge              = 2005
    FingerLow               = 1
    FingerHigh              = 1
    MaxTapTime              = 180
    MaxTapMove              = 171
    MaxDoubleTapTime        = 180
ect, ect.

---

### Post by Akegata on 2018-09-20
What does lightdm/gdm3 have to do with synaptics?
I am however already using lightdm.

---

### Post by Akegata on 2018-09-20
The more I dig into this the more confused I get.
I am able to make libinput take over from the default evdev (by install xserver-xorg-input-libinput). However, I get fewer options for my touchpad than I do if I boot a live Ubuntu 18.04 USB on the laptop. For instance, I can't change the tap to click option on my local installation, that option doesn't show up at all.

If I uninstall xserver-xorg-input-libinput and install xserver-xorg-input-synaptics the evdev driver takes over handling of the touchpad and keyboard. If I remove /usr/local/X11/xorg.conf.d/10-evdev.conf and reboot neither the touchpad nor the keyboard works, so synaptics is definitely not being used at all.

---

### Post by mc4man on 2018-09-20
I would purge the xserver-xorg-input-evdev package, install both xserver-xorg-input-libinput & xserver-xorg-input-synaptics, 'unfiddle' any other .conf's you messed with, if any  & reboot.
If the driver isn't loading then check /var/log/Xorg.0.log, search out synaptics.
Tried your i3 here, no issue, the driver loads and synclient works fine & fully fleshed out.
 From the Xorg log - 
> 5.469] (II) LoadModule: "synaptics"
[     5.469] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[     5.469] (II) Module synaptics: vendor="X.Org Foundation"
[     5.469] 	compiled for 1.19.3, module version = 1.9.0
[     5.469] 	Module class: X.Org XInput Driver
[     5.469] 	ABI class: X.Org XInput driver, version 24.1

---

### Post by Akegata on 2018-09-22
I've done all of the above, still can't get the synaptics driver to load. I'm currently trying to find out what differs between my normal installation and a persistant USB ubuntu 18.04 USB where synaptics works as expected on the same hardware.
I can't figure out anything that might cause this isssue. I've tried messing around with /usr/share/X11, /etc/X11/xorg.conf.d/, /boot stuff and modprobe configuration. Nothing seems to be relevant to what's blocking synbaptics from being loaded.

---

### Post by Akegata on 2018-09-23
After a lot of troubleshooting I realized that what was happening was that the kernel incorrectly identified the touchpad as a mouse.
I was running kernel 4.15.0-34.37 and noticed that the live USB was running 4.15.0-29-generic.

I wasn't sure how to downgrade to that specific kernel version, but I used ukuu to downgrade to 4.15.0-041500-generic. After this, the touchpad is finally identified correctly and the synaptics drivers are loaded.

---

