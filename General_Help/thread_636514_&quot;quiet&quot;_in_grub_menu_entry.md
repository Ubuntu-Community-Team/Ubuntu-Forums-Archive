---
title: "&quot;quiet&quot; in grub menu entry?"
date: 2007-12-09
forum: General Help
---

### Post by Schalken on 2007-12-09
My Ubuntu Gutsy grub menu entry looks like this: ```
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=cd378e5e-24e4-4d76-a119-8aa6a678f6af ro **quiet** splash
initrd          /boot/initrd.img-2.6.22-14-generic
**quiet**
``` I was wondering what is the purpose of the "quiet" command after the initrd line, what's the difference between that and the "quiet" option on the kernel line?

---

### Post by p_quarles on 2007-12-11
They both do the same thing: they hide non-critical text output during the various stages of the boot process. You'll notice that the Recovery Mode boot option omits this option: if you boot into that, you'll see all the output instead of the splash screen.

---

### Post by Existentialist on 2007-12-11
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=cd378e5e-24e4-4d76-a119-8aa6a678f6af ro **quiet splash**
initrd          /boot/initrd.img-2.6.22-14-generic
**quiet**

If you remove the parts in bold, you can see the difference.  Rather than a ubuntu loading screen you can see the actual boot process and the dmesg output.  It will still load to the graphical login after it starts x.

---

### Post by Schalken on 2007-12-13
Hmmm, it still doesn't explain what the difference is between the two. If there is no difference, why is there two?

---

### Post by jwcgator on 2007-12-13
There IS a difference.

Quiet = Splash screen, that's all you see

No quiet = you see all the output of the stuff that's actually happening, instead of the splash screen

---

### Post by p_quarles on 2007-12-13
> **Schalken said:**
> Hmmm, it still doesn't explain what the difference is between the two. If there is no difference, why is there two?
Are you asking about the difference between "quiet" in the two settings, or are you asking about the difference between the two boot processes? "quiet" means the same thing in both cases, but vmlinuz-2.etc and initrd.img-2.etc are two separate elements in the boot routine.

---

### Post by Schalken on 2007-12-14
sorry, no i mean what is the difference between the "quiet" that comes after "initrd", and the "quiet" that is on the same line as "kernel". (you may need to scroll the code box to the right to see the latter)

---

### Post by p_quarles on 2007-12-14
> **Schalken said:**
> sorry, no i mean what is the difference between the "quiet" that comes after "initrd", and the "quiet" that is on the same line as "kernel". (you may need to scroll the code box to the right to see the latter)
No, I see what you're talking about, and, again, there's no difference in meaning. The "quiet" option (for both "kernel" and "initrd") just means that it's not going to display the text output for those two stages of the boot process. 

If you wish to explore this further, just remove those "quiet" options from the file, and reboot.

---

