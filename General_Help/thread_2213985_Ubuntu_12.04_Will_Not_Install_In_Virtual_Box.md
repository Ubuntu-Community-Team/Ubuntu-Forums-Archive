---
title: "Ubuntu 12.04 Will Not Install In Virtual Box"
date: 2014-03-29
forum: General Help
---

### Post by Vannyi on 2014-03-29
I'm trying to install Ubuntu 12.04 in Virtual Box, but each time, right after booting from CD, I get the message "This kernel requires an x86-64 CPU by only detected an i686 CPU. Unable to boot - please use a kernel appropriate for your CPU"


My host is a Windows 7 Ultimate PC,l 64-bit


I have tried to install both Ubuntu 12.04 32-bit and Ubuntu 12.04 64-bit and get the same message. I have also tried updating Virtual Box and am now running 4.3.10 r93012.


Any thoughts?


Thank you

---

### Post by TheFu on 2014-03-29
Did you select "ubuntu" or "ubuntu amd64" when specifying the guest OS type?
I could be off with the exact name, but there is definitely a 64-bit selection.

---

### Post by ajgreeny on 2014-03-29
And do you have hardware virtualisation enabled in your BIOS as it is needed for 64 bit guest OSs.

---

