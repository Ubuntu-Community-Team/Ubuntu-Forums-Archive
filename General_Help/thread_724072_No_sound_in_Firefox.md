---
title: "No sound in Firefox"
date: 2008-03-14
forum: General Help
---

### Post by TRANQU111TY on 2008-03-14
While playing videos etc in Firefox I have no sound. Amarok works fine. I'm not sure if using a sound in Thunderbird for incoming mail has something to do with this.

---

### Post by danwood76 on 2008-03-14
Are the videos you are playing flash videos?
It could be a flash issue.

---

### Post by TRANQU111TY on 2008-03-16
> **danwood76 said:**
> Are the videos you are playing flash videos?
It could be a flash issue.

Nope. Actually Flash videos are working fine now. But still no sound with normal videos playing in Firefox.

---

### Post by Ub1476 on 2008-03-16
It probably doesn't work because you opened Amarok first, and when playing sound in Ff as well, ALSA will not allow this because the "audio device (already) is busy". Will be fixed in Hardy Heron (April), I think.

Try to logout, then **only** start Firefox.

It might be an Ubuntu bug though, since I'm using Arch Linux and can use Amarok and Youtube at the same time.

---

