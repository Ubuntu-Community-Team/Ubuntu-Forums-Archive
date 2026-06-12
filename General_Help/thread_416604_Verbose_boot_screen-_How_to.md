---
title: "Verbose boot screen- How to??"
date: 2007-04-21
forum: General Help
---

### Post by zenwalker on 2007-04-21
Hi,

I want to get the verbose mode boot screen in Edgy. I mean in other distros, while booting we get a splash screen with a progress bar on it. But if we press F2 or ESC keys, then it will take us to the verbose mode where we can see the booting steps the kernel is doing. So i want the same thing in Edgy too. 

Oh ya i commented out the "QUITE" line in the /boot/grub/menu.lst file too. But that was of no use at all. 

Btw whats the QUITE line do there??

So ya, how to get the booting verbose screen also if get that, if i want to go back what should i do??

Thanks

---

### Post by Theimon on 2007-04-21
Ctrl+Alt+F1 should do the trick, taking out the quiet-parameter gives even more feedback from the console than default.

---

### Post by rajitsrinivas on 2007-04-21
I installed startupmanager to modify GRUB options graphically.This tool has an option called 'Show text during boot' on the Boot options menu. And I was satisfied with the verbose info.
May be you should try it from Synaptics.

---

### Post by mcduck on 2007-04-21
> **zenwalker said:**
> Hi,

I want to get the verbose mode boot screen in Edgy. I mean in other distros, while booting we get a splash screen with a progress bar on it. But if we press F2 or ESC keys, then it will take us to the verbose mode where we can see the booting steps the kernel is doing. So i want the same thing in Edgy too. 

Oh ya i commented out the "QUITE" line in the /boot/grub/menu.lst file too. But that was of no use at all. 

Btw whats the QUITE line do there??

So ya, how to get the booting verbose screen also if get that, if i want to go back what should i do??

Thanks

You are not supposed to comment any lines out, instead you should remove the 'quiet' from defoptions & your kernel entry lines.

```
# defoptions=quiet splash
```
should become
```
# defoptions=splash
```

and then change:
```
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda3 ro quiet splash
```
..into this:
```
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda3 ro splash
```

If you want to completely disable the graphics, to only see the text, also remove the 'splash' from both these lines. You may also add 'vga=792' to change the boot splash & TTYs into 1024x768 with 24-bit colors.

---

