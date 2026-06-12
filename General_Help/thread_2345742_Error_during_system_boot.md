---
title: "Error during system boot"
date: 2016-12-07
forum: General Help
---

### Post by marckino on 2016-12-07
Hi everyone, I'm new on this forum and on the Linux world.
I just recently installed it on my new laptop Kubuntu 16.10 overwriting win 10.
All was well, compatibility seems great, the problem is that when I start or stop the system I get this error on black screen:

```

[  26.0887641  i2c_hid  i2c-ITE8350:00:  failed to reset device.

```

But I do not understand what comes, maybe I was wrong to install the system, or simply missing some drivers.
On the net I didn't found anything on this issue, so I decided to post it here to see if someone knows what is due.
But it seems not to affect the operation of my computer.

---

### Post by ian-weisser on 2016-12-07
If your touchpad functions, then you can safely ignore it.
It's a kernel error that occurs once (26.088 seconds after boot), probably during touchpad initialization, and merely remains in that display register.

---

### Post by marckino on 2016-12-08
Ok, thanks, but there isn't a way to fix this error for example by updating the kernel.

---

### Post by ian-weisser on 2016-12-08
Depends on cause of the error.

It might be a bug. It might be a misconfiguration. It might be something else.
Investigating such an event can be very fulfilling, and a great opportunity to learn new skills. 
However, there is likely no easy fix to the initial failure of touchpad initialization at this time.

If you wish to investigate, start with the kernel log in /var/log/dmesg. If you can locate the error in that log, the events immediately before may offer clues to the failure.

---

