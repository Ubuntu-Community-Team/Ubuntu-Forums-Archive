---
title: "slow waking up from hibernate mode"
date: 2008-01-29
forum: General Help
---

### Post by shakirsahab on 2008-01-29
hello everyone. i'm new to ubuntu (GUTSY) and so far i think i'm liking it. however, i have it loaded on an HP laptop that i take to school and what not so i have to close the screen causing it to go into hibernation. 

when i open it, it takes like a good minute for it to show the password prompt, afterwards its fine though. any help?

---

### Post by Zebediah49 on 2008-01-29
> **shakirsahab said:**
> hello everyone. i'm new to ubuntu (GUTSY) and so far i think i'm liking it. however, i have it loaded on an HP laptop that i take to school and what not so i have to close the screen causing it to go into hibernation. 

when i open it, it takes like a good minute for it to show the password prompt, afterwards its fine though. any help?

System-Preference-Power Management.  It's in there.

---

### Post by shakirsahab on 2008-01-29
i know how to work the settings for when i want it to hibernate/suspend etc, but the problem is that when its hibernated and i want to wake it up, it takes a good while for it to wake up.

---

### Post by tiredofthis on 2008-01-30
I can verify the same behavior on an HP 8510p. Got suspend to work, but there seems to be a timeout of about a minute when waking up. Nothing meaningful in the logs, from what I can see.

---

### Post by tiredofthis on 2008-02-01
I found a solution for my HP laptop: In the BIOS settings, disable "SATA native mode" (under "Device Configurations"). This must have been what caused a time-out on the hard disk.

---

