---
title: "Ubuntu 12.10 reboot after (I believe) processor error"
date: 2013-02-26
forum: General Help
---

### Post by nanoVapor on 2013-02-26
Hi everyone!

I've looked all over the forum and Google but couldn't find anything.

Every day my ubuntu 12.10 reboot with a kernel error (I think.. Sometimes it reboots and I away from computer). The messege seems to be about some problem with the processor. I'm looking for the logs, hoping that there is anything there, but I don't know where to search...

My PC config is:

i5 2500k @ 4.5Ghz + Hyper 212 Plus (push'n'pull) | AsRock z68 Extreme4 | 4x4Gb DDR3 Corsair Vengeance | 2x 500GB WD Caviar Green (RAID0) | Corsair VX550W | ATI 4870 1Gb DDR5

Yes, it's overclocked by BIOS configuration. Using Win 7 and Win 8, I have no problems! The computer stay on for days, with heavy use and no reboot.

With Ubuntu, even If I'm not using it, it reboots. :(

Can anyone help me? Is there any log that save erros by any hardware?

Sorry my bad english.

---

### Post by CharlesA on 2013-02-26
Check /var/log/kern.log and /var/log/dmesg

If there was a kernel panic it could also be recorded in the syslog.

---

### Post by nanoVapor on 2013-02-26
Thanks!

I'm looking inside this logs, but I'm tottaly new to Ubuntu and I cound't find anything...

Is there any keyword that I could search?

I'm pretty sure that the error message was about the processor (and the 4 cores)... But I cound't see the message at the last time, since I was away from computer... :(

---

### Post by CharlesA on 2013-02-26
If the logs aren't too big, you could zip them up and attach them to the post, but generally you will notice something abnormal or that something doesn't look right.

Each user's log is semi unique to their system, as each system has its own quirks.

---

### Post by nanoVapor on 2013-02-27
Hi,

Thanks for the support!

I attached my logs in this post.

---

### Post by CharlesA on 2013-02-28
I didn't see much in the logs. Maybe someone more familiar will take a look at them.

---

### Post by nanoVapor on 2013-03-05
> **CharlesA said:**
> I didn't see much in the logs. Maybe someone more familiar will take a look at them.


Thanks for the reply CharlesA!

Anyone else?

---

