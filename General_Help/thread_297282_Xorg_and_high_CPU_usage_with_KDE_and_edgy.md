---
title: "Xorg and high CPU usage with KDE and edgy"
date: 2006-11-10
forum: General Help
---

### Post by m.musashi on 2006-11-10
I just did the kubuntu-desktop install on my dual core laptop. I noticed that everything was very slow to respond so I ran top and I see that Xorg is running consistently at 45% or so. Even still, with a dual-core I should have lots of juice left but menus open slowly, dragging is choppy, etc.

I had a similar problem on my desktop and it seems that beagle was the problem. I uninstalled it and all was well. For whatever reason, beagle is not even installed on the laptop and it's xorg that is causing the problems.

I'm wondering if it's an nvidia driver issue. I used to have beryl installed but it seems broken (I get bash: beryl-manager: command not found if I try to run it). I've reinstalled the driver - it was installed with automatix2. I don't see any difference so I'm kind of at a loss. I did notice that the driver is nvidia-glx. I thought edgy didn't use glx. Could that be the problem? If so, how do I fix it?

Any ideas?

Thanks in advance.

---

### Post by WebDrake on 2006-11-11
I've been having similar issues with Xorg on Ubuntu Edgy.  I had assumed it was connected with the KTorrent problems described here:
[http://www.ubuntuforums.org/showthread.php?p=1725360](http://www.ubuntuforums.org/showthread.php?p=1725360)
... maybe these are symptoms of some more general underlying problems.

---

### Post by m.musashi on 2006-11-12
I couldn't get over the suspicion that it was a driver problem. I removed all traces of the driver and the restricted kernel bit and reinstalled everything following the beryl and edgy guide. I now get the nice new nvidia splash and xorg is back to 1 or 2%. So it looks like it was a driver problem after all.

However, beryl still won't run and I don't know what's up with that.

---

### Post by WebDrake on 2006-11-13
> **m.musashi said:**
> I couldn't get over the suspicion that it was a driver problem. I removed all traces of the driver and the restricted kernel bit and reinstalled everything following the beryl and edgy guide. I now get the nice new nvidia splash and xorg is back to 1 or 2%. So it looks like it was a driver problem after all.

Could you go through your process of fixing it for the rest of us, please? :)

---

### Post by oleoleole on 2006-11-13
Hm, I have the same problem with ATI-drivers, everything worked fine with nVIDIA-card and drivers, but since I don't like nvidia I decided to switch back to ATI with fglrx-drivers, after that Xorg uses about 10-15% CPU all the time. 

But I don't know if the drivers that causes the problem. Cause I was checking "KInfoCenter" under "CPU" and sometimes my 2,66GHz P4 CPU was at 333MHz, sometimes at 666MHz and 2,66GHz and different values. Same problem at the laptop, there it's switches between 1200MHz and 1600Mhz, it's a 1,6Ghz CPU.

Maybe it should act like this, but if not I guess that could be the problem?:p

EDIT:

I was recognizing another thing as well... If I do lots of things using CPU, or switch up and down a window (show/hide several times) the CPU frequenzy is moving up and things goes faster, If I don't touch anything, it's resting at 333MHz. If I do a little it moves up to 666MHz, and if I do it several times it moves up to 2,6GHz where it should be:p I don't know why it's acting like this, but there shouldn't be any power saveings enabled that I know about... unless they have done something awful in the kernel:P

EDIT:

After looking around in "modconf" I found out that "p4-clockmod" were enabled, that's why things worked slow here. If someone have same problem on laptops or something, it could be listed some modules in "kernel/cpu/cpufreq" ("modconf" is not pre-installed)

---

### Post by Velotix on 2006-11-13
> But I don't know if the drivers that causes the problem. Cause I was checking "KInfoCenter" under "CPU" and sometimes my 2,66GHz P4 CPU was at 333MHz, sometimes at 666MHz and 2,66GHz and different values. Same problem at the laptop, there it's switches between 1200MHz and 1600Mhz, it's a 1,6Ghz CPU.

