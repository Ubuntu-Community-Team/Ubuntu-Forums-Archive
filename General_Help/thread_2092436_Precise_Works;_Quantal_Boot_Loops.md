---
title: "Precise Works; Quantal Boot Loops?"
date: 2012-12-07
forum: General Help
---

### Post by Xplorer4x4 on 2012-12-07
I have a very old Intel Celeron(Pentium based - if memory serves me right) laptop with a 30GB HDD and 250 *MB* of RAM and a Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP for video out. I have installed Lubuntu Precise, using the Alt CD image, and it runs pretty good given the lackluster specs. However, if I install Quantal from either the Alt CD image, or upgrade through a working Precise install using "sudo do-release-upgrade -d" the system simply goes in to a sort of boot loop. The loop I am referring to, starts booting, the desktop cursor appears over a black screen, and then it does a partial reboot, and kills what bit of a running desktop session there is and runs some checks before repeating this over and over. I tried using boot-repair disc to set the vga option. The lbunutu install cd uses vga=788, but boot-repair only gave me the option of a lower value. I tried the automatically chosen variable and tried booting lubuntu 12.10. No luck. So I edited the vga=XXX option manually and tried 788. Still Quantal boot loops.

---

### Post by SteveDee on 2012-12-12
Did you get any warnings or other messages about PAE support during install or upgrade?

I would expect that to be an issue with the hardware you describe (I can't run 12.10 on this Pentium M powered Dell D600).

---

### Post by Xplorer4x4 on 2012-12-12
Steve, thanks for a reply! No I get no warnings of any kind. Just the sort of hot reboot attempt, almost similar to a log out rather then a full on hard reboot.

When you say you are unable to run Quantal on your old machine, what do you mean? The driver support is not there?

---

### Post by SteveDee on 2012-12-12
> **Xplorer4x4 said:**
> ...When you say you are unable to run Quantal on your old machine, what do you mean?...

Its to do with lack of non-PAE support in 12.10

See: [http://ubuntuforums.org/showthread.php?t=2073327&highlight=pae](http://ubuntuforums.org/showthread.php?t=2073327&highlight=pae)
...and...
[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

...but maybe if you didn't see a message, that's not your problem.

---

