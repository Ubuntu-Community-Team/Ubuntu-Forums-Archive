---
title: "Ubuntu freezes every 10sec"
date: 2017-02-24
forum: General Help
---

### Post by fddc on 2017-02-24
Hey,

I tried to install ubuntu and I have freezes that appears every 10sec and last 10sec and so on, I can't use ubuntu... During these freezes mouse/keyboard input/display are froze. It freezes on ubuntu live, ubuntu 14.04, 16.04 and 16.10 installed. I tried to install the last graphics drivers but nothing worked.
No freeze when I launch ubuntu in safe mode and significantly less freezes when I use firefox without clicking on the tool bar.
My computer is an acer Aspire S5-371-565N, i5 6200U, intel HD Graphics 520, 8gb ram.

Do you have any idea to solve my issue?

Thanks

---

### Post by Perfect Storm on 2017-02-24
Try add this to grub:
```
sudo nano /etc/default/grub
```
change:
**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"**
to
**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_idle.max_cstate=1"**

save= <ctrl>+<o>
exit= <cttrl>+<x>

It workd for my laptop.

---

### Post by fddc on 2017-02-25
I changed and launched update-grub that but my computer keeps freezing

---

### Post by ortermagic on 2017-02-25
what keyboard are you using?  save=ctrl+s on mine

---

