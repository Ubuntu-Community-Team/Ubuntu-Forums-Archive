---
title: "Is there a way to set commands to run automatically from grub rescue?"
date: 2017-10-05
forum: General Help
---

### Post by jerommal on 2017-10-05
Hey all, due to some unfortunate software updates (Windows) when I boot to linux these days I'm taken to a grub rescue terminal.  I've found a set of commands that resumes a normal boot cycle:

```

set root=(hd0,6)
set prefix=(hd0,6)/boot/grub
insmod normal
normal

```

For all intents and purposes this works fine, but it's a pain to type in every time I turn my computer on.

My question is, is there a way to set up the grub rescue prompt to automatically type in these instructions when it starts, instead of having to do it manually?

Also, are there any not obvious issues that may arise from a boot that isn't working properly?  I'm not very confident about what's happening under the hood here, so I want to make sure my installation doesn't have some new holes in it that I should get taken care of.

Thanks a lot



(I'm dual booting with Windows 10, and these problems have arisen after  finally giving in and installing the new "Creator's Update," which seems to have corrupted my boot partition somewhat.  Thanks  Microsoft!)

---

### Post by VMC on 2017-10-05
This is what I do to get grub back:

```
sudo grub-install --recheck --root-directory=/ /dev/sda
```

Do this from terminal after your ubuntu boots up. Then you can update grub:
```
sudo update-grub
```

This is for a BIOS computer.

---

