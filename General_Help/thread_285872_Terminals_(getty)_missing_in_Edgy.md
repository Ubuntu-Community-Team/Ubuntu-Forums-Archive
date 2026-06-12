---
title: "Terminals (getty) missing in Edgy?"
date: 2006-10-27
forum: General Help
---

### Post by Daniel15 on 2006-10-27
Hi,
 I've recently upgraded to Ubuntu Edgy, and I've noticed a fairly annoying problem: The getty terminals are missing! (You know, the CTRL+ALT+F1, CTRL+ALT+F2, etc.). Is there any way to get these back? I'm having problems with getting X to start, which means I have to constantly reboot into recovery mode...

Thanks,
 --Daniel15

---

### Post by Daniel15 on 2006-10-28
OK, I fixed this problem, so I think I should post how I did it...

I fixed this problem by editing the resolution that the framebuffer uses. Edit **/boot/grub/menu.lst** (by typing 'sudo nano /boot/grub/menu.lst' in a terminal), and find the 'kernel' line for your kernel (it will be towards the end of the file). Add this to the end of the line:
```
 vga=0x318
```
For example, my kernel line now looks like:
```
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda6 ro quiet splash resume=/dev/sda8 vga=0x318
```
Reboot, and check if it worked.

The only problem I found was that the Ubuntu splash screen doesn't look proper (the Ubuntu logo is not centered). Apart from that, everything appears to be working fine :)

---

### Post by Ramses de Norre on 2006-10-28
If you add the option to the ```
#defoptions 
``` line it will be added to new kernels automatically and remain on the old ones after kernel upgrades ;)

---

### Post by Daniel15 on 2006-10-29
> **Ramses de Norre said:**
> If you add the option to the ```
#defoptions 
``` line it will be added to new kernels automatically and remain on the old ones after kernel upgrades ;)

Oh, I didn't know that. Thanks for telling me :)

---

