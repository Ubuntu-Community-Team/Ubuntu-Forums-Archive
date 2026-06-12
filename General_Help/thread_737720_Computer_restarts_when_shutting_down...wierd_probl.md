---
title: "Computer restarts when shutting down...wierd problem"
date: 2008-03-27
forum: General Help
---

### Post by lespaul_rentals on 2008-03-27
I am posting this in the Community Cafe because I would like some advice as soon as possible.

I got done building my computer and everything works fine except for one problem.  When I tell my computer to shut down, it will go through all the processes and power off, then all of a sudden it will spring back to life and restart!  It's not a Linux problem with my hardware, either (I have a Gigabyte GA-M57SLI-S4).  No matter what distro I use, I get the same thing.  Windows is no better.  Heck, even if I use the power button to attempt a cold shutdown, it will power off then power back up.  The only way to stop it from running is by cutting off the power at the source.

Any advice?  I've gone through all the BIOS settings and disabled all the settings that might play a role in this.  Should I RMA the motherboard?

Thanks!

---

### Post by kutjara on 2008-03-30
> **lespaul_rentals said:**
> I am posting this in the Community Cafe because I would like some advice as soon as possible.

I got done building my computer and everything works fine except for one problem.  When I tell my computer to shut down, it will go through all the processes and power off, then all of a sudden it will spring back to life and restart!  It's not a Linux problem with my hardware, either (I have a Gigabyte GA-M57SLI-S4).  No matter what distro I use, I get the same thing.  Windows is no better.  Heck, even if I use the power button to attempt a cold shutdown, it will power off then power back up.  The only way to stop it from running is by cutting off the power at the source.

Any advice?  I've gone through all the BIOS settings and disabled all the settings that might play a role in this.  Should I RMA the motherboard?

Thanks!

It certainly sounds like a motherboard problem, since it's replicated across a range of OSes. The fact it even occurs when you hard stop the system with the power button, makes me think it can only be hardware-related.

It might be worth having a look at your MB documentation regarding dip switch settings before you send it back, however. Maybe one of the switches is sending a "keep alive" instruction. I'm not familiar with that particular MB, though, so I could easily be wrong.

You say you can only get the machine to shut down by pulling the power cord. What happens when you then plug it back in? Does the machine immediately reboot or does it stay off until you turn it on?

---

### Post by K.Mandla on 2008-03-30
Moved to General Help.

---

### Post by lespaul_rentals on 2008-03-31
> **kutjara said:**
> It certainly sounds like a motherboard problem, since it's replicated across a range of OSes. The fact it even occurs when you hard stop the system with the power button, makes me think it can only be hardware-related.

It might be worth having a look at your MB documentation regarding dip switch settings before you send it back, however. Maybe one of the switches is sending a "keep alive" instruction. I'm not familiar with that particular MB, though, so I could easily be wrong.

You say you can only get the machine to shut down by pulling the power cord. What happens when you then plug it back in? Does the machine immediately reboot or does it stay off until you turn it on?

The Gigabyte S4-series has no motherboard jumpers.  All settings are controlled in the  BIOS.  I even flashed the BIOS with the newest version, thinking the issue might have been resolved with the update.  Same problem.  Good thinking, though.

If I plug it back in, it will stay powered down.  It's only when I turn it on that it gets a life of its own and refuses to die.

---

### Post by darkorical on 2008-03-31
you might want to check your power button connection you could have it crossed with the reset button I know it sounds like a silly solution but i have done it before

---

### Post by kutjara on 2008-04-02
The only other thing I can think of is that Ubuntu may have got it into its head that "shutdown" means "restart." It could have mapped the power button to restart as well. It sounds a bit far-fetched, I know, but I'm otherwise out of ideas.

---

### Post by lespaul_rentals on 2008-04-02
> **kutjara said:**
> The only other thing I can think of is that Ubuntu may have got it into its head that "shutdown" means "restart." It could have mapped the power button to restart as well. It sounds a bit far-fetched, I know, but I'm otherwise out of ideas.

It's not an Ubuntu problem.  openSuSE, PCLinuxOS, Linux Mint, SimplyMEPIS, Slackware, Arch, and Windows XP all had the same problem.  If I used the power button during POST or during other such times when the operating system had no control over the computer, it still had the same problem.

[QUOTE=darkorical]you might want to check your power button connection you could have it crossed with the reset button I know it sounds like a silly solution but i have done it before[/QUOTE]

Thanks, but nope.  I've done it too; don't you feel stupid when you realize what the problem is?  Haha.  :)   Unfortunately the fix isn't that simple this time.  I checked, checked again, checked thrice.  I even tried reversing the polarity of the power switch and reset switch wires, no dice.  Thanks anyway.

I even tried shutting down the computer without the NVIDIA card or other such add-ons that aren't essential for the computer to run.  Still, same problem.

I'm sending the motherboard back to Newegg for an RMA.  Hopefully the new board fixes things.  I have a feeling it will, since I read about this same problem with some other GIGABYTE motherboards, and a replacement fixed it for the users who were having trouble.

---

