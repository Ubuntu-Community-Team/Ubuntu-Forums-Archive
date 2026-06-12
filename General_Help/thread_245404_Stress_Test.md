---
title: "Stress Test?"
date: 2006-08-27
forum: General Help
---

### Post by sunrex on 2006-08-27
can i stress test my cpu and ram in linux? if so how? i want to make sure its stable running at 100%

---

### Post by peabody on 2006-08-27
If you go to the grub menu by hitting escape just before boot, there should be an option to run memtest86 which is a RAM stress tester.  It's no replacement for a real hardware based ram tester, but if RAM is especially bad it should manage to tell you.  You do need to let it run for quite some time for it to be a fair test, and you can't use your system while it's doing it, so you may wish to do this as an over-night thing.  As for the CPU, I'd just see how long you can keep the CPU running at 100%.  Run a quake 3 demo with all detail turned up, etc.

---

### Post by limaunion on 2006-08-27
I've never used it but there's a program called cpuburn, maybe that's what you're looking for.

$apt-cache show cpuburn

Description: a collection of programs to put heavy load on CPU
 CPUburn is a collection of programs to put heavy stress on CPU.
 These programs are designed to load x86 CPUs as heavily as possible
 for the purposes of system testing.

---

### Post by sunrex on 2006-08-27
I guess it cant be that stable since gmod (hl2 mod) keeps crashing in wine, it says its using up 92% of my 2.5ghz cpu, but if gmod crashed wouldn't wine crash as well? this is where i have problems, since it just exits to steam

---

### Post by peabody on 2006-08-27
> **sunrex said:**
> I guess it cant be that stable since gmod (hl2 mod) keeps crashing in wine, it says its using up 92% of my 2.5ghz cpu, but if gmod crashed wouldn't wine crash as well? this is where i have problems, since it just exits to steam

Aw heck, instability in Wine's kind of a fact of life.  I'd try cedega and their support.  And I believe more than one process within wine is being run which is why HL2 is going bye-bye but the steam interface isn't.

---

### Post by sunrex on 2006-08-27
Cedega? after that sucky demo.. no thanks.

---

