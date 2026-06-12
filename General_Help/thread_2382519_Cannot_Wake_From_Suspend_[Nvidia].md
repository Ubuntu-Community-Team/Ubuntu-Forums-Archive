---
title: "Cannot Wake From Suspend [Nvidia]"
date: 2018-01-14
forum: General Help
---

### Post by mydroog on 2018-01-14
*SOLVED, SEE LAST POST FOR DETAILS*

Hey everyone,

My computer is unable to to wake from suspend. I believe this may have something to do with Nvidia drivers, as I am using proprietary drivers v384.11.

This driver powers 2 graphics cards, 2 x GTX660 in SLI mode. I previously had two monitors hooked up to the first card, and one to the second. I have since hooked up all 3 monitors to the first card, to make things easier (as well as I have heard Linux doesn't like dual cards). This changed nothing.

My issue is that the system is unable to wake from suspend. What happens is that it comes out of hibernation successfully, and goes to the login screen. Everything seems correct at the login screen, all 3 monitors turn on, everything is positioned correctly, and so forth. However, when I enter my password and do login, the system completely stops functioning. It is completely unresponsive (the keyboard too cannot send any outputs, for example my caps lock on/off LED doesn't trigger), the only option is a reboot every time.

Recently, I think after I made some change, I get an error message before even getting to the login screen. When the computer is taken out of hibernate, I don't even get to the login screen. 2 of 3 monitors turn on, and display the messages

```
[ 140.054924 ] NVRM: Xid (PCI:0000:01:00): 61, 1927(16e4) 00000000 000000

  [ 140.0560721] NVRM: Xid (PCI:0000:01:00): 61, 1927(16e4) 00000000 00000


```


I've been keeping a log of things I've tried to do to fix this issue, as it is huge for me. It is the biggest barrier to going linux-only as I can never let the computer go to hibernate, and end up doing dozens of on/off cycles per day.

```
1) Added to the section in Xorg.conf for "device"

Section "Device"
    Identifier     "my id"
    Driver         "my dr"
    VendorName     "my vendor"
    BoardName      "my board name"
    Option         "NvAGP" "1"
EndSection

Specifically "Option" NvAGP was added. Supposed to alleviate susepnsion issues.

DID NOT WORK - REMOVED THIS OPTION

2) Blacklist the intel_agp module 

sudo nano /etc/modprobe.d/blacklist.conf

I added the line "blacklist intel_agp" to the bottom (with commentary so you can find it again to remove).

Did not work -> commented this line out using #

3)Following lines added to blacklist.conf

blacklist nouveau
blacklist lbm-nouveau
options nouveau modeset=0
alias nouveau off
alias lbm-nouveau off

Also disabled kernel nouveau using the command:
"echo options nouveau modeset=0 | sudo tee -a /etc/modprobe.d/nouveau-kms.conf"

and rebuilt kernel using "sudo update-initramsfs -u"

DID NOT WORK
```

---

### Post by pqwoerituytrueiwoq on 2018-01-15
have any custom boot options?
```
/etc/default/grub
```

this is what i use:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1280x800-24,mtrr=3,scroll=ywrap"

sudo update-grub
``` will apply changes

i use xscreensaver not lightlocker, it could be a lightlocker issue

---

### Post by mydroog on 2018-01-15
> **pqwoerituytrueiwoq said:**
> have any custom boot options?
```
/etc/default/grub
```

this is what i use:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1280x800-24,mtrr=3,scroll=ywrap"

sudo update-grub
``` will apply changes

i use xscreensaver not lightlocker, it could be a lightlocker issue

Here is my current grub code in the folder you specified. Also, I'm not sure what this line you added in does exactly. Would that work fine on a multi-monitor setup?

Additionally, I have noticed that even if I lock the computer, when I log back in, all my monitors go blank. Perhaps you are correct that it may be an issue with the locker.

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

---

### Post by mydroog on 2018-01-15
The mystery deepens..

I tried using "sudo pm-hibernate". I realized that I don't need hibernate, but suspend, but I wanted to try it anyway. GRUB screen loaded up, I selected by xubuntu distro (I also have Win10 on a different drive).

Then the screen went blank, and I had 2/3 monitors displaying the following:

```
[   975.622178] RTNL: assertion failed at /build/linux-hwe-UY0ygs/linux-hwe-4.13.0/net/core/dev.c (2356)
[   975.622224] RTNL: assertion failed at /build/linux-hwe-UY0ygs/linux-hwe-4.13.0/net/core/dev.c (2398)
```

Followed by the same two codes I had before when I would wake from suspend

```
[   975.844436] NVRM: Xid (PCI:0000:01:00): 61, 1927(16e4) 00000000 00000000
[   975.850605] NVRM: Xid (PCI:0000:01:00): 61, 1927(16e4) 00000000 00000000
```

Another interesting thing was that when I did sudo pm-suspend, I was semi-succesfully able to wake from suspend for the first time. Waking from suspend bypassed the lockscreen and jumped straight to my desktop. All 3 monitors were on and fully functioning. I could even move my mouse around. However everything else in the system was completely unresponsive, keyboard was unresponsive, I couldn't click anything, and after 10-15 seconds the mouse disappeared too. 

Such a crazy problem, but one that must be solved. I really don't want to have to move from Xubuntu, but being unable to suspend at least, is a deal breaker

---

### Post by pqwoerituytrueiwoq on 2018-01-17
does it work if you completely disable lightlocker
when it wakes it should be on your desktop not a login screen

---

### Post by mydroog on 2018-01-17
> **pqwoerituytrueiwoq said:**
> does it work if you completely disable lightlocker
when it wakes it should be on your desktop not a login screen

I'm trying to pursue this avenue now. I fully uninstalled Lightlocker and installed gnome screensaver, but still have the same result. The new login screen comes up, and the system stops functioning entirely. I can attempt to go without a locker to see if that works, in that case would just uninstalling gnome-screensaver do the trick?

---

### Post by mydroog on 2018-01-18
> **pqwoerituytrueiwoq said:**
> does it work if you completely disable lightlocker
when it wakes it should be on your desktop not a login screen

So I just attempted this.

Same issue. It wakes from hibernate straight to the desktop, where the system immediately freezes and stops accepting all input.

---

### Post by pqwoerituytrueiwoq on 2018-01-19
have you tried booting with [FONT=courier new]nomodeset[/FONT]?
What PSU are you using, maybe the sudden power draw from the dual GPU is causing a momentary Vdrop causing a crash; can you reproduce with any other OSes?

My mom's system has a similar issue AMD Phenom II 965 + GT 430, some times when it enters sleep mode it locks up in sleep mode before the fans turn off; at one point it would fail to wake in this state; it also had issues of waking randomly; eg opening a closet door would trigger it

---

### Post by mydroog on 2018-01-19
> **pqwoerituytrueiwoq said:**
> have you tried booting with [FONT=courier new]nomodeset[/FONT]?
What PSU are you using, maybe the sudden power draw from the dual GPU is causing a momentary Vdrop causing a crash; can you reproduce with any other OSes?

My mom's system has a similar issue AMD Phenom II 965 + GT 430, some times when it enters sleep mode it locks up in sleep mode before the fans turn off; at one point it would fail to wake in this state; it also had issues of waking randomly; eg opening a closet door would trigger it

I will try the nomodeset, I haven't heard of this fix before, so I'll do some research and try it out.

The issue cannot be reproduced in Windows 10. I can't remember the exact brand of PSU, but when I built the system, dual GPUs were taken into account. I'm running a (true) 800W PSU or so, powering two Nvidia GTX660s and a Phenom II X3 720 (old, lowly CPU. Hopefully will have the money to upgrade the system soon). I've done extensive stress testing in Windows 10, heavy gaming using dual GPUs, never had a problem.

Edit:  Apparently I already tried booting with nomodeset. No change.

---

### Post by pqwoerituytrueiwoq on 2018-01-19
does this only happen with one gpu installed?
i assuming you are using the nvidia 384 or 387 driver?
i have a 650 ti boost and the only issue i have with waking from sleep occurs if my tv is off and the system starts outputting to vga instead of hdmi
xubuntu 14.04 nvidia 384

---

### Post by mydroog on 2018-01-20
Hey everyone!

Good news, I found a solution. I have tried COUNTLESS solutions online, literally everything I could find. I decided to purge and re-install the nvidia drivers. Upon installing the latest drivers, I would slowly reconfigure my 3 monitors to find out where the issue was. Then I finally found it. Ive' suspected it was some weird issue with the Nvidia drivers, And I was correct.

It's Base Mosaic.

Previously, I was only able to set my monitors up correctly with base mosaic enabled. However, for some reason, it makes the computer unable to properly wake from suspend.

IF YOU ARE SUFFERING FROM THIS ISSUE, TRY THIS:

Enable base mosaic, and configure your monitor setup. Save the xorg.conf file. Then disable base mosaic in Nvidia settings, hopefully your monitor layout will remain unchanged, and you can save the configuration. If it changes your monitor layout, you can always disable base mosaic manually in the xorg.conf file without affecting your monitor layout. 

Sudo nano /etc/X11/xorg.conf
Then where base mosaic is located, change it to "off"

Boom. I can hibernate now.

---

