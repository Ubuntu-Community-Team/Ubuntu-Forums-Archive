---
title: "Epiphany causes a restart of X"
date: 2008-03-30
forum: General Help
---

### Post by Maupertus on 2008-03-30
Hey everybody,

lately when I use epiphany, I get a crash of Epiphany, or worse, a reboot of X (as if I accidently used ctrl+alt+bckspc). In my syslog I get the following problems:
[I]
Mar 30 20:24:20 matthijs kernel: [30120.099106] npviewer.bin[20874]: segfault at 0000000000000010 rip 00000000f722e0f3 rsp 00000000ee52ee80 error 4

Mar 30 20:24:20 matthijs kernel: [30120.108502] npviewer.bin[20790]: segfault at 00000000f1ff7ed4 rip 00000000f6fb9b90 rsp 00000000f51a9310 error 4Mar 30 

20:24:23 matthijs kernel: [30122.184245] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.

Mar 30 20:24:23 matthijs kernel: [30122.184264] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode

Mar 30 20:24:23 matthijs kernel: [30122.184329] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode[/I]

Although I don't think the last 3 entries about my GPU have anything to do with it, I posted them because it's approx. the same time entry.

Now npviewer.bin is the flashviewer in the mozilla-linux flavour if I'm correct, but how can it cause such a severe crash? And can I fix it?

---

