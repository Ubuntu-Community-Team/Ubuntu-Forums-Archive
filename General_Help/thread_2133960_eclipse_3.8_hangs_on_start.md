---
title: "eclipse 3.8 hangs on start"
date: 2013-04-09
forum: General Help
---

### Post by koma77 on 2013-04-09
After upgrading to 13.04, my eclipse 3.8 hangs while showing the startup splash (it hangs at "starting workbench").

I'm using openjdk 7 and I have Android SDK installed.

I get no printouts in the console, nor does starting eclipse with --cleanup do any difference.

Any ideas?

---

### Post by koma77 on 2013-04-09
I attached with strace to the java process that took 100% CPU.

Basically it does this over and over again:
[pid 28738] poll([{fd=17, events=POLLIN}, {fd=16, events=POLLIN}, {fd=111, events=POLLIN}], 3, 0) = 0 (Timeout)
[pid 28738] recvfrom(16, 0x7f27f827a784, 4096, 0, 0, 0) = -1 EAGAIN (Resource temporarily unavailable)
[pid 28738] poll([{fd=17, events=POLLIN}, {fd=16, events=POLLIN}, {fd=111, events=POLLIN}], 3, 0) = 0 (Timeout)
[pid 28738] recvfrom(16, 0x7f27f827a784, 4096, 0, 0, 0) = -1 EAGAIN (Resource temporarily unavailable)

---

### Post by rlgoodman on 2013-06-25
Any solution to this? I have the same problem, but no Android SDK.

---

### Post by cariboo on 2013-06-25
Moved to General Help. as this is about Raring, and not Saucy.

---

### Post by koma77 on 2013-06-25
> **rlgoodman said:**
> Any solution to this? I have the same problem, but no Android SDK.

I had to uninstall the Ubuntu package and install Eclipse from the Eclipse website...

---

### Post by rlgoodman on 2013-06-25
I wound up removing my $HOME/.eclipse/.metadata/ directory and that seemed to solve it, at the cost of losing my projects and other setup.

Thanks

---

