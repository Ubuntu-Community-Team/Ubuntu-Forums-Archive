---
title: "virtual box and performances"
date: 2014-01-27
forum: General Help
---

### Post by jsabina1 on 2014-01-27
Hi everybody,
I have ubuntu 13.10 installed on a lenovo t510 with i7 quad and 8 GB of ram.
I have to use windows 7 for some apps, so I installed it on virtual box.
I gave 2048Mb of RAM and 1 CPU.

The system seems to be working well, but the computer is heating a bit more and I see from top that the CPU usage from virtual box is around 60%  and memory 28.4%

Does it mean it use all the cores?
there is some way I could configure it better?

thanks

---

### Post by sudodus on 2014-01-27
I would give up to half of the CPUs and RAM to the virtual machine, if that is necessary for it to run well. But don't run it except when you really need it.

I can't tell you why it is using 60% CPU usage, when you have only given it one CPU. Maybe the guest OS can use one CPU only, but the virtual machine itself uses other CPUs. Let us hope someone who knows will read this and tell us :-)

---

### Post by DuckHook on 2014-01-27
<sigh> Windows VMs...

I don't use W7 anymore, so the following is my experience in XP and Vista. Can't see W7 being much different. Next time VM is running, look in Win task manager and note process that is eating up CPU cycles. It is likely to be *svchosts*, which is unhelpful because it could be just about anything. The usual culprits are:

1. MS auto update which is kludgy, crufty, bloated, temperamental, full of memory leaks and generally awful. This one is the worst of the lot and not much you can do unless you forego updates (not a good idea, especially with Windows).
2. Antivirus which will download, update, scan entire file structure and do triple backward saumersault with two and a half twists before settling down.
3. Automated housekeeping processes like file database updates, defrag, etc.
4. Other app updates like flash, java, Adobe, iTunes, HP, etc that all fight to check and download their updates right after boot up.
5. Dozens of other possibilities including malware.

1-4 is just the tip of the iceberg. It is notoriously hard chasing down system problems/memory leaks in Win because it is designed to be opaque and thus maintain the illusion of "ease of use" by conflating ignorance with "user friendliness".

What to do:

1. See if VM settles down after 20 minutes. If it does then it is likely 2-4. If it does not, then it is more likely 1 or 5. Proceed to step 2.
2. Using Task Manager, kill the rogue *svchosts*. Make sure you select the right one. In a typical Win environment, there can be dozens. Make sure it's the one eating up your CPU cycles. Note what functionality breaks (I've had experience from sound system to network). This doesn't mean that the broken system is the culprit, but it's a start to diagnosing and Googling for the answer.
3. If system settles down for 10 seconds only to bog down again with another *svchosts* automatically launched, then this indicates a system service (which automatically launched another rogue process). The culprit in this case is now more likely to be #1. You can go into Win system services and disable them one by one to nail down the culprit through process of elimination. Start with auto updates.
4. You should also *ps -eF* and *top* your host to see if you see anything unusual, though you are unlikely to see anything useful. Everything happening inside the VM process is unlikely to be reported in much detail to the host OS.

Further steps will have to depend on other forum members. It's been years since I've had to squash a Win problem and I'm now lousy at it.

**TIP** I've found that when it comes to Win OSes, if you end up solving the problem or resorting to a fresh install that actually behaves, always keep a snapshot of that well-behaved version on your VM so that you can roll back to it when something (invariably) goes bad. Another strategy is to copy the VM to a NAS or external HDD for a pristine start. I use both strategies. Windows is the only OS for which I find the need to do this, and it's saved my butt on numerous occasions.

BTW, I do want to thank you for reminding my how much I'm NOT missing by no longer having to wrestle with MS bugbears.

---

### Post by jsabina1 on 2014-01-29
thanks..
I disabled few services (search indexer and spooler service).. I've put the minimal settings, no "fancy" effects.. disabled windows update..
let's see.. it looks like now is calmer..
let's hope..
I need windowz just sometimes for few stuff, but it's really annoying that use so much resources!!

---

