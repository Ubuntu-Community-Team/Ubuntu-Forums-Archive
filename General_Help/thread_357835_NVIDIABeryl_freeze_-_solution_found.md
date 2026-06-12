---
title: "NVIDIA/Beryl freeze - solution found"
date: 2007-02-10
forum: General Help
---

### Post by closet geek on 2007-02-10
If you are experiencing regular freezes while using Beryl with the NVIDIA drivers then I believe I have stumbled upon the solution. The type of freezes I used to get were odd: the mouse would still move, the music would still play but I couldn't click anything and the keyboard was useless. The only option was a hard reboot.

This solution is courtesy of the NVIDIA forums and has so far caused my system to not freeze for 3 days when it used to freeze every couple of hours. Run this:

```

modprobe nvidia NVreg_RegistryDwords="PerfLevelSrc=0x2222"; echo 'options nvidia NVreg_RegistryDwords="PerfLevelSrc=0x2222"' | sudo tee -a /etc/modprobe.d/options

```

The first part modprobes the module with the new option, the second part is my creation to make sure the module is loaded upon restart with the correct option.

I don't know why this works but it does for me and for others on the NVIDIA forums. I did a thorough search of these forums and I couldn't find a single thread with this fix in it so I hope this helps. Use at your own risk.

cg

---

### Post by BackwardsDown on 2007-02-10
I recognize the symptoms. But before I run your solution (and possibly braking my pc) can you tell me how I can uninstall your fix?

---

### Post by closet geek on 2007-02-10
> **BackwardsDown said:**
> I recognize the symptoms. But before I run your solution (and possibly braking my pc) can you tell me how I can uninstall your fix?

Sure:

```

modprobe nvidia; sudo replace "options nvidia NVreg_RegistryDwords=\"PerfLevelSrc=0x2222\"" "" -- /etc/modprobe.d/options

```

cg

---

### Post by FuturePilot on 2007-03-01
I've had a similar problem. Only everything is frozen. No mouse, no keyboard, no nothing every few minuets. I'm going to give this a shot. Hopefully it works.

---

### Post by Jphenow on 2007-03-05
By the way your fix doesn't exist, replace isn't a command

---

### Post by Tyr_7BE on 2007-03-06
I had a very similar problem.  Upgrading the nvidia drivers using the drivers found here fixed my problem.  3 days now without a single lockup, and it used to happen at least twice per day.

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by HasratUSA on 2007-03-07
> **BackwardsDown said:**
> I recognize the symptoms. But before I run your solution (and possibly braking my pc) can you tell me how I can uninstall your fix?

ROFL :lolflag: I was planning on asking the same question

---

### Post by HasratUSA on 2007-03-07
> **Tyr_7BE said:**
> I had a very similar problem.  Upgrading the nvidia drivers using the drivers found here fixed my problem.  3 days now without a single lockup, and it used to happen at least twice per day.

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

milone is the man i'm telling ya!!! :)

---

### Post by lvlo on 2007-03-08
there  is another solution that works for me [http://www.nvnews.net/vbulletin/showthread.php?t=86253]("http://www.nvnews.net/vbulletin/showthread.php?t=86253")

---

### Post by bwhaley on 2007-07-13
FYI, This work great for me with an Nvidia 7800! Thanks!

---

### Post by johnnyzazza on 2007-11-11
This has been driving me crazy.  I can confirm this works as well.
Nvidia 7800

Great thanks.

---

