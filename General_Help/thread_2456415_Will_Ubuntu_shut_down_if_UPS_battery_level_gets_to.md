---
title: "Will Ubuntu shut down if UPS battery level gets too low?"
date: 2021-01-11
forum: General Help
---

### Post by bullwinkle2 on 2021-01-11
I have my Ubuntu system plugged into an APC Uninterruptible Power Supply and the USB cable is connected, so the battery indicator in the top bar shows the UPS battery percentage.  Great, but what I don't see is anything in the Power settings similar to what you would see on a Mac, that lets you tell the computer to do a power off if the UPS battery gets too low.  Is this something that is even done by default, and if so how do you see or change the battery percentage setting at which the power off initiates?  If not, what is the current recommended way to add that functionality (preferably as additional settings in the Power menu?).

My above question is specifically about the desktop version (running the default Gnome desktop) but as an aside I assume that Ubuntu Server (the one with no desktop) doesn't do any monitoring of a UPS unless you install additional software to do that, correct?

---

### Post by ActionParsnip on 2021-01-11
What is the output of:
```

lsusb; lsb_release -a; uname -a; dmesg | grep -i ups

```
Thanks

---

### Post by grahammechanical on 2021-01-11
This is an old answer to a similar question and I do not know if it is still applicable. We still have deconf Editor installed in Ubuntu and all the settings mentioned in that reply are still there. So, it might be the solution you are looking for.

[https://askubuntu.com/questions/92794/how-to-change-critically-low-battery-value](https://askubuntu.com/questions/92794/how-to-change-critically-low-battery-value)

Regards

---

### Post by maglin2 on 2021-01-11
When I last tried the dconf editor method has no effect any more.
The lower Upower.conf method worked for my laptop.

---

### Post by SeijiSensei on 2021-01-11
```
sudo apt install apcupsd
```

From the manual page:

>     The apcupsd daemon controls the operation of most American Power Conversion Corp (APC) UPSes.

During a power failure, apcupsd informs users about the loss of utility power and that a shutdown may occur.  If utility power is not restored, a system shutdown will follow when the battery is exhausted, a specified timeout expires, a specified battery charge percentage is reached, or a specified battery runtime (based on internal UPS calculations and determined by power consumption rates) expires.  If the utility power is restored before one of the these shutdown conditions is met, apcupsd will inform users of this and the shutdown will generally be cancelled. 


If you have networked Linux PCs, the daemon can be configured to notify the other systems on the network to shut down as well.

---

### Post by bullwinkle2 on 2021-01-11
> **ActionParsnip said:**
> What is the output of:
```

lsusb; lsb_release -a; uname -a; dmesg | grep -i ups

```
Thanks

.....
Bus 001 Device 004: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
.....
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.5 LTS
Release:    18.04
Codename:    bionic
Linux Ubuntu 4.15.0-130-generic #134-Ubuntu SMP Tue Jan 5 20:46:26 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux
[    2.055691] usb 1-1.2: Product: Back-UPS ES 650 FW:842.J3 .D USB FW:J3
[    2.176989] hid-generic 0003:051D:0002.0003: hiddev1,hidraw2: USB HID v1.10 Device [APC Back-UPS ES 650 FW:842.J3 .D USB FW:J3 ] on usb-0000:00:1a.0-1.2/input0

---

### Post by bullwinkle2 on 2021-01-11
> **grahammechanical said:**
> This is an old answer to a similar question and I do not know if it is still applicable. We still have deconf Editor installed in Ubuntu and all the settings mentioned in that reply are still there. So, it might be the solution you are looking for.

[https://askubuntu.com/questions/92794/how-to-change-critically-low-battery-value](https://askubuntu.com/questions/92794/how-to-change-critically-low-battery-value)

Regards

Thank you!  The second answer in that thread appears to be applicable to current versions of Ubuntu (the one that mentions the file /etc/UPower/UPower.conf).  I can confirm that file is present in Ubuntu Desktop, but not Ubuntu Server.  The three possible states for action are:

PowerOff
Hibernate
HybridSleep

But for some reason the setting "CriticalPowerAction=HybridSleep" is used, don't understand why they would use that instead of PowerOff so that the system gets shut down gracefully.  Also the default percentage remaining cutoff defaults seem a bit low, by default it waits there is only 2% of battery life left to take action, which is great with a fresh battery I suppose, but I have noticed that as batteries get older the percentage remaining tends to drop a lot faster.  The time settings seem more sane (action is taken when 120 seconds of battery life remain) but because by default UsePercentageForPolicy is set to true, the percentage settings are used.  I'm pretty sure that an APC UPS shows both time remaining and percentage remaining, because if I run upower -d it shows these:

```
  ups
    present:             yes
    state:               fully-charged
    warning-level:       none
    time to empty:       34.4 minutes
    percentage:          100%
    icon-name:          'battery-full-charged-symbolic'

```

So, I set UsePercentageForPolicy=false and also I set IgnoreLid=true because it is not a laptop.  So the settings I wound up changing from the defaults are:

IgnoreLid=true
UsePercentageForPolicy=false
CriticalPowerAction=PowerOff

It would be nice if these options were accessible through the Power GUI.  Also my one nit about Upower is it gives you no way to run a script prior to shutting down, in case you need to run some process before the power fails completely.  Other UPS monitoring software can do that I think, but since this is the one that comes preinstalled I imagine it is the one most people use, and probably most users never know it exists on their system.

---

### Post by bullwinkle2 on 2021-01-11
> **maglin2 said:**
> When I last tried the dconf editor method has no effect any more.
The lower Upower.conf method worked for my laptop.

Yep that's what I found too.  Thanks.

---

### Post by bullwinkle2 on 2021-01-11
> **SeijiSensei said:**
> ```
sudo apt install apcupsd
```

Thanks, this looks like the solution for Ubuntu Server which doesn't seem to come with any UPS monitoring preinstalled.

> **SeijiSensei said:**
> From the manual page:

If you have networked Linux PCs, the daemon can be configured to notify the other systems on the network to shut down as well.

Actually I have one place I could maybe use that, IF it is not too difficult to set up.  Will look into that at some point, thanks!

---

### Post by SeijiSensei on 2021-01-11
Like much Linux software, there's little to distinguish between server and workstation applications. You can run apcupsd on either.

---

