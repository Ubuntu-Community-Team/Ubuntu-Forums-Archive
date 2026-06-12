---
title: "Second Dual Boot Screen after Grub Menu? (Need help!)"
date: 2012-10-23
forum: General Help
---

### Post by elise17 on 2012-10-23
Hi,
here's the run through:

1. I turn on my computer
2. Splash Loading Screen
3. Grub menu (where I choose whether to boot into 12.04 or Windows 7)
4. [This is where my issue is] If I select to boot into Windows in step 3, a 2nd Dual Boot Screen appears, where I have to again select between Ubuntu and Windows. If I select Windows, it boots up fine but if I select Ubuntu nothing happens. 

I want to get rid of this 2nd Dual Boot Screen because I find it unnecessary. Anyone knows how to do this? :-k

---

### Post by ~LoKe on 2012-10-23
What's the output of:
```
cat /boot/grub/grub.cfg
```

---

### Post by Mark Phelps on 2012-10-23
> **elise17 said:**
> [This is where my issue is] If I select to boot into Windows in step 3, a 2nd Dual Boot Screen appears, where I have to again select between Ubuntu and Windows. If I select Windows, it boots up fine but if I select Ubuntu nothing happens. 

I want to get rid of this 2nd Dual Boot Screen because I find it unnecessary. Anyone knows how to do this? :-k

What has happened is that a boot entry for Ubuntu has been added to your Win7 boot loader.  The only way I know for sure that this happens is if you install using Wubi -- as that uses the Windows boot loader to launch the menu.

Since that selection does nothing, my guess is either that you (1) installed using Wubi and later removed that install, or (2) tried to install using Wubi and it only partially worked.

If you know FOR SURE that your Ubuntu installation is in its own partition OUTSIDE of Windows, then you should do the following in Win7:
1) Download and install EasyBCD from the NeoSmart Technology Forums
2) Launch EasyBCD, Click the Edit Boot Menu button, select the Ubuntu menu item -- and delete it. Click the Save Settings icon (looks like a diskette).

When you then reboot and select Win7, you should not be getting a menu screen anymore.

---

### Post by elise17 on 2012-10-23
> **Mark Phelps said:**
> What has happened is that a boot entry for Ubuntu has been added to your Win7 boot loader.  The only way I know for sure that this happens is if you install using Wubi -- as that uses the Windows boot loader to launch the menu.

Since that selection does nothing, my guess is either that you (1) installed using Wubi and later removed that install, or (2) tried to install using Wubi and it only partially worked.

If you know FOR SURE that your Ubuntu installation is in its own partition OUTSIDE of Windows, then you should do the following in Win7:
1) Download and install EasyBCD from the NeoSmart Technology Forums
2) Launch EasyBCD, Click the Edit Boot Menu button, select the Ubuntu menu item -- and delete it. Click the Save Settings icon (looks like a diskette).

When you then reboot and select Win7, you should not be getting a menu screen anymore.

My current Ubuntu Installation is definitely in a separate partition, I'll install EasyBCD in Windows and see if it works, thanks! :)

---

### Post by elise17 on 2012-10-26
It works great, 2nd dual boot screen gone. Thank You Mark Phelps!

---

