---
title: "Computer Randomly reboots"
date: 2020-12-06
forum: General Help
---

### Post by kjsmith on 2020-12-06
Hello, 

This problem started occurring over the last few weeks. The computer randomly will restart. Sometimes it will restart and come back up like I just turned it on or told it to restart, other times it will restart right after the grub menu and do this multiple times before booting back in to Ubuntu again. I can run the live CD so far without any issues. My first thought was a hard drive was on its way out, so I swapped in a new hard drive that I was going to use for a different system, and completely disconnected the older drive. Reinstalled the OS and the same problem occurs. The live CD appears to run without any issues, but I haven't used it for more than an hour before going back to the installed OS. 

After the hard drive I suspected maybe thermals were a problem. I knew my front case fan had died (on my list of things to replace), but I found the back case fan died as well. It sits in the corner of the room under a desk with another desktop next to it, so air flow isn't ideal, but it isn't blocked by anything either. The power supply, CPU cooler fan, and GPU fan are all working. However, with it sitting on my desk, case open, the issue still was occurring and the BIOS and 'sensors' application were should temps to be 45 degC or less . I was thinking possibly the power supply, but being a 650W supply, with 4 HDs, and a GTX 750 graphics card, I cannot image I am using any where near the limits of that supply. I'm at a loss of what to investigate next. 

I've had the computer sitting at the BIOS screen for the past few hours, no issues so far. Temps at 40 degC. 


[LIST]
[*]Ubuntu 20.04
[*]AsusRock X-99 extreme 4
[*]Intel Xeon E5-1620
[*]16GB of RAM Corsair DDR4-2133 (4GB in quad channel)
[/LIST]

Before I submitted this, I realized that I did not recall having this problem with Ubuntu 18.04, but also was running 20.04 for a few weeks before this problem started to happen. 

Thanks,
-Kevin

---

### Post by NM5TF on 2020-12-06
so what you might try is [COLOR="#FF0000"]timeshift[/COLOR] to restore your system to a previous working version...

go here  [https://linuxconfig.org/ubuntu-20-04-system-backup-and-restore](https://linuxconfig.org/ubuntu-20-04-system-backup-and-restore)

tommy

---

### Post by dionblundell on 2020-12-06
I would definitely be looking at a temperature/thermal issue.

The BIOS screen isn't a very good test of a computer, as nothing really happens there.

I would suggest you buy a can of dry compressed air, and use this to blow out the dust from your Power Supply and the heatsink of your CPU. Make sure your PC is disconnected from power. When you do this, make sure you use something non-conductive to stop the PSU and CPU fan spinning (if you blow them with compressed air, you will over-spin them and ruin the bearings), you are only trying to blow out the dust, not spin the fans. After doing that, blow the loose dust out of the case. Once the inside of the case looks clean from dust, remove the RAM, blow clean the RAM slots, re-seat the RAM. If this does not help, your next step is to renew the thermal paste on the CPU heatsink.

Good luck

---

### Post by kjsmith on 2020-12-07
Thanks Tommy and Dion. I'll give those items a try and see what comes out. 

I agree with you Dion the BIOS isn't a good "stress test" for thermals, more or less watch to see how long it would sit there idle and if it would restart. However, this afternoon, I was running a few applications, games, etc. to put load on the CPU and try to drive up some heat in the case. When the system was running and I was checking the thermals, but everything was sub 50 degrees from the 'sensors' command line report and the load was bout 50% on all the cores. Then after I stepped away for dinner it starts doing it again so I was not around when it started to happen to see what the temps were.  

However, can we assume for a moment after I blow out the fans, PSU, etc., and redo the thermal paste on the CPU (I plan on doing this in the next day or two). Any thoughts after that step if the issue keeps occurring of things to try?

Thanks again for the suggestions,
-Kevin

---

### Post by CatKiller on 2020-12-07
> **kjsmith said:**
> Any thoughts after that step if the issue keeps occurring of things to try?
Check the motherboard (and power supply if you can safely examine them) for bulging capacitors. The machine is relatively elderly and has had a period of elevated temperatures because of the dead fans. Spontaneous rebooting tends to be the result of voltage spikes, in my experience.

---

### Post by rbmorse on 2020-12-07
What Catkiller said.  

In addition, despite the load being well within rating, the PSU could still be the problem, especially if it's more than a couple of years old. Capacitors age from thermal stress, occasionally prematurely, and may develop intermittent internal short circuits. Same is true for the capacitors in the VRM circuits located near the CPU.  

For an ATX spec machine, a momentary short circuit on the 3 Volt rail is interpreted as pressing the reset button. 

One other thing to check...make sure the RAM modules are fully seated in their sockets. Same for any expansion cards in PCI slots, and that the retention screw that attaches to the backplane isn't pulling the card out of alignment when tightened.

---

