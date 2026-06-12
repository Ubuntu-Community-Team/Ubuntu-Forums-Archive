---
title: "clock is counting 2-3 times too fast"
date: 2007-11-15
forum: General Help
---

### Post by liblamb on 2007-11-15
This morning I turned my computer on and now the clock runs 2-3 times faster than it should.  I can watch the seconds speed by.  In addition any icon animation is very fast and it is hard to type without multiple letters appearing.  Any ideas?  I don't even know what details to provide.  This occurs for any desktop environment.

Ubuntu 7.10
Kernel 2.6.22-14-generic
Gnome 2.20.1
1GB  RAM
AMD 64 X2 3800+

---

### Post by reimerjc on 2007-11-15
> **liblamb said:**
> This morning I turned my computer on and now the clock runs 2-3 times faster than it should.  I can watch the seconds speed by.  In addition any icon animation is very fast and it is hard to type without multiple letters appearing.  Any ideas?  I don't even know what details to provide.  This occurs for any desktop environment.

Ubuntu 7.10
Kernel 2.6.22-14-generic
Gnome 2.20.1
1GB  RAM
AMD 64 X2 3800+

Sounds like an issue with your internal clock frequency.  Since I am a computer engineer, I could try to explain to you what is happening but I don't think that would help.  Try resetting your BIOS to see if that helps.

---

### Post by liblamb on 2007-11-15
I have done a little more checking and the BIOS seems to keep the time correctly.  But, when I boot into either Ubuntu or Fedora the clock (and everything else) runs way too fast.  Can GRUB affect this?

---

### Post by reimerjc on 2007-11-16
> **liblamb said:**
> I have done a little more checking and the BIOS seems to keep the time correctly.  But, when I boot into either Ubuntu or Fedora the clock (and everything else) runs way too fast.  Can GRUB affect this?

Not sure if GRUB is causing this.  Anyway, I'll try to explain why everything is running fast.  You have an internal clock (say 2GHz) that is used by the CPU to execute "commands."  Typically, the "command" will run synchronously with the clock on the rising edge (the clock is essential a square wave).  When you say that everything is running fast, then that leaves me to believe that it is a hardware issue where for some reason the clock that your CPU is seeing is at a higher frequency.  It is much more complicated than this, but hopefully this gives you a better idea of whats happening.  Now where along the CPU and/or motherboard the frequency appears to be off, I'm not sure.  If your system is not overheating, than it most likely is an isolated issue.  In any event, I would send the computer in for repairs.

---

### Post by keithlommel on 2007-11-16
I am having the exact same problem, and it seems to have started about the same time. Perhaps something was broken in a recent update?

BTW, the BIOS keeps perfect time, and when I boot into Windows XP, the clock also runs accurately, so this seems to be a Ubuntu problem.

Anybody else? Any ideas?

---

### Post by liblamb on 2007-11-16
I think you are right reimerjc.  I've booted from a couple live CDs and they all run fast.  Grrrr... So you think this is a motherboard problem?  I put the PC together myself so I'll have to call each part   maker  myself.

---

### Post by hardyn on 2007-11-16
is the RTC indexed from the core speed of the processor or the FSB?  I am not a computer engineer, but if your bios has mis-represented the FSB speed of the processor, you could be in an over-clock condition.  before you start sending stuff back on warranty, update the firmware of the motherboard.  no improvement, launchpad. and consider returning, buying a new motherboard.

---

### Post by keithlommel on 2007-11-17
Yeah, I tried a fresh install and the live CDs and they all exhibit the same behavior, so it's likely hardware related, What's odd, though, is that I've been running this machine for over a month now without problem, and even now it still has no problems when booting into Windows XP. I guess Linux gets its clock timing from a different source than XP, and it's that source that is broken.

I have an ECS GeForce6100SM-M with an AMD Athlon 64 X2 4200+ (65W). I haven't monkeyed with any of the BIOS settings or tried to overclock anything.

I don't think the overall computer is overclocked, though, because software does not appear to be running faster than normal. It is only the system clock, and a few isolated things which seem to be indexed to the system clock (mouse double click time, keyboard repeat rate, some animated stuff on websites, etc.) that is running fast. If I play back music or movies, they all play at regular speed and the elapsed time counter in the player is normal.

--Keith

---

### Post by keithlommel on 2007-11-17
I've done a little research and it seems there are some motherboard chipset, BIOS, and kernel combinations that wind up supplying linux with two sets of timing signals, resulting in the system clock advancing at double speed. 

Here's how I fixed mine.

Edit your GRUB configuration file:

```
gksudo gedit /boot/grub/menu.lst
```

Look for a line like this:

```
kernel /boot/vmlinuz-2.6.22-14-generic root=/dev/sdb1 ro quiet splash
```

Append this:

```
noapic acpi=off
```

So it now looks like this:

```
kernel /boot/vmlinuz-2.6.22-14-generic root=/dev/sdb1 ro quiet splash noapic acpi=off
```

This worked for me. If that doesn't work you might try one of the following:

```
noapic nolapic
noapic acpi=noirq
noapictimer
noapictimer irqpoll
noapic acpi=noirq nolapic

```

Good luck!

---

### Post by Nehvrook on 2007-11-17
I was having a problem very similar to this when I upgraded to gutsy. The solution for me was to add "clock=tsc" to the end of the kernel line in the grub menu.

Mine ended up looking like this:```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=376719ed-ba94-4f73-ad45-26e2d9e91461 ro quiet splash clock=tsc
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
```

---

### Post by liblamb on 2007-11-17
Woohoo! keithlommel is super cool.  The solution as you suggested (noapic acpi=off) worked.  GRUB was the culprit and I'm not surprised because I was messing with it before this happened, although there was also a kernel-upgrade I believe.  Yeah for problem solved.

Is it possible that adding an entry in menu.lst to boot Fedora could have caused the problem?  Maybe I'll try adding it in again and find out.

Great help.

---

### Post by halln on 2007-12-10
> **keithlommel said:**
> I've done a little research and it seems there are some motherboard chipset, BIOS, and kernel combinations that wind up supplying linux with two sets of timing signals, resulting in the system clock advancing at double speed. 

Here's how I fixed mine.

Edit your GRUB configuration file:

```
gksudo gedit /boot/grub/menu.lst
```

Look for a line like this:

```
kernel /boot/vmlinuz-2.6.22-14-generic root=/dev/sdb1 ro quiet splash
```

Append this:

```
noapic acpi=off
```

So it now looks like this:

```
kernel /boot/vmlinuz-2.6.22-14-generic root=/dev/sdb1 ro quiet splash noapic acpi=off
```

This worked for me. If that doesn't work you might try one of the following:

```
noapic nolapic
noapic acpi=noirq
noapictimer
noapictimer irqpoll
noapic acpi=noirq nolapic

```

Good luck!

It worked for me too but afterwards my system wont shutdown.. need help

---

### Post by dooglio on 2007-12-18
> **Nehvrook said:**
> I was having a problem very similar to this when I upgraded to gutsy. The solution for me was to add "clock=tsc" to the end of the kernel line in the grub menu.

Mine ended up looking like this:```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=376719ed-ba94-4f73-ad45-26e2d9e91461 ro quiet splash clock=tsc
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
```

This fix worked for me. Thanks for posting it!

---

### Post by dooglio on 2007-12-18
> **dooglio said:**
> This fix worked for me. Thanks for posting it!

Well...almost. Now my system clock runs too slow! :(

---

