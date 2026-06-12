---
title: "[Xubuntu] Not SUCH a lightweight!? (or am i doing s.t. wrong?)"
date: 2007-01-06
forum: General Help
---

### Post by sorabsuperstar on 2007-01-06
So what i have here is an old machine:
MoBo: Matsonic MS-5120
CPU: AMD-K6II 300 Mhz
RAM: 128 MB SDRAM
Graph: ATI - 3D Xpression+ (Mach64)

In its better days, Windows 98 and then 2000 used to rum on this machine. PErformance under 2K was acceptable, as far as i remember.
Later the machine was used as a router under Suse 6.x.. KDE1 was installed and worked quite well.

Now i heard, that Xubuntu was such a lightweight. 128 MB was enought. A P1 would do.......
So i installed it on the machine. But the result is more than disappointing.
It is sooooo slow, especially when (the so called lightweight) XFCE is running.

Examples:
With XFCE running, the machine cant even prperly replay a mp3. Its choppy and distorted, because there are not enough System resources (No, it is not the sounddriver: With failsafe-login - without XFCE - mplayer replays mp3 properly, but barely i guess)

Another example: When loading the example-doc-file on the Ubuntu-CD "oo-derivatives.doc" with Ami-Pro, it is hardly possible to edit the file, cause that one page of text with two embedded png-graphs is puttung the X-server to fully load (i think its the xserver, CPU-Average-Load stays at least under 1.0)

So to decide whether deleting that xfce-thing again (since it does not make sense that way) or troubleshoot, i need to know, if maybe it is just the way that XFCE is not such a lightweight as announced on the Xubuntu-page. So that the machine is not good enough to run it.
Or is iot supposed to run faster on that machine, so there must be something wrong?

Does anyone use the same Graphiccard? Is there a trick to observe wth it?

---

### Post by ajgreeny on 2007-01-06
Another example: When loading the example-doc-file on the Ubuntu-CD "oo-derivatives.doc" with Ami-Pro,
Did you mean *abiword* rather than *ami-pro,* which is the lotus smartsuite word processor?  I'm still surprised but have to say that the compatibility between *lotus amipro* and doc files was pretty poor when I was using it a long time ago, and some people using *MSword* found it difficult to open doc files produced in *ami-pro.*  I don't know if this has any bearing on your problem, but thought it worth saying, just in case.

---

### Post by theslut on 2007-01-06
who gives a damn. go and spend a few hundred (insert currency) here and get an upgrade :P

---

### Post by sorabsuperstar on 2007-01-06
Sure, i mean abiword, not Ami-Pro. Sorry

While i am not so sure anymore that it is because of the x-server.
When i log in to the machine from my (rather up to date) Kubuntu-Machine with x-output to that machine, it is even slower (actually not-useable) And that cannot have anything to do with the local xserver or Graphiccard of the Xubuntu-box.

So i am not yet asking for solutions. Just please tell me,  if anyone has Xubuntu running with acceptable performance on a comparable machine?????

---

### Post by MetalMusicAddict on 2007-01-06
With those specs Id recommend [Fluxbuntu]("http://fluxbuntu.org/").

---

### Post by kerry_s on 2007-01-06
Dsl linux-> [http://www.damnsmalllinux.org/index.html](http://www.damnsmalllinux.org/index.html)

Your not going to get a pocket rocket with those specs. Don't expect miracles.

---

### Post by BLTicklemonster on 2007-01-07
fluxbuntu for sure.

Or just load fluxbox or icewm on there if you don't want to go full bore and redo the hard drive. There are several threads here on how to set either of them up.

---

### Post by sorabsuperstar on 2007-01-07
[QUOTE=several users]fluxbuntu for sure.

[/QUOTE]

Thanks guys, going to try that.

Was thinking about just putting mwn onto it.
But if there is a ready-made ubuntu Distro wrapped around fluxbox, i'll go for it! :D 

Cheers

---

### Post by MetalMusicAddict on 2007-01-07
Fluxbuntu is currently under heavy development and the next release will rock even harder. :)

---

