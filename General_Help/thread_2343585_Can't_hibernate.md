---
title: "Can't hibernate"
date: 2016-11-17
forum: General Help
---

### Post by lemino on 2016-11-17
Hi! I've managed to get hibernation to work in previous versions of Ubuntu, but now I just can't seem to get the hang of it. I have:

a Dell Vostro 3360 with Ubuntu 16.10, freshly installed. The installation was a standard one, without encryption or that option that makes it possible to resize the partitions. Pretty plain, you might say. So, when I to "sudo pm-hibernate" (or "sudo systemctl hibernate" for that matter) is that the screen goes black(possibly after the harddrive spinning and fiddling a little, giving me false hopes. It then stays black without anything else happening for about 15 seconds, then the system reboots and gives me the system freshly started with none of the previous applications open. 

Any ideas on this?

/Erik

---

### Post by 0x656b694d on 2016-11-17
Hi,
What is the size of your swap partition and the size of RAM?

---

### Post by lemino on 2016-11-17
They're about the same; the RAM is 4 GB and the swap 4,1 GB.

---

### Post by 0x656b694d on 2016-11-17
is it used when you hibernate or it cannot hibernate even right after boot? I have no more guesses,*sorry. I'd look into dmesg for any errors, ensure swap partition is swapon.
Not sure it really matters in your case, but here [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq) they recomment 6 GB minimum for 4 GB of RAM (i didn't read the whole page though).

---

### Post by lemino on 2016-11-18
Thanks for the help though. I looked into the link you provided, good information although it didn't solve my problem. I resized my swap using a live-usb to 7,5 gb but the situation is still the same. One thing I can think of is that I haven't specified in GRUB the UUID of the swap to resume from - but that should cause problems later, on resuming, not straight away, right?

---

