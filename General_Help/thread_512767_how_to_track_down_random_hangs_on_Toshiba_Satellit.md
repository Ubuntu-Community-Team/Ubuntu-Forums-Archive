---
title: "how to track down random hangs on Toshiba Satellite"
date: 2007-07-29
forum: General Help
---

### Post by happygoodluck on 2007-07-29
Hi -- installed Ubuntu 7.04 on my Toshiba Satellite A75. However, it hangs from time to time, seemingly random. Where do I go to look for clues as to what's casing it? Are there system logs, or an app to track things running high CPU/memory before it crashes?

Symptom - using computer for internet, then the windows become unresponsive but the mouse can still move around. Nothing in the Panel works. Can't open System Manager, can't get the shut down dialog to restart. I have to do Alt+SysReq+B to restart the machine.

thanks in advance

---

### Post by tomchuk on 2007-07-29
If you're using them, try getting rid of the proprietary fglrx drivers and use the open source radeon driver.

---

### Post by happygoodluck on 2007-08-05
sorry for the newbie question, but how would I know if the drivers I'm using are the fglrx proprietary drivers or the open source drivers?
In xorg.conf, I found this line:

Section "Device"
	Identifier	"ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]"
	Driver		"ati"
	BusID		"PCI:1:5:0"
EndSection

In Device Manager, I clicked the tree node for "Radeon Mobility 9100" (which matches above) and it listed the vendor as ATI. But, I haven't found anything about "open source" or "fglrx". Since ATI is written all over, I suspect those are ATI's proprietary drivers, but no way for me to know for sure.

thanks!!

---

### Post by happygoodluck on 2007-08-05
One way that consistently reproduces the hang:
1) use Linux for a few minutes, eveything is ok
2) leave the machine unused for 10 minutes or so
3) click the Firefox icon in the Panel to launch Firefox

Actual:
- Firefox does not launch
- icon gets a solid border around it
- nothing in the panel responds, cannot open any programs
- have to restart

---

### Post by gkellerman on 2007-08-08
Hi.  Working on a Toshiba P30 and I am experiencing the same symptoms.  Seemingly random hangs while using KDE.

When I boot into a console only mode, I still get the 'random' freeze.  This leads me to believe that even if the display driver is a problem, it is definitely not the only issue.

I have previously played with various combinations of enabling and disabling ACPI LAPIC etc...  also with no success...  (I had the same issues with SuSe, Gentoo, Mepis) using their various kernel versions and patches...

I AM STARTING TO BELIEVE THAT LINUX IS NOT MEANT FOR THIS LAPTOP!

Any help will be appreciated.

PS:  Toshiba P30 with ATI Radeon 9700 / 1Gb Memory Feisty 7.04 running Kubuntu.

---

### Post by happygoodluck on 2007-08-10
One guess I have is that the laptop's power saving feature may interfere. Perhaps the laptop is trying to go into "sleep" or "power saving" mode, but Linux has something running and the two fight for control - ie, hang the machine.
I'm going to disable all power saving on the laptop to see if that helps any, or refute this guess.

Still haven't figured out how to replace the ATI drivers though.

---

### Post by happygoodluck on 2007-08-10
Another actual behavior:

- the clock stops -- it will show the same time for 3-4 minutes

---

### Post by juice19 on 2007-08-13
Having similar freezes ctr alt <- dosnt work.  when it freezes only mouse will work for a few seconds.  If you find anything out please let me know.  

I also have a toshiba satellite a75 s213 with ATI Radeon 9100IGP. 

One more thing,  Freezes happen faster and more often if i run dosbox or dosemu.

Thanks

---

### Post by LuckyDevil on 2007-09-15
Not sure if this helps you or not...I was having the same issues.  After fixing all over-heating issues (it had many) and upgrading the bios I still had constant freezing issues.  I read a forum somewhere suggesting turning off hyper-threading in the bios.  After that I've run for weeks without a lockup, previously I couldn't get more than an hour.

Not the best solution, but it's worked well for me on the toshiba a75-s206.  

Hope it works for you, if not, feel free to pm me, I have plenty of experience with these laptops as my whole family has had problems with them!

---

### Post by rubari777 on 2008-04-11
I received a Toshiba P30 as a gift because of the hang problem, and it has nothing to do with software, same happens with XP, it's just a hardware design problem, laptop has two fans that take air from beneath and blows it to the rear, actually what it does is take all dirt from the surface where the laptop is and drops it inside like a vacuum cleaner, specially if you are used to sit on the rug to navigate or chat.  I disassembly completely and found both sinks clogged with lint, I think it's very difficult to remove without opening, you can try blowing air from behind while vacuum from the fan openings below, this explains why reappears pretty soon. Ubuntu, Kubuntu and Mepis run just fine and installation is very smooth, with some versions you will need to get the correct driver for the wireless adapter. And something else, rise the back of the notebook to give some additional airflow, used wine cork will help.

---

### Post by pixnaps on 2008-07-12
> **juice19 said:**
> Having similar freezes ctr alt <- dosnt work.  when it freezes only mouse will work for a few seconds.  If you find anything out please let me know.  

I also have a toshiba satellite a75 s213 with ATI Radeon 9100IGP. 

One more thing,  Freezes happen faster and more often if i run dosbox or dosemu.

Thanks
I get this too, on my toshiba satellite A135-S4527. It freezes most frequently when running Dosbox, but also sometimes in the ordinary gnome environment (e.g. using firefox).

Help?

---

### Post by pixnaps on 2008-07-12
I've made a new (non-archive) thread for this problem, [here](http://ubuntuforums.org/showthread.php?p=5374160).

---

