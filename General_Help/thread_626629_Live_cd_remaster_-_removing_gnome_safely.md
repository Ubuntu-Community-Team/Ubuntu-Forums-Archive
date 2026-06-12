---
title: "Live cd remaster - removing gnome safely"
date: 2007-11-29
forum: General Help
---

### Post by fibuntu on 2007-11-29
So, I've tried to remaster the Ubuntu Gutsy live cd.

There's a big problem. I wanted to remove gnome and did apt-get remove --purge gnome* 
I installed fluxbox then. Then I squashfs'ed the thing and made the iso. I tested it with qemu and vmware both. It hangs on the place where the usplash progress bar is going from head to head. There comes a screen where it reads some text about "Built-in shell (ash)" and then there's a line with text "(initramfs)" and then the cursor. So, does "apt-get remove --purge gnome*" remove some essential stuff and makes the cd not to work? Or what am I doing wrong?

---

