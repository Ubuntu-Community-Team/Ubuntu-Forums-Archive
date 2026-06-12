---
title: "Doesn't detect hyper threading..."
date: 2005-10-20
forum: General Help
---

### Post by ymmotrojam on 2005-10-20
I'm having some issues with hyper threading... no errors, but it just simply doesn't see two cpus. I have tried what some have suggested and installed the linux kernel 2.6... smp, but that didn't do it either. Any help would be appreciated. If you need more info about my pc, just ask...

Thanks! :)

---

### Post by Casey on 2005-10-20
My dual core (AMD) processor shows up as 2 CPUs when I use the SMP kernel.  Is there any way to turn hyperthreading on or off in the bios?  If so my guess is that you might have it turned off.

Alternatively did you make sure that you are actually booting into the SMP kernel?

---

### Post by ymmotrojam on 2005-10-20
I haven't checked the bios, but that's because I know it was turned on before I switched from Windows (I can see two processors in Windows). Also, I was booted with the smp kernel.

---

### Post by duffydack on 2005-10-20
amend "ht=on" to your grub menu.lst

---

### Post by Dolphin on 2005-10-20
On a side note: Hyperthreading is next to useless.  I wouldn't care if Ubuntu is detecting it or not.

---

### Post by ymmotrojam on 2005-10-20
[quote=Dolphin]On a side note: Hyperthreading is next to useless. I wouldn't care if Ubuntu is detecting it or not.[/quote] I don't know if completely agree with this. I realize that dual-core is a more effective solution, but hyper-threading isn't bad... atleast in Windows I can assign a process to a particular virtual cpu via the task manager (aka... afinity). That way I can have a very intensive program running on one v-cpu, while it doesn't affect my browsing and email on the other v-cpu...

is hyper threading worth a whole lot? that's sort of a relative question/answer, but I would say that it is a whole lot better than just having a conventional processor. Should Ubuntu support it? why not? I'd say that if my computer has the ability to do something, the operating system should support it as much as possible. Even if I couldn't control which processes were on which v-cpu, it would atleast be nice if Ubuntu was able to automatically separate some of the system stuff on one v-cpu and my apps like firefox, gaim, etc on the other...

:)

---

### Post by Dolphin on 2005-10-20
I'm speaking from years of working with hardware and dealing with Intel's "Marketting is more important than innovation" policy.  I have yet to see hyperthreading be of any sort of benefit whatsoever.  I HAVE, however, seen it be a hinderance.  I've often recommended people turn hyperthreading OFF for certain tasks (ie games) as it performs better without it.  Trust me when I say that HT is all marketting and nothing else.  Intel feels very threatened by AMD so they like to market the hell out of crap features like this.

---

### Post by ymmotrojam on 2005-10-21
[quote=Dolphin]I'm speaking from years of working with hardware and dealing with Intel's "Marketting is more important than innovation" policy. I have yet to see hyperthreading be of any sort of benefit whatsoever. I HAVE, however, seen it be a hinderance. I've often recommended people turn hyperthreading OFF for certain tasks (ie games) as it performs better without it. Trust me when I say that HT is all marketting and nothing else. Intel feels very threatened by AMD so they like to market the hell out of crap features like this.[/quote]
well, I honestly don't care whether much of it's marketing or not. I have seen improvements on my end. And again I would like the operating system I use to be able to support my hardware as much as possible.

---

### Post by Darling on 2006-05-22
[QUOTE=Dolphin]On a side note: Hyperthreading is next to useless.  I wouldn't care if Ubuntu is detecting it or not.[/QUOTE]
Well, I dist-upgraded to dapper last week, and I noticed a huge speed improvement. I also saw 2 cpu's in the system monitor, and I'm quite sure that there was only one in breezy. I guess it's only now in Dapper that I'm really using the HT
So:
* Either hyperthreading really improves the speed or,
* Dapper is really a lot faster than Breezy.
I don't really care which one of the 2 is correct ;-)

---

### Post by bluenova on 2006-05-22
[QUOTE=Dolphin]On a side note: Hyperthreading is next to useless.  I wouldn't care if Ubuntu is detecting it or not.[/QUOTE]
This is totally untrue, everyone who I've read about installing the smp kernel version have seen their speed go through the roof after changing.

---

### Post by Cirrocco on 2006-05-22
whether or not you use HT should be decided on what you use your computer for.

1 task...HT= OFF   (gaming, movie/sound editing)
2+ tasks...HT= ON (surfin the net, checkin email, chatting, running a script all at once)

at work we have a server with dual xeons.  this server runs one app - that app is single threaded.  when HT is on you can plainly see on the taskman that 1 virtual CPU is cookin, while 3 are idle.  this means HT is a waste of time.  turning it off allocated 100% more CPU time to that 1 single threaded task.  processing speed improves.

HT doesn't equate to "twice as fast" because it halves the L1 and L2 cache (shared between virtual CPUs).  more practical benchmarks show approximately a 10% improvement (avg accross the board).

/read more tomshardware, tom is good for you

---

