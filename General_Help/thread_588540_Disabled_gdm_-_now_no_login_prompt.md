---
title: "Disabled gdm - now no login prompt"
date: 2007-10-23
forum: General Help
---

### Post by spaceman_spiff on 2007-10-23
Hi,

I have not been able to switch to a virtual console for quite some time, both in 7.04 and now in 7.10. I need it now to be able to install new NVIDIA drivers. When I try Alt-Ctrl-F2 I get a blinking cursor but no login prompt.

I tried disabling gdm by using rcconf (unchecking the gdm so it won't start. Plan to use startx from the promt instead), but now the booting hangs after "Running local boot scripts (/etc/rc.local)      [OK]".

No login prompt. 

I can boot into recovery mode to get a prompt, but that leaves me at initlevel 1, which makes the NVIDIA installation complain and request that I go to initlevel 3. But then it hangs as above.

Any clues?

---

### Post by #Reistlehr- on 2007-10-23
have you tried typing?

This happens to me, and i hit enter or space a few times, and the prompt finally appears.

But i'm sure you've tried that. So i'll go brainstorm some more.

---

### Post by jhofmann on 2007-10-23
Welcome to Bug 129910.  I think, anyway.  Only advice I could give is to re-enable gdm if possible and try to use the Restricted Drivers Manager.

Wish I could help more,
Jim

---

