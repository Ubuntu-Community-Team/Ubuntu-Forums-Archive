---
title: "XSane ScanMaker 3800"
date: 2006-08-09
forum: General Help
---

### Post by Paul41 on 2006-08-09
I have a ScanMaker 3800 scanner which according to the Sane website this scanner is not supported ([http://sane-project.org/unsupported/microtek-scanmaker-3800.html](http://sane-project.org/unsupported/microtek-scanmaker-3800.html)).  When I open XSane I just get a dialog box that says > No devices available.

I ran the following command:
```
scanimage -L
```
and the output was:
> No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).


Is there any way that I can try to use another scanner that may be close to mine to see if it works?

---

### Post by alienexplorers on 2006-08-17
Try going into Synaptic and lookup sane.  Find "libsane-extras" and select it and apply it.  Restart computer and try xsane again.

---

### Post by Paul41 on 2006-08-17
> **alienexplorers said:**
> Try going into Synaptic and lookup sane.  Find "libsane-extras" and select it and apply it.  Restart computer and try xsane again.

Thanks for this, I will try it as soon as I get home this afternoon.

---

### Post by Paul41 on 2006-08-17
I installed libsane-extras but still have the same problem.  Any other ideas?

---

