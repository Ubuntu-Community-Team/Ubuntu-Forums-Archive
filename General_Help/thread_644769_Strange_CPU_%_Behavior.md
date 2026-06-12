---
title: "Strange CPU % Behavior"
date: 2007-12-19
forum: General Help
---

### Post by Antsh on 2007-12-19
I have notice that in the System Monitor that my CPU has strange usage. The CPU is utilizing hyperthreading, so the System Monitor sees two processors. Usage on one will go all the way up to 100% and averages around 50%, whereas usage on the second one is almost 0%. Suddenly, both of the them switch and now the second one is running at 50-100% and the first one is at 0%.

I've tried activating HT by adding "ht=on" to the grub config file, but it made no difference.

Does anyone have any ideas?:confused:

---

### Post by roaldz on 2007-12-19
> **Antsh said:**
> I have notice that in the System Monitor that my CPU has strange usage. The CPU is utilizing hyperthreading, so the System Monitor sees two processors. Usage on one will go all the way up to 100% and averages around 50%, whereas usage on the second one is almost 0%. Suddenly, both of the them switch and now the second one is running at 50-100% and the first one is at 0%.

I've tried activating HT by adding "ht=on" to the grub config file, but it made no difference.

Does anyone have any ideas?:confused:

It is hyperthreading already, but it´s switching the CPU-consuming thread from one ¨core¨ to another. You have to run multithread-optimised software to utilize multiple ¨cores¨. Most software just use 1 thread. Pity.

---

### Post by Antsh on 2007-12-19
Yes, I understand that, but should it be switching cores constantly and idling at 50-100% usage?

This problem just became noticeable in the past few days. Now it is interfering with the performance of the system.

Could disabling HT possible help?

---

### Post by roaldz on 2007-12-19
> **Antsh said:**
> Yes, I understand that, but should it be switching cores constantly and idling at 50-100% usage?

This problem just became noticeable in the past few days. Now it is interfering with the performance of the system.

Could disabling HT possible help?

First you should know what is exactly consuming your CPU power. I´m not sure how familiar you are with the terminal, but you could run ¨top¨ in the terminal.

---

### Post by Antsh on 2007-12-19
It appears xorg is the culprit.

---

### Post by Antsh on 2007-12-19
Well, I used Envy to uninstall the proprietary ATI drivers I was using. Then I set it up to use the old drivers and rebooted. Now the only thing I get is some IRQ 19 error and Xorg can no longer start.

---

### Post by roaldz on 2007-12-20
> **Antsh said:**
> Well, I used Envy to uninstall the proprietary ATI drivers I was using. Then I set it up to use the old drivers and rebooted. Now the only thing I get is some IRQ 19 error and Xorg can no longer start.

Make sure you have the ¨plug and play os¨ option enabled in your bios.

---

