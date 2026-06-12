---
title: "Ubuntu Mate is with distorted images."
date: 2016-03-23
forum: General Help
---

### Post by lynx6 on 2016-03-23
Hallo everybody.


I have a screen image problem that distorted and totally lock on *Ubuntu Mate 15:10* (32-bits) using Kernel 4.2
This problem was not happening in *Ubuntu Mate 15.04* to Kernel 3.19
The computer has a video chipset *Intel 945GC* Express.
The image is attached.


How can I solve this problem.
Thank you.

---

### Post by QDR06VV9 on 2016-03-23
Try booting to the older Kernel 3.19 to see if that changes that behavior.
To boot to an older kernel when you see grub(Boot Options)  select Advanced and arrow down to the 3.19 kernel.

---

### Post by lynx6 on 2016-03-23
Ubuntu Mate 15.10 comes with Kernel 4.2
I do not have the Kernel 3.19 installed on your computer.

Versions installed are:
4.2.0-16-generic, 4.2.0-17-generic, 4.2.0-18-generic, 4.2.0-22-generic, 4.2.0-30-generic

---

### Post by QDR06VV9 on 2016-03-23
> **lynx6 said:**
> Ubuntu Mate 15.10 comes with Kernel 4.2
I do not have the Kernel 3.19 installed on your computer.
I think you meant your computer..as mine has the 3.19.0-30 kernel.
Long story short just install an older kernel in synaptic with headers associated with the same version of the kernel you are installing. 
Or maybe check that the headers are also installed for the 4.2 kernel.
Ok boot to an older kernel than the one you are seeing the tearing in.

---

### Post by lynx6 on 2016-03-28
> I think you meant your computer..as mine has the 3.19.0-30 kernel.
Long story short just install an older kernel in synaptic with headers  associated with the same version of the kernel you are installing. 
Or maybe check that the headers are also installed for the 4.2 kernel.
Ok boot to an older kernel than the one you are seeing the tearing in.

Thanks for the tip.
I did not know that at Synaptic could install old kernel.
Thank you.

---

