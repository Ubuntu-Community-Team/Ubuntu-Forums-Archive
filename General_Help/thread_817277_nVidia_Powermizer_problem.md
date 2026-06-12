---
title: "nVidia Powermizer problem"
date: 2008-06-03
forum: General Help
---

### Post by bravemenrun333 on 2008-06-03
Has this problem been solved in the meantime?
I've been using Windows XP since my gpu renders all compiz effects unusable with ubuntu, because of this stupid powermizer problem (powermizer being to laggy when throttling up the gpu) :(

---

### Post by FuturePilot on 2008-06-03
No :(

Is it really that slow that you have to use Windows? If it is you could always just disable Compiz. :)

---

### Post by bravemenrun333 on 2008-06-04
Oh no! And theres no solving of the issue in sight?
Is nVidia aware of the problem?
I dont want to turn compiz off :(

---

### Post by sdennie on 2008-06-04
This problem has been known for a long, long time and is 100% an nvidia problem (seems slightly better in 173.15.04 driver though).  There are various fixes for it but, the least dangerous (as in not dangerous at all) is to just force the card to full power: [http://ubuntuforums.org/showthread.php?t=747294](http://ubuntuforums.org/showthread.php?t=747294).  That may be overkill but the general sentiment is correct (specifically "nvidia-setting -q all" sets the card to max power and it will stay there for 30 seconds).

---

### Post by bravemenrun333 on 2008-06-04
I dont like the idea of having a script looping all the time to lock the performance at 100%... seems to me to be a "ugly" fix :(

Is there a chance for a new driver release which fixes the problem? There are two possibilities for the devs:

1) to make a switch which allows user to turn off powermizer

2) to correct the speed of throttling gpu power

come on, nvidia!

---

### Post by sdennie on 2008-06-04
On the nvidia linux forums, an nvidia developer stated that PowerMizer would be configurable on linux in a future driver release.  However, nvidia rarely specifies when linux fixes or enhancements will be released so, PowerMizer support may come in 6 weeks or in 6 years (or maybe even never.  2 years ago they stated that they had no plans to add PowerMizer controls for linux).

---

### Post by s0ury on 2008-06-04
Boys, some guy from the nvidia forum posted the fix, i tried it on my 8600GS and it works, i have no idea why and how he only posted the fix, didn't explain anything, someone more experienced might want to explain it (the reason why this file is used on boot since I created it just now)
anyhow. fix:
1. Create this file with:
Alt + F2:
```
gksu gedit /etc/modprobe.conf
```

2. Insert these two lines:
```

options nvidia NVreg_RegistryDwords="PerfLevelSrc=0x2222"
options nvidia NVreg_Mobile=1

```

3. Save and reboot.

It worked for me and it sticks the powermizer mode to 2 (people who need maximum battery life on their laptops wouldn't be seeking to disable powermizer in the first place)

Hope i've helped and looking forward to an experienced user to explain this.

I've seen other solutions but they require a timer who'd occupy the proccessor continuously, this one seems like it's the safest one.

---

### Post by sdennie on 2008-06-04
> 
options nvidia NVreg_RegistryDwords="PerfLevelSrc=0x2222"


Actually, this is probably the least safe solution.  It does indeed lock the video card to the highest PowerMizer state but, as far as I've seen, no one from nvidia has ever commented on what sorts of other effects it may have.  It does work (I've used it in the past) but, the reason the solution wasn't explained is because no one but nvidia completely understands what it does so, it can't be explained.  Others have claimed that it's also possible to force full power on AC and normal PowerMizer settings while on battery with a similar fix but, I've not tried it.

Running a script that pings the card every 25 seconds is certainly not ideal but, it uses no noticeable CPU power (it's asleep 99.9% of the time) and the side effects are well known (every 25 seconds you ask the nvidia card about itself).

---

### Post by bravemenrun333 on 2008-06-05
My solution was to insert the following line into /etc/modprobe.d/nvidia-kernel-nkc

options nvidia_new NVreg_Mobile=1 NVreg_RegistryDwords="PerfLevelSrc=0x2222" 

Now the performance level seems to be locked to "2" and my card does not get warmer than 55°C at idle

---

### Post by bravemenrun333 on 2008-11-28
Under 8.10 there's no more nvidia-kernel-nkc file!

It's the following fix:
paste following line into /etc/modprobe.d/options
options nvidia NVreg_RegistryDwords="PerfLevelSrc=0x2222"

---

### Post by neurotopia on 2008-12-14
Hi.  I've spent the last 4 days obsessively searching for an actual fix to this problem.  I'm running sager np5793 and Ubuntu 8.10 with an 8800gtx and the 177.82 vidia driver.  I've tried using the various fixes I've found around the 'net with both the 177 and 173 nvidia drivers -- that I've DLed from both the nvidia site as well as through symantec packet manager.

I've tried changing xorg.conf as well as /etc/modprobe.d/options using various iterations of the 
```

options "RegistryDwords" "PowerMizerLevelAC=0x2"
options "RegistryDwords" "PowerMizerLevel=0x2"

```
in options and 
```

options nvidia NVreg_RegistryDwords="PerfLevelSrc=0x2222"
options nvidia NVreg_Mobile=1 (also varied this line trying the "nvidia_new" option).  

```
in both xorg.conf and/or options.  I even tried "CooldBits" "1" in xorg. conf which gave me access to the option for changing freqs, however, I was never able to get those changes to take effect.

Vor, I  tried your query script, as well.  The best result I have been able to get from any of these approaches allowed powermizer to move up to level 1 (from a range of levels 0-3).

Any help that y'all can offer would be tremendously appreciated.  As others have already expressed, paying money for hardware that you can't actually use is more than a little frustrating.  And I'm trying very hard to resist going back to windows, even for gaming.

---

### Post by neurotopia on 2008-12-16
You shouldn't underestimate my complete lack of self-esteem in this matter: my ability to grovel is indeed a force to be reckoned with.  ):P

---

### Post by interim descriptor on 2009-02-20
I've not been able to get a satisfactory solution, either.

The only thing I've done that helps is adding the following line to the "Device" Section:

Option  "ConnectToAcpid"        "false"

After restarting X, you may unplug your laptop from external power, and it will stay on the highest performance mode. But it has to start out connected to the AC adapter, which is a huge limitation.

I theorize that if someone were to modify ACPID to always report being connected to external power, then the nvidia driver could be fooled into being on the highest power mode, at all times, without ever being connected to AC power.

Anyone know how to do this?

---

### Post by matmat07 on 2009-02-21
Maybe i'm saying something obvious, but in windows, we had to edit the registry to edit powermizer and if I remember correctly, the the first number are for AC and the 2 last for Battery(or vice versa). 22= no powermiser usage and 33 = powermiser usage.

---

### Post by neurotopia on 2009-02-24
in the nvidia notes for the 180.29 drivers it mentions fixing a regressive bug with powermizer and the 2.6 kernel.  anyone know if this driver fixes the problem?

---