Maybe it should act like this, but if not I guess that could be the problem?

Modern motherboards tend to do this automatically - it has nothing to do with Ubuntu. The main reason for doing it is that higher voltage and current running through a CPU shortens its life expectancy (hence why overclocking kills CPUs faster). Therefore, by dropping it down to lower speeds when idle - I'm guessing by dropping the CPU multiplier from 8x to 1x as opposed to actually messing with the clock speed when the CPU is active, which would be really stupid - it greatly increases your CPU's lifespan.

My parent's computer for example drops to 1GHz when idle and hits 2.4GHz max, and only exceeds 1GHz when doing something particularly intensive - there's probably a threshold set that tells the BIOS when to force the CPU's clock speed back up. It's possible that this power-saving trick was also unfortunately causing m.musashi's problems; if the system thought the action wasn't severe enough to warrant a high clock speed it was probably functioning at the crippled clock speed, which would rack up extra CPU cycles and make the user none too happy. If true, it probably also meant that the seemingly high CPU usage would have been solved simply by doing a more intensive task - an ironic solution but a solution nonetheless.

That said, I think it's possible to force the CPU to constantly run at max, but how exactly you do this I don't know and it probably is different for each motherboard: I'm not experienced with messing around in the BIOS. Like I say, though, that would probably drop your CPU's lifespan significantly:

My parents' computer is in fact an identical replacement of a faulty PC. That PC blew out two power supplies within a month and was constantly at maximum CPU speed. The onboard CPU temperature sensors reported a constant operating temperature of 64C. Make of that what you will.

---

### Post by oleoleole on 2006-11-13
> **Velotix said:**
> Modern motherboards tend to do this automatically - it has nothing to do with Ubuntu. The main reason for doing it is that higher voltage and current running through a CPU shortens its life expectancy (hence why overclocking kills CPUs faster). Therefore, by dropping it down to lower speeds when idle - I'm guessing by dropping the CPU multiplier from 8x to 1x as opposed to actually messing with the clock speed when the CPU is active, which would be really stupid - it greatly increases your CPU's lifespan.

My parent's computer for example drops to 1GHz when idle and hits 2.4GHz max, and only exceeds 1GHz when doing something particularly intensive - there's probably a threshold set that tells the BIOS when to force the CPU's clock speed back up. It's possible that this power-saving trick was also unfortunately causing m.musashi's problems; if the system thought the action wasn't severe enough to warrant a high clock speed it was probably functioning at the crippled clock speed, which would rack up extra CPU cycles and make the user none too happy. If true, it probably also meant that the seemingly high CPU usage would have been solved simply by doing a more intensive task - an ironic solution but a solution nonetheless.

That said, I think it's possible to force the CPU to constantly run at max, but how exactly you do this I don't know and it probably is different for each motherboard: I'm not experienced with messing around in the BIOS. Like I say, though, that would probably drop your CPU's lifespan significantly:

My parents' computer is in fact an identical replacement of a faulty PC. That PC blew out two power supplies within a month and was constantly at maximum CPU speed. The onboard CPU temperature sensors reported a constant operating temperature of 64C. Make of that what you will.

Well, for me this was "powernowd"-"problem" I just removed it, and the speed is stuck at where it should be, at 2,66GHz at the desktop, and 1,6GHz at the laptop. For me this acceleration was WAY to slow. So I prefer a dead CPU after some years, when it's old and useless anyway. And run with no loss (or less as possible) when I still have it:p

---

### Post by m.musashi on 2006-11-13
> **WebDrake said:**
> Could you go through your process of fixing it for the rest of us, please? :)

Uh. If I wasn't such a hack I could. Basically, I did sudo apt-get remove and the names of the kernel-restricted-modules, nvidia-glx and maybe one or two others. Sorry, it's been a couple days and I didn't take notes.

---

### Post by WebDrake on 2006-11-15
> **m.musashi said:**
> Uh. If I wasn't such a hack I could.

Never mind.  Thanks anyway! :)

---

