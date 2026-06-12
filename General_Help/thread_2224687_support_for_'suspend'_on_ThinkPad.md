---
title: "support for 'suspend' on ThinkPad?"
date: 2014-05-17
forum: General Help
---

### Post by Apollo8 on 2014-05-17
I am running 14.04 64 bit on a ThinkPad X1 Carbon. Everything works except suspend/sleep. It is a big battery drain to have to leave the computer running when I am not using it, even if the screen shuts off. Is there a way to get 'suspend' or sleep mode working?

---

### Post by tgalati4 on 2014-05-17
There are log files in /var/log (pm-powersave.log and pm-suspend.log).  Go through them and post any helpful errors.

---

### Post by Apollo8 on 2014-05-17
I searched for both of those things and couldn't find them. What I can tell you is that whenever I try to put the laptop to sleep, the screen goes dark, the adaptive keyboard stays on, and I cant get it to wake up. I have to do a hard reset by holding down the power button.

---

### Post by tgalati4 on 2014-05-18
What power management daemon are you running?

For me: (I'm running 12.10-based Linux Mint Mate)

tgalati4@Mint14-Extensa ~ $ ps aux | grep power
tgalati4  2142  0.0  0.2 556016  4176 ?        Sl   Apr02   0:28 mate-power-manager
root      2212  0.0  0.0 222168  1948 ?        Sl   Apr02   0:46 /usr/lib/upower/upowerd

```
 ps aux | grep power
```

---

### Post by Apollo8 on 2014-05-18
root      1562  0.0  0.1 239520  4740 ?        Sl   08:11   0:00 /usr/lib/upower/upowerd
mxxxn   1612  0.0  0.1 295784  4412 ?        Ssl  08:11   0:00 /usr/lib/x86_64-linux-gnu/indicator-power/indicator-power-service
mxxxn   3324  0.0  0.0  15948   920 pts/1    S+   08:40   0:00 grep --color=auto power

---

### Post by tgalati4 on 2014-05-18
Play with upower:

```
upower --help
```

Post the output of:

```
upower --dump
```

---

### Post by Apollo8 on 2014-05-21
Device: /org/freedesktop/UPower/devices/battery_BAT0
  native-path:          BAT0
  vendor:               SMP
  model:                45N1703
  serial:               1308
  power supply:         yes
  updated:              Wed 21 May 2014 07:28:00 PM PDT (120 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               fully-charged
    energy:              45.62 Wh
    energy-empty:        0 Wh
    energy-full:         45.62 Wh
    energy-full-design:  45.02 Wh
    energy-rate:         0 W
    voltage:             16.584 V
    percentage:          100%
    capacity:            100%
    technology:          lithium-polymer

Device: /org/freedesktop/UPower/devices/line_power_AC
  native-path:          AC
  power supply:         yes
  updated:              Wed 21 May 2014 07:27:54 PM PDT (126 seconds ago)
  has history:          no
  has statistics:       no
  line-power
    online:             yes

Daemon:
  daemon-version:  0.9.23
  can-suspend:     yes
  can-hibernate:   no
  on-battery:      no
  on-low-battery:  no
  lid-is-closed:   no
  lid-is-present:  yes
  is-docked:       no

---

### Post by tgalati4 on 2014-05-21
Post the output of:

```
free
```

It's possible that you may not have a large enough swap to hold the RAM snapshot, therefore your system won't hibernate, and possibly interfere with suspend.

---

### Post by sam_baker2 on 2014-05-21
I have a Thinkpad 500 and I use rtcwake.
Works great with suspend.

---

### Post by Apollo8 on 2014-05-23
total       used       free     shared    buffers     cached
Mem:       3941304    1297804    2643500     366428      32420     856912
-/+ buffers/cache:     408472    3532832
Swap:      4083708          0    4083708

---

### Post by tgalati4 on 2014-05-23
So you have ~4 GB of RAM and a 4 GB swap, so hibernate should be activated.  Perhaps it was turned off manually or during installation because of a bug.  Check your power management settings and see if hibernate can be switched on and see if that works.  Also, check all of the power management settings in BIOS and make a list of those settings.

---

### Post by Apollo8 on 2014-05-26
I'm stumped. I looked in the "power" section of the BIOS but there was nothing about hibernate or suspend. Some settings for Intel Speed Step, battery optimization, etc... but nothing that looks like it has anything to do with this. I also couldnt find anything in the Ubuntu power settings that would explain why the screen doesn't come back on after suspending.

---

### Post by tgalati4 on 2014-05-26
Have you gone through this page?  [https://help.ubuntu.com/community/PowerManagement/Hibernate](https://help.ubuntu.com/community/PowerManagement/Hibernate)

---

### Post by Apollo8 on 2014-05-31
Thanks for that info, but it doens't help. I dont know what to do with that stuff. I dont know how to compile something from a kernel. I'll keep searching the web but I think 'suspend' just isn't going to work with Linux.

---

### Post by tgalati4 on 2014-05-31
Don't give up to soon.  You say suspend does not work, but it does go to sleep.  It just doesn't wake up properly.  So now you need to dig a little deeper.  

Go through the settings in /etc/default/acpi-support

Install acpitool then post the output:

```
sudo apt-get install acpitool
acpitool -w
```

This gives a list of devices that have power during sleep.  You may need to turn some of them on or off to get a proper wake cycle.  For instance, you say the keyboard stays lit, that implies it has power during sleep.  So try to figure out which device the keyboard is connected to and set it to disable.

---

### Post by Apollo8 on 2014-05-31
Here it is:
 Device    S-state      Status   Sysfs node
  ---------------------------------------
  1. LID      S4    *enabled 
  2. SLPB      S3    *enabled 
  3. IGBE      S4    *enabled   pci:0000:00:19.0
  4. EXP2      S4    *disabled  pci:0000:00:1c.1
  5. XHCI      S3    *enabled   pci:0000:00:14.0
  6. EHC1      S3    *enabled   pci:0000:00:1d.0


Thanks for sticking with me on this!

---

### Post by tgalati4 on 2014-05-31
So you have a lid switch and an SLPB which is probably a sleep power button which remain enabled during S4 and S3 sleep modes.  You can look up the sleep modes and what they mean.  You need power to both of those, because if you turn them off, then you will definitely not be able to wake up.

I'm not sure what the other 4 are.  What is the output of:

```
lspci
```

Start changing settings in /etc/default/acpi-support.  But only change one parameter at a time.  Take notes, and change the settings back if you get no change in behavior.  This is a tedious process that will require many reboots and hard-resets.  So make sure you don't have any open files or applications while doing this.

---

### Post by xadder on 2014-06-07
I am having the same problem. If I close the lid, my Thinkpad (X220i) goes to sleep as expected. When I open, the screen is rally dark and nothing happens when I type my password. 

I have loads of disk spare, and swap is free gives:

             total       used       free     shared    buffers     cached
Mem:       4016028    1106036    2909992      69324      79488     522936
-/+ buffers/cache:     503612    3512416
Swap:      7811068          0    7811068

Suspend has worked fine on the laptop until 14.04 (I run Xubuntu). Help!

---

### Post by xadder on 2014-06-19
BUMP. This is a real problem for everyday usage of my Thinkpad.

---

