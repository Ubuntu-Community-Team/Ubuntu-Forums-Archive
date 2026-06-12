---
title: "Suspend / Hibernate Issues"
date: 2007-01-09
forum: General Help
---

### Post by bg1256 on 2007-01-09
I have two computers, one running Dapper, the other running Edgy.  Both are having issues with suspend/hibernate.

On my laptop (Dapper), I can enter suspend and hibernate just fine; however, when I attempt to resume, the computer asks for my password, leaves suspend/hibernate for a few seconds, then goes back into suspend.  After it does this, I can resume normally without it suspending again.

Any way to fix this?

Also, is there any way to resolve the issues with suspend / hibernate in Edgy as well? I'm also running aiglx+beryl on my desktop computer, which is running Edgy.

Thanks!

---

### Post by galileon on 2007-01-23
hi do you have nvidia drivers installed? for me, they break suspend and hibernate.

i changed "nvidia" back to "nv" in xorg.conf, and these two work fine now. i can live without acceleration, its a tablet pc...

---

### Post by tux21 on 2007-01-23
hibernation doesn't work at all for me in edgy
but works flawlessly in blag.

---

### Post by bg1256 on 2007-02-08
I do have 3d acceleration enabled with the new nvidia drivers.  Is there any known workaround for this?

---

### Post by galileon on 2007-02-08
found the solution on this link,

[http://parrenin.frederic.free.fr/DellLatitudeD800/linux-DellLatitudeD800.html](http://parrenin.frederic.free.fr/DellLatitudeD800/linux-DellLatitudeD800.html)
<quote>
Xserver - Proprietary "nvidia" driver
You need for that to install nvidia-glx, and to change one line in /etc/X11/xorg.conf from:
       Driver          "nv"
to:
       Driver          "nvidia"
Display then works, but you only have access to the maximal resolution (1920x1200).
I have not found a solution to this yet.

For the display to wake up correctly after a suspend/hibernate, you also have to:
1) Add this line in section "device" of your /etc/X11/xorg.conf file:
        Option          "NvAGP" "1"
2) Set POST_VIDEO to false in /etc/default/acpi-support
You really need those two things together to make it work.
(I have tested with either one or the other and it does not work).

This is my xorg.conf file for the nvidia driver.

There is a problem that prevents access to a virtual console with <CTRL>-<ALT>-<F1> to <CTRL>-<ALT>-<F6> when using the nvidia driver.
To solve this problem, simply add vga=788 after splash in your /etc/grub/menu.lst file.
This makes the screen using a 800x600 resolution during the boot process and for the virtual consoles.
You can also use vga=791 to have it in 1024x768.
Unfortunately, I have not figured out how to use a "wide screen" resolution (e.g. 1280x800).

TVout also does not work correctly.
<Fn>-<F8> does not switch between dispalys as expected.
The only solution I found was to boot with the cable connected (or more simply to restart the X server with the cable connected).

</quote>
check it out.

---

