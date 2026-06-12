---
title: "Touchpad working abnormally in sony vaio laptop"
date: 2012-12-06
forum: General Help
---

### Post by arunes007 on 2012-12-06
I recently installed ubuntu1 11.10 on my sony vaio laptop when install was complete
then i noticed my touchpad was not working properly. when I edited grub to this
```

GRUB_CMDLINE_LINUX="i8042.nopnp"

```
and ran
```

sudo update-grub

```
after reboot I got my touchpad working but abnormally. But when I suspended my computer I got it working normally.
So everytime when i restart my laptop I need to suspend my computer to get my touchpad working properly.
it is quite awkward....

---

