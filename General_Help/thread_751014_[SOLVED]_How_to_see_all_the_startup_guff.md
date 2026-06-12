---
title: "[SOLVED] How to see all the startup guff?"
date: 2008-04-10
forum: General Help
---

### Post by whitefort on 2008-04-10
Hi,

I know the progress bar as Ubuntu loads looks very cool, but I'm wondering how to turn it off.  I'm trying to learn a bit more about how Linux actually works, and I thought it would be helpful if I could see all that text-on-the-screen stuff, and try to learn more about Linux by figuring out what it all means.

I *think* I remember reading that some key or key combination would turn off the pretty progress bar, but I can't remember what it was.

Am I right in thinking that I can turn off the progress bar?  If so, I'd be grateful if someone would tell me how.

Thanks.

---

### Post by prshah on 2008-04-10
> **whitefort said:**
> 

I *think* I remember reading that some key or key combination would turn off the pretty progress bar, but I can't remember what it was.

Thanks.

That's a good idea. Ctrl+Alt+F8 (Virtual terminal 8 ) carries progress messages as the system is booting. 

But I have no idea on how to permanently turn off the progress bar.

---

### Post by p_quarles on 2008-04-10
To permanently disable the bootsplash screen, you'll need to do two things (permanent, btw, does not mean irreversible):
```
sudo mv /etc/rc2.d/S98usplash /etc/rc2.d/D98usplash
```
This changes the usplash script from automatically starting to being automatically disabled. Then, you will need to edit the kernel initiation command:
```
sudo nano /boot/grub/menu.lst
```
For the default boot entry, simply remove the words "quiet" and "splash" from the "kernel" line. The standard output for the boot process will now be visible.

Simply reverse these steps to get the bootsplash back.

---

### Post by whitefort on 2008-04-10
Great!  Many thanks for the speedy replies!

---

