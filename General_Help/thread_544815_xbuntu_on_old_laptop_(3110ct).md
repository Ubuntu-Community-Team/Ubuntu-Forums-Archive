---
title: "xbuntu on old laptop (3110ct)"
date: 2007-09-06
forum: General Help
---

### Post by Lanrat on 2007-09-06
Hi, i have a old Toshiba portege 3110ct laptop, the specs are: 300mhz P2 cpu, 6gb hd, 128mb ram, 800x600 display, and thats just about it. i like it because it is so small and portable.it previously had windows 2k on it and it worked just fine (except it begin a little slow, but its a slow comp) but i wanted something more than just windows so i put xubuntu on it, the install took about 7 hrs but it did install. but here are my problems.

1. it takes too long to boot. win 2k took less than a minute to boot on this laptop, xubuntu takes about 4 minutes. (same with shutdown)

2. no support for pnp dock. (it had a dock that has some more prts on it like ps2, audeo, usb, com, lpt, cga. and the dock also has a network card in it) in windows 2k i could plug it in and out while using the comp and it would just work. in xubuntu i need to reboot first.

3. xubuntu dosent have support for my wifi card. i use a gigfast wf721-aex wireless card, and a gigafast wf741-uic both work fine in win (duh) and on normal ubuntu the wf721-aex works, but i haven't tried the  wf741-uic. i would prefer to get the wf741-uic working as that is the 1 i would like to use but eather is ok.

and thats it, i really love linux and would love to have it on this laptop. i tend to use it for basic web browsing (firefox), IMi, and if i can avi playback (win 2k with vlc could do this but the quality was really bad, probably due to the slow possessor, but if i can get this working in linux :popcorn: ) also if anyone could recommend me with another disterio to install on this please let me know. (do not tell me about dsl, it does even worse on this comp)

Thanks!

---

### Post by merlinus on 2007-09-06
Have you tried zenwalk?

-merlin

---

### Post by Lanrat on 2007-09-06
i looked at zenwalk, it dosent look like it would run on that old of a computer any better. would it?

---

### Post by merlinus on 2007-09-06
Zenwalk GNU/Linux is optimized for the i686 instruction set, but backward compatible with i486.  These are the minimal hardware requirements to run Zenwalk in Xwindow mode, with correct performance  (some lower configs work - ie : PII - , but might be slow) : 
 [LIST]
[*]Pentium III class processor
[*]128 Mb RAM
[*]2Gb HDD[/LIST]

-merlin

---

### Post by Lanrat on 2007-09-06
what version should i download? Standard or core?

---

### Post by kerry_s on 2007-09-06
a custom install would be the best thing for those specs, i would go with debian, as they support the old stuff, but ubuntu if your just starting off.

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by Lanrat on 2007-09-06
i dont really need ubuntu, so il also try debain.

---

### Post by kerry_s on 2007-09-07
> **Lanrat said:**
> i dont really need ubuntu, so il also try debain.

[http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-businesscard.iso)

when it gets to package selection uncheck all of them, that will give you just the base.
login as root
apt-get install xorg gdm synaptic fluxbox rox-filer leafpad dillo iceweasel
reboot(ctrl+alt+delete)
choose fluxbox in the session menu and login
you can use synaptic to get what ever else you need.

---

### Post by Lanrat on 2007-09-07
i will try this.

---

