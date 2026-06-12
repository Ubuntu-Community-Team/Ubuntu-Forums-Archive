---
title: "Stop quiet booting?"
date: 2007-10-11
forum: General Help
---

### Post by rdoolen on 2007-10-11
I am running the Gutsy Beta; therefore, there are lots of kernel updates. Every time that happens, the update rewrites the menu.lst, and puts the "quiet" back in the booting options.

Well, I don't want quiet. I want to see all the booting info. I know this has been the default for a couple of versions, but is there away to stop it from doing this, or am I stuck editing it out every time. 

By the way, Gutsy is a nice update, I look forward to it stabilizing. I mean, if this is my biggest complaint, it must be going good. 

Thanks.

---

### Post by FuturePilot on 2007-10-11
Find this in your menu.lst
```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

```
Remove the quiet splash, then run
```
sudo update-grub
```

---

### Post by rdoolen on 2007-10-11
Cool, thanks a lot!

---

