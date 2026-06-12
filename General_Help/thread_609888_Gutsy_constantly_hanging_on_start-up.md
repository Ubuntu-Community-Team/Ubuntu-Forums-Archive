---
title: "Gutsy constantly hanging on start-up"
date: 2007-11-11
forum: General Help
---

### Post by bootsbradford on 2007-11-11
Over the past few days I am having a problem with gutsy on start-up. 

The grub menu will come up and the latest kernel will be launched. However, more often than not at the moment, the computer will 'hang' or 'jam' as the progress bar fills up on the ubuntu start-up screen. I will need to hold down the power button to power off. If I then re-start again, it is OK.

This happened very rarely before but now it seems to happen almost every time. Is there anything I can do to resolve this problem?

---

### Post by mscdex on 2007-11-11
I have the same problem but I am on Xubuntu 7.10. I run it on my laptop and it has been working just fine and was just using it the other night. However when I tried to start it up this morning, the same thing happened to me: the progress bar became stuck every time at the same spot and was hung up on something. The last line that is always reported by the console is: "kinit: No resume image found, doing normal boot." 

I am running kernel 2.6.22-14-generic if that helps.

---

### Post by ^^Snoop^^ on 2007-11-11
I had problems on boot-up using Feisty and Gutsy, adding IRQPOLL into the menu.lst fixed that though :)

---

### Post by bootsbradford on 2007-11-11
> **^^Snoop^^ said:**
> I had problems on boot-up using Feisty and Gutsy, adding IRQPOLL into the menu.lst fixed that though :)

Is it literally a case of just adding that one word? Does it matter where it comes in the file?

---

### Post by bootsbradford on 2007-11-13
This is getting a little silly - and all too predictable...

From cold, I will attempt to boot the pc and it will hang as soon as it tried to load the kernel. I will then instantly reboot a second time, and it will load fine. I don't understand!!

How can I avoid having to reset it so often?

---

### Post by bootsbradford on 2007-11-15
anybody? please...

---

### Post by bootsbradford on 2007-11-16
bump

---

