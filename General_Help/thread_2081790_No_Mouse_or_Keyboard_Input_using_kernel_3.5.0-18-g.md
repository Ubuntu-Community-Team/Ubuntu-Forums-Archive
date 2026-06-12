---
title: "No Mouse or Keyboard Input using kernel 3.5.0-18-generic"
date: 2012-11-07
forum: General Help
---

### Post by lemming280 on 2012-11-07
After updating my kernel to the latest 3.5.0-18-generic, I have no mouse or keyboard input.  It just sits at the login screen.  Not even the power button works, I have to hold down to power button for 5 seconds and force a shutdown.  If I boot up to the previous kernel, however, everything is fine.

Now that I have updated my kernel once through "apt-get upgrade", I can't seem to do it again, so every time since then I have been purging and reinstalling linux-image-3.5.0-18-generic as well as linux-headers-3.5.0-18-generic.  Each time with the same result, no mouse or keyboard input.

Hopefully someone has experienced this before?
Thanks.

---

### Post by dcstar on 2012-11-09
> **lemming280 said:**
> After updating my kernel to the latest 3.5.0-18-generic, I have no mouse or keyboard input.  It just sits at the login screen.  Not even the power button works, I have to hold down to power button for 5 seconds and force a shutdown.  If I boot up to the previous kernel, however, everything is fine.

Now that I have updated my kernel once through "apt-get upgrade", I can't seem to do it again, so every time since then I have been purging and reinstalling linux-image-3.5.0-18-generic as well as linux-headers-3.5.0-18-generic.  Each time with the same result, no mouse or keyboard input.

Hopefully someone has experienced this before?
Thanks.

That kernel is probably being used successfully by tens of thousands of people by now, report it as a bug that affects your hardware.

---

### Post by lemming280 on 2012-11-12
Actually I got it working two days ago (I forgot about this thread).  It worked when I purged linux-image-3.5.0-18-generic and linux-headers-3.5.0-18-generic (again), and reinstalled both of them as well as linux-image-extra-3.5.0-18-generic.

Thanks for your reply :)

---

