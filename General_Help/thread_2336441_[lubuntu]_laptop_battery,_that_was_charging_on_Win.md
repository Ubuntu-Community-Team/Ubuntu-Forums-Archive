---
title: "[lubuntu] laptop battery, that was charging on Win7, is not charging on Lubuntu"
date: 2016-09-08
forum: General Help
---

### Post by den4ik1996 on 2016-09-08
Hi guys.

I've got a problem and I need your help.

So, I am running Ubuntu on my PC and I really like it, so I decided to switch my laptop from Win7 to Ubuntu too. I found out that battery wasn't charging anymore. Also, system worked a bit slow, so I decided to go with Lubuntu. And I really like it, it is fast and lightweight, and everything but the battery is working just fine. The battery icon says it is charging, but it is stuck at 0%. The funny thing is that even when the laptop is switched off and is charging (the flash light is on - orange light), it doesn't work if the AC cord is not plugged in. And I can't go back to Win7 cause now Lubuntu 16.04 is the only OS installed on my laptop.[COLOR=#000000]
[/COLOR]
Here is more info about my laptop:

[COLOR=#000000]1. Laptop - COMPAQ Presario CQ57[/COLOR]
[COLOR=#000000]2. Processor - 2x Intel(R) Celeron (R) CPU B815 @ 1.60GHz[/COLOR]
[COLOR=#000000]3. Memory - 2 GB[/COLOR]
[COLOR=#000000]4. Video card description: VGA compatible controller product: 2nd Generation Core Processor Family Integrated Graphics Controller[/COLOR]
[COLOR=#000000]vendor: Intel Corporation[/COLOR]
[COLOR=#000000]physical id: 2[/COLOR]
[COLOR=#000000]bus info: pci@0000:00:02.0[/COLOR]
[COLOR=#000000]version: 09[/COLOR]
[COLOR=#000000]width: 64 bits[/COLOR]
[COLOR=#000000]clock: 33MHz[/COLOR]
[COLOR=#000000]5. Wifi card- AR9485 Wireless Network Adapte


Any ideas how I can make my battery charge?[/COLOR]

---

### Post by den4ik1996 on 2016-09-08
Doesn't anyone know? :cc
It is really important.. I need my laptop for my studies in the uni...

---

### Post by #&amp;thj^% on 2016-09-08
This has worked on Lenovo and Hp Laptops but your mileage may vary.
Try to fully discharge the battery by playing Videos or Music til it dies...Then manually remove the battery and plug-in the cord and reinstall the battery and power on the Laptop.
Make sure you have what you need **backed-up before proceeding. **
If all goes well it should now show as charging.

---

### Post by den4ik1996 on 2016-09-08
The thing is that it is stuck at 0%, so it dies right after i take the cord out. Then I did what you said, it didn't help.

Any other suggestions?

---

### Post by den4ik1996 on 2016-09-08
upower -d result. what do you think?
Device: /org/freedesktop/UPower/devices/line_power_AC
  native-path:          AC
  power supply:         yes
  updated:              Thu 08 Sep 2016 20:58:33 BST (880 seconds ago)
  has history:          no
  has statistics:       no
  line-power
    warning-level:       none
    online:              yes
    icon-name:          'ac-adapter-symbolic'


Device: /org/freedesktop/UPower/devices/battery_BAT0
  native-path:          BAT0
  vendor:               HP
  power supply:         yes
  updated:              Thu 08 Sep 2016 21:12:38 BST (35 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               charging
    warning-level:       none
    energy:              0 Wh
    energy-empty:        0 Wh
    energy-full:         0 Wh
    energy-full-design:  0 Wh
    energy-rate:         0 W
    percentage:          0%
    capacity:            100%
    technology:          lithium-ion
    icon-name:          'battery-caution-charging-symbolic'


Device: /org/freedesktop/UPower/devices/DisplayDevice
  power supply:         yes
  updated:              Thu 08 Sep 2016 20:58:34 BST (879 seconds ago)
  has history:          no
  has statistics:       no
  battery
    present:             yes
    state:               charging
    warning-level:       none
    energy:              0 Wh
    energy-full:         0 Wh
    energy-rate:         0 W
    percentage:          0%
    icon-name:          'battery-caution-charging-symbolic'


Daemon:
  daemon-version:  0.99.4
  on-battery:      no
  lid-is-closed:   no
  lid-is-present:  yes
  critical-action: HybridSleep

---

### Post by #&amp;thj^% on 2016-09-08
Dose it show charging in the panel...upower shows that it is but is it really?.
And just one more trick to try...but first close and save everything opened.
Just hold down the power button 7 seconds until it shuts down, then another 10/20 seconds. The orange battery light may go from blinking to steady orange. See if that fixes it.

---

### Post by den4ik1996 on 2016-09-08
The icon on a panel says it is charging, but the energy level stuck at 0%.

The trick didn't help. The orange battery light was steady orange at all times.

---

### Post by #&amp;thj^% on 2016-09-08
Well time will tell if it is charging or not.
I  suspect its a software issue and that it never occurred in previous versions of Ubuntu, I would boot your computer with a LiveCD of Ubuntu and leave your power-pack plugged in.
If the problem persists this would indicate a hardware issue.

---

### Post by den4ik1996 on 2016-09-08
Well. it has been like this for months now. Cause I have been running Linux for a while now.

---

### Post by QIII on 2016-09-08
Just to be clear:

Does it charge when the machine is turned off?

Does it charge if you are in the BIOS menu?

---

### Post by #&amp;thj^% on 2016-09-08
Well I have been running Linux for over 10 years...and sometimes these things just automagicly fix them selves.
I would try the live CD method (I showed in my above post) to be sure your battery is still good.
They do go bad.
Anyway Good Luck
Ninjed by QIII

---

### Post by den4ik1996 on 2016-09-08
> [COLOR=#000000]1)Does it charge when the machine is turned off?[/COLOR][COLOR=#000000][INDENT]
2)Does it charge if you are in the BIOS menu?[/INDENT]
[/COLOR]

1)No
2)No

> [COLOR=#000000]I would try the live CD method[/COLOR]
Okey

---

### Post by den4ik1996 on 2016-09-09
I run a live Xubuntu session, wasn't charging either.

---

### Post by sudodus on 2016-09-09
When you have tried all the tips in the previous replies, maybe you can these tips:


1. Tru again with Windows.

a. Get or make a Windows Preinstallation Environment, boot from it, and check if the computer is charging. I guess that is the closest you can get to a real installed Windows.

b. If still no go, you can install Windows again. It should not be necessary to do all the updates & upgrades. Juat run the basic Windows system.


2. You can also try some very different linux distro (very distant from Ubuntu both in time and configuration). Try live (without installing) when possible.

a. Maybe some very new (not yet released and with a brand new kernel and brand new hardware drivers) and some very old distro. (If it has passed end of life is no good for regular use, but can be OK for testing, particularly if you remove the internal drive, so there is no data that can be corrupted or stolen.)

b. maybe Fedora, Manjaro, Mageia, openSUSE, Tiny Core, Wary Puppy, Porteus (kiosk).

-o-

If the battery is charging with one of the other systems, we know there is a software issue with Ubuntu and linux distros similar to Ubuntu. Otherwise I think the battery or the system for charging the battery is bad.

I don't know what conclusions to draw from the fact that the computer does not charge the battery when in the BIOS menus or when turned off but connected to the power grid. If ***you***, who are reading this post, know, please tell us :-P

---

### Post by QIII on 2016-09-09
If it is not charging when the machine is turned off or when in the BIOS menu (read: the OS has nothing to do with either of these two states), then my suspicion immediately goes to a battery gone bad or charging circuitry in the device.

---

### Post by motar2 on 2016-09-09
I had a problem very much like you are having but my Laptop is a Acer Aspire, after weeks of searching the web and trying different recommendations what did the trick for my system was to find the battery reset pin hole on the bottom of the laptop, it has a little icon which is hard to see and difficult to figure out what it means but the icon shows what it looks like a rectangular shape which pretends to be animated.    

With the laptop power down and disconnected from the mains, you need to insert a paper-clip through the pinhole and hold it for around 8 to 10 seconds, this resets the battery to a factory pre-set. Don’t power on just yet, it is recommended to wait for around 5 minutes before plugging the machine into the mains and switching it on.  

This cure my battery charging problems, hope it works for you.

---

### Post by den4ik1996 on 2016-09-09
Motar2, I have got a removable battery, so there is no the reset pin hole on my laptop I am aware of.. 

sudodus, I tried to install Fedora, but I got this error:
FATAL: No or empty root+argument
Refusing to continue
System halted

---

### Post by sudodus on 2016-09-09
Did you download a live iso file, like the one at this link: [https://getfedora.org/en/workstation/download/](https://getfedora.org/en/workstation/download/)?

- Was the checksum correct?
- Did you install it into a USB drive or DVD?
- Did the live system boot and work?
- Could you install it?
- Could you boot and run the installed system?

Please indicate where you got this error output! I think it is enough to get the live system running. You need not install it to test if it can charge the battery.

What about the comments in the replies above about charging when the computer is off?

- How long did you try that - only a few minutes, or several hours?
- Was the battery lifetime getting short when you were running Windows?

---

### Post by den4ik1996 on 2016-09-09
Yeah, it was a live iso file.

So, I booted from the USB drive and tried to install it, and got that error. Then I tried to run it live and got the same error again. So, I had to go back to the installed OS I have which is Lubuntu.

And about the battery. I took the battery out for about 5 minutes I think. 

When I had Windows, battery was working for 1.5-2 hours without charging.

---

### Post by sudodus on 2016-09-09
I think that there are three alternatives. I will not try to guess which alternative is most likely.

1. The battery and the 'hardware around it' are still good and would charge and run more than one hour, maybe as long as before, if you boot the computer with Windows.

2. The battery is damaged, and does no longer work.

3. Some hardware in the computer is damaged and can no longer charge the battery.

It is possible, that there is some feature in Windows, that can re-activate the battery. Are you willing and able to re-install Windows (or a preinstallation environment of Windows)? I am far from sure, that the battery will work with Windows, and you have to spend hours to do it, but it will give you an answer, so whatever the result, it might be worth the effort.

---

### Post by den4ik1996 on 2016-09-10
I don't know if I want to spend money on buying Windows when there is no guarantee the battery will work. This laptop is getting old, so I might think about getting the new laptop then..

---

