---
title: "Radeon error fix?"
date: 2004-11-07
forum: General Help
---

### Post by Adam Boettiger on 2004-11-07
On bootup, I get one line with the following error:

Radeon  fb: Invalid Rom Signature 0 should be 0xaa55

What do I need to do to fix this so I don't see the error on bootup??

---

### Post by FLeiXiuS on 2004-11-07
Have you installed the 'FGLRX' drivers for ATI?

Can you access a failsafe terminal?

---

### Post by Adam Boettiger on 2004-11-07
No. How do I do that?

I can access terminal but don't know how to tell if it is failsafe or not.

---

### Post by wallijonn on 2004-11-07
I take it that this is a laptop. ?

Can you set "no ACPI" in the bios before building the OS?

.

---

### Post by FLeiXiuS on 2004-11-09
[QUOTE=Adam Boettiger]No. How do I do that?

I can access terminal but don't know how to tell if it is failsafe or not.[/QUOTE]

A terminal is great.  Let me point you to the right direction of installing the ati fglrx drivers.

**Installing ATI FGXLR Drivers**
[http://wiki.ubuntulinux.org/BinaryDriverHowto](http://wiki.ubuntulinux.org/BinaryDriverHowto)

**Enabling 3d Acceration**
[http://ubuntuforums.org/showthread.php?t=3567&highlight=fglrx](http://ubuntuforums.org/showthread.php?t=3567&highlight=fglrx)

---

### Post by daniels on 2004-11-09
DON'T INSTALL FGLRX -- THIS WILL NOT HELP AT ALL

The error is relatively harmless and will *not* impact in *any* way on X's operation.  If you want to give the complete dmesg log, output of lspci, et al, it might get debugged and fixed, but as it is, it's not a pressing issue, and won't harm X.

Repeat, installing fglrx will almost certainly just cause your problems, and it absolutely won't solve the radeonfb error.

---

### Post by ulrich on 2004-11-09
> Repeat, installing fglrx will almost certainly just cause your problems, and it absolutely won't solve the radeonfb error.
but wouldnt it be nice for him to have 3d accel through fglrx?
as far as i my experience go, the radeon-driver just gives nice 2d quality but no real 3d harware accellaration. or is in this case the fb (framebuffer i assume?) something completely different?

---

### Post by daniels on 2004-11-09
[QUOTE=ulrich]but wouldnt it be nice for him to have 3d accel through fglrx?
as far as i my experience go, the radeon-driver just gives nice 2d quality but no real 3d harware accellaration. or is in this case the fb (framebuffer i assume?) something completely different?[/QUOTE]The standard radeon driver gives full 3D acceleration for r1xx/r2xx (everything up to, but not including, 9550, and also the IGP320/340 chips).  fglrx is a nightmare to install, and often ends up with many problems, as can be seen by the fact virtually half of the active threads every day are about problems with fglrx.

The framebuffer is different from X -- it's the kernel driver for the console.  That error is nothing to do with X (indeed, it comes long before the kernel even tries to mount the root filesystem), so fglrx cannot and will not fix it.

---

### Post by ulrich on 2004-11-09
> The standard radeon driver gives full 3D acceleration for r1xx/r2xx (everything up to, but not including, 9550, and also the IGP320/340 chips). fglrx is a nightmare to install, and often ends up with many problems, as can be seen by the fact virtually half of the active threads every day are about problems with fglrx.

The framebuffer is different from X -- it's the kernel driver for the console. That error is nothing to do with X (indeed, it comes long before the kernel even tries to mount the root filesystem), so fglrx cannot and will not fix it.

thanks for lighten this up!
i for myself own an ati-based card for a year or so now and back then getting the whole thing work was a mess. kernel patching, driver patching... it really was no fun. i think i spended a complete month on that. to complete the mess i had buyed a nforce2 based mobo...

but today i think setting fglrx up is, especially with ubuntu, a minute thing.

at home and here at work i use ati (9500 and 9100) and with both systems there was no problem setting fglrx up. could be that one of the causes is that i now can recite a complete XF86Config in my sleep since that mess back then, but with ubuntu it worked right out of the box.
im not  really an fglrx-fan cause as a user i see all that stuff that still doesnt work compared to the windos-drivers but the 2d-signal of ati-cards is way more better than nvidias, i think. so i have to stuck with them.

---

