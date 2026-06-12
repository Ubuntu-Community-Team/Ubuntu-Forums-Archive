---
title: "Clock going 2.5 times faster than it should"
date: 2007-04-23
forum: General Help
---

### Post by goldfish2 on 2007-04-23
I just upgraded to feisty and now my clock (as reported by date) is going much faster than it should.

Using /proc/interrupts, I have discovered that the timer does 250 ticks per REAL second, but my system progresses by a second every 100 ticks.

I'm on a Thinkpad Laptop 600X running Xubuntu Feisty kernel 2.6.20-15-generic.  After doing a bit of research, I have found people running 64-bit systems (which mine is not) get the same problem, which they have been able to solve using combinations of the following boot options:
noapic
nolapic
noapictimer
acpi=off
acpi=noirq
clock=pmtmr

None of these have worked for me, and I've been making sure to use acpi=off everytime as my laptop does not support it.

Please help.  Thanks,
~Gold Fish2

---

### Post by tictacman on 2007-04-23
This is an old bug thread - but there might be some relevent information here:

[https://bugs.launchpad.net/linux/+bug/17589](https://bugs.launchpad.net/linux/+bug/17589)

At the very bottom of the of thread the user suggests that the real fix was replacing cmos battery.

---

### Post by goldfish2 on 2007-04-23
For now I am assuming the problem is software, since the change was tied to my installation of  Feisty.  I can try a live boot disc to verify this.  The bug report pointed to talks about gain several minutes over the course of a day while my probably is much more sever: My clock is going over 2X faster than it should, so I would gain over a day in  the course of a day, far greater than a few minutes.  I believe my Kernel is incorrectly reading the number of clicks per second that it has set.  

I might have wanted to mention that I had to force a reboot in the middle of the upgrade due to memory filling up. Though I am not sure this will have much play in the potential causes and solutions.

I did run into a couple of other bugs in that bug report that have similar qualities to mine, but none that match my specifications.  If you find others that may be my bug I would be grateful for there links.

~GoldFish2

---

### Post by goldfish2 on 2007-04-23
bump

---

### Post by goldfish2 on 2007-04-24
New Info: The clock issue only appears in the current kernel version that was installed with feisty.  If I boot to any previous kernel version the clock works fine.  It is clear this is an issue with the kernel that is causing it to generate 250 tics per second, but only thinks a second is 100 tics...

This should not happen, I thought it was only a single kernel option to change the number of ticks per second, so that should either be set to 250 or 100.... if someone could check using /proc/interrupts how many tics per second are suppose to occur, that could be helpful.

---

### Post by lodravah on 2007-04-25
Hey.

I'm having the same problem on my Toshiba Satellite Pro 4300, running clean install of Feisty. Same Kernel..

---

### Post by goldfish2 on 2007-04-28
anyone know how to fix this?

---

### Post by lodravah on 2007-04-28
The only fix I found was going back to Kubuntu 6.10. The laptop - bugs in 7.04 were sadly too annoying for my daily use. Including the fans and temperature going ballistic, clock speeding and unable to unmount external HDD. But that's me..

---

### Post by carlok on 2007-05-02
I made a deb of a new 2.6.21.1 kernel and I've just put its config here
[http://perassi.org/quickhacks/kernel-feisty-clock-fix/]("http://perassi.org/quickhacks/kernel-feisty-clock-fix/")
as described on my post
[http://perassi.org/2007/05/02/fixing-fast-running-feisty-kernel/]("http://perassi.org/2007/05/02/fixing-fast-running-feisty-kernel/")
the problem seems to be fixed.

---

### Post by Nehvrook on 2007-05-07
> **goldfish2 said:**
> 
After doing a bit of research, I have found people running 64-bit systems (which mine is not) get the same problem, which they have been able to solve using combinations of the following boot options:
noapic
nolapic
noapictimer
acpi=off
acpi=noirq
clock=pmtmr




I'm having the same problem with 2x clock speed. How do I set the above boot options to try and fix the problem?
(I'm quite new to Ubuntu and Linux, still learning how things work so I don't know how to set a boot option)

---

### Post by Nehvrook on 2007-05-08
Okay never mind. I was having this problem in Ubuntu 6.10 but now I've upgraded to 7.04 and it's gone. I don't understand how but at least it's fixed for me. Good luck to everyone else

---

### Post by tok on 2007-05-26
i encountered similar problems with clock speed, using xubuntu 7.04 on a tp 600x.
i found that setting the bios option "quick boot" to "enable" solved the problem for me!
eventually that helps solving your problems too. 

tok

---

