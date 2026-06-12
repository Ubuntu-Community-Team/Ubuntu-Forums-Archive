---
title: "GRUB Problem"
date: 2008-03-07
forum: General Help
---

### Post by madara_sama on 2008-03-07
Hi, I just tried...
When Feisty Fawn installed, Grub was include into MBR automatically.
It worked well, if we just install it in single OS. But how about dual OS, triple OS, and so on...
I have tried it. And I figured that some crash appeared if we try that. By default, Ubuntu shows about 3 lines, for generic, recovery, and memtest. It's fine, in a short time. Suddenly, just when I really need to change, some trouble came to me. System told me that [COLOR="Red"]BOOT FAILURE[/COLOR].
Fixmbr won't work for this. Live CD too, sometime it works, sometime no. What is this caused by? How to solved it?

If I remove ubuntu, I won't. But no failure appeared, really worked well.

---

### Post by dcstar on 2008-03-07
> **madara_sama said:**
> Hi, I just tried...
When Feisty Fawn installed, Grub was include into MBR automatically.
It worked well, if we just install it in single OS. But how about dual OS, triple OS, and so on...
I have tried it. And I figured that some crash appeared if we try that. By default, Ubuntu shows about 3 lines, for generic, recovery, and memtest. It's fine, in a short time. Suddenly, just when I really need to change, some trouble came to me. System told me that [COLOR="Red"]BOOT FAILURE[/COLOR].
Fixmbr won't work for this. Live CD too, sometime it works, sometime no. What is this caused by? How to solved it?

If I remove ubuntu, I won't. But no failure appeared, really worked well.

Tell us **exactly** what you want to boot, and the output of these commands:

```
fdisk -l
cat /boot/grub/menu/lst
```

---

### Post by madara_sama on 2008-03-08
no, that won't work. That message about "System Failure, please insert system disk"
So, I can't boot any OS. No Grub appeared.

---

