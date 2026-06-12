---
title: "Setting up a local server (dd-wrt) to cache ubuntu deb files"
date: 2014-03-18
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2014-03-18
I am wondering if i can put a flash drive in my dd-wrt router and have it use that to cache the archives i would download to /var/cache/apt/archives
i know there is a package for this in the Ubuntu repos, though i have never used it.
i commonly test installs on different HDDs on my desktop, sometimes in virtualbox
i figure i can speed it up a bit and save bandwidth by having the files locally stored at my router
```
root@WZR-300HP:~# cat /proc/cpuinfo 
system type        : Atheros AR7242 rev 1.1 (0x1101)
processor        : 0
cpu model        : MIPS 24Kc V7.4
BogoMIPS        : 265.42
CPUClock        : 400
wait instruction    : yes
microsecond timers    : yes
tlb_entries        : 16
extra interrupt vector    : yes
hardware watchpoint    : yes, count: 4, address/irw mask: [0x0000, 0x0c08, 0x0b30, 0x0778]
isa            : mips1 mips2 mips32r1 mips32r2
ASEs implemented    : mips16
shadow register sets    : 1
kscratch registers    : 0
core            : 0
VCED exceptions        : not available
VCEI exceptions        : not available
```

---

### Post by TheFu on 2014-03-18
Not really good for a router, but you can setup apt-cacher-ng on any Ubuntu box. Turns out it works about 60% of the time where "cache hits" happen. You can mirror the repo, but there is so much there that is never used, that I didn't think it was worthwhile.

```
$ du -sh *
553M    apt
3.4G    apt-cacher-ng
101M    apt-xapian-index

```

---

### Post by pqwoerituytrueiwoq on 2014-03-18
that would require another computer, or a raspberry pi at the very least
i figure if my router can filter ads it can cache deb files from ubuntu.com, getdeb.net, and lauchpad.net to usb flash drive, so when i do a few installs everything is right there

---

### Post by TheFu on 2014-03-18
Not really the same thing, but perhaps you can look at the apt-cacher-ng code and make it work on your router?
Or perhaps something like cobbler would be worth checking out?

---

