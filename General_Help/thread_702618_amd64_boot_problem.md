---
title: "amd64 boot problem"
date: 2008-02-20
forum: General Help
---

### Post by slayer666 on 2008-02-20
I managed to install the amd64 version of heron with wubi. But when the ubuntu "knight rider" splashscreen is supposed to appear nothing does. The screen is black. I can hear some activity, but I don't know if there's any errormessages due to the black monitor. not even a blinking marker.

The monitor is active so the monitor has signal.

Any ideas?

---

### Post by ago on 2008-02-20
What version of wubi is that?
At the countdown press esc and select verbose mode
Did you try ctrl+alt+f2?

---

### Post by slayer666 on 2008-02-20
> **ago said:**
> What version of wubi is that?
At the countdown press esc and select verbose mode
Did you try ctrl+alt+f2?

No.... :)

---

### Post by ago on 2008-02-21
Does the orange progressbar stop at a couple of notches? 
And neither ctrl+alt+del nor ctrl+SysRq+B do work.
I have that issue with amd64 on an samsung machine. Did not have much time to debug yesterday night, but that looks very much like a kernel issue during the rcS.d sequence (when loading up some modules).

If that is the case, press esc to edit the boot menu, select the normal boot mode, remove "splash" from the kernel line

When you reboot tell me what is the last line you see.

Repeat the process removing "quiet splash" this time.

---

### Post by slayer666 on 2008-02-21
> **ago said:**
> Does the orange progressbar stop at a couple of notches? 

The orange bar doesn't show at all, no ubuntu logo. nothing. The screen is on but only showing black.

---

### Post by ago on 2008-02-21
Then press esc and select safe graphic mode if that fails see the verbose mode

---

