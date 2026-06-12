---
title: "Patchy Edgy Performance"
date: 2006-11-24
forum: General Help
---

### Post by craftybones on 2006-11-24
Hello all,

I have had some major issues with the following setup:

AMD64 3700
1Gb RAM
Nvidia GeForce 6100 (onboard)
Nvidia nForce (onboard sound)
Gigabit motherboard

Edgy i386. yes I know I should probably install the 64 bit version, but for the obvious reasons I chose what I chose.

Edgy firstly took AGES to install. It took about 4 hours. I have no clue why. It was just weird. It would just sit there chugging away for hours not moving a bit and then move again slowly...

Once installed, nVidia was a slight mess to configure, but got that configured. However, things would crash and hang for no apparent reason. I had Synaptic running and my system just wouldn't respond. I had to reboot. Then once the nvidia drivers were installed, I had firefox, synaptic and a terminal open, and again same problem.

I know RAM might be a possible issue, however, I already run XP on the machine and haven't faced any hang time.

I am currently going to revert to Dapper, but does anyone have any ideas? Is it a kernel level issue? I couldn't even execute top, it would just hang. At one point, ls took 2 minutes or so to return to prompt.

Would like some feedback.

craftybones

---

### Post by craftybones on 2006-11-24
Oh forgot to mention:

two hard drives:

1) Maxtor 80 G some arbit model I no longer remember

2) Maxtor SATA 300G another arbit model I no longer remember.

Ubuntu is installed on the 300G drive on a 150G partition. the other 150G is a fat partition with a ton of data.

Thank you,

craftybones

---

### Post by craftybones on 2006-11-25
Interesting update:

I tried installing 6.06 over the existing 6.10 installation and had the same problems. took forever to install, so I aborted it.

I thought about it some more, and I think it has something to do with my SATA drive. So on a hunch, I installed on my non SATA drive. And it works like a charm. No hangups.

My guess is that something is wrong with driver support for the nvidia SATA  controller. Its an nforce 430, and I am going to do some research on whether I can fix this.

Thanks,

craftybones

---

### Post by incubus on 2006-11-25
I'm very sorry for that.  It is, however, an interesting case.  I would not suspect the SATA support.  So if you run a Live CD, without touching the hard drive, everything runs smoothly? (assuming you're using an IDE connection for the cd/dvd drive).

Can you run top now with this non-SATA hard drive? Is everything else working as expected?

good luck,
incubus

PS: You said "revert back to Dapper".  So was your computer working fine before that?

---

### Post by craftybones on 2006-11-25
Hello incubus,

Yes, everything runs smoothly if I ran the LiveCD.

Everything also ran really smoothly once I switched my SATA controller from the onboard nForce to a PCI SATA controller. 

Everything *almost* works as expected. I don't suspect there are any more issues, however, when I "shut down" my machine, it doesn't shut down entirely, it manages to do everything, but I find the fan still running and the processor still up, however nothing else is up(blank screen etc).

Yes "revert back to Dapper" meant that I did have Dapper installed. It was on my non-SATA drive however. The Sata controller I had was an nForce 430 which is not supported. So the generic driver just didn't seem to work. I should perhaps file a bug.

> **incubus said:**
> I'm very sorry for that.  It is, however, an interesting case.  I would not suspect the SATA support.  So if you run a Live CD, without touching the hard drive, everything runs smoothly? (assuming you're using an IDE connection for the cd/dvd drive).

Can you run top now with this non-SATA hard drive? Is everything else working as expected?

good luck,
incubus

PS: You said "revert back to Dapper".  So was your computer working fine before that?


Craftybones

---

### Post by craftybones on 2006-11-25
Also incubus,

The following, unrelated, doesn't work if you want to take a look.

[http://www.ubuntuforums.org/showthread.php?t=306735](http://www.ubuntuforums.org/showthread.php?t=306735)

craftybones

---

### Post by incubus on 2006-11-25
craftybones

That's really unfortunate and it deserves a bug complaint. Having a new hard drive and not being able to use it is torture.

Now with this thing that not even shutdown is working properly, it points to lack of support for your south bridge chipset. If I was in your situation, I would start to google around and even try other forums (Gentoo, for example), to see if other people have had the same issue.  You may need to apply some patches and recompile your kernel.  Hopefully, there will be an easier solution.

Do file a bug complaint. It's only with your help that the developers will hear about the problem.  : )

Good luck.
incubus

---

### Post by craftybones on 2006-12-01
Any solutions on this anyone? I am lost. THis is what I have tried so far:

1) install dapper fresh on my IDE drive

This worked, for a while, and then the problems started cropping up after the second boot or so. SATA wouldn't mount. Same issues persisted. I haven't been able to find anything about it on the web. The install itself was normal however and didn't take 4 hours long

2) install edgy on ide drive:

SAme as above

I am at my wits' end and SERIOUSLY require help here. I don't know what to do. What's strange is Debian Etch works great on it!

craftybones

---

