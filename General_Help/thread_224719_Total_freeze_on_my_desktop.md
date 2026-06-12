---
title: "Total freeze on my desktop"
date: 2006-07-28
forum: General Help
---

### Post by Grog140 on 2006-07-28
I am pulling my hair out trying to figure this out, it seems so random. I could use the computer for hours without freezing, but then come back later and it freeze 10 seconds in! ITs a complete freeze, no curser momemnet, nothing!

The machine is a:
Dell Dimension 5100
ATI Radeon X300
512mb of RAM
3.0Ghz P4 w/HT

As a side note, I AM running XGL/compiz but I cannot link it directly to this fact because the freezes are so random! I haven't have it crash yet if I run it under Gnome without XGL but I have spent little time in there so it COULD have froze if I used it anymore.

The problem is that I cannot purposely repeat the problem! So if anyone has any info about freezes on either my hardware, or freezes in general would be appretiated.

Thanks

---

### Post by philippe_carlo on 2006-07-28
XGL is a good bet. Try sniffing through the logs in /var/log. Maybe you can find something out of the ordinary there.

---

### Post by Grog140 on 2006-07-28
Yip, lots of errors compared to my laptops log file. Here is just a sample of the many, many lines of errors.

```
Jul 28 16:30:23 randell-desktop kernel: [17179790.988000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0x08ce4000 for 49152 bytes
Jul 28 16:30:23 randell-desktop kernel: [17179790.988000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
Jul 28 16:30:23 randell-desktop kernel: [17179790.988000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xc4bafd80 for 49152 bytes
Jul 28 16:30:24 randell-desktop kernel: [17179792.532000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0x08ce4000 for 49152 bytes
Jul 28 16:30:24 randell-desktop kernel: [17179792.532000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
Jul 28 16:30:24 randell-desktop kernel: [17179792.532000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xc8c08680 for 49152 bytes
Jul 28 16:30:27 randell-desktop kernel: [17179794.992000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xb078d000 for 1916928 bytes
Jul 28 16:30:27 randell-desktop kernel: [17179794.996000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
Jul 28 16:30:27 randell-desktop kernel: [17179795.000000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xcdce48c0 for 1916928 bytes
```

Seems to be a fglrx thing....lol Or at the very least a ATI problem!

Does anyoen know of anything that might be the problem?

EDIT: None of these errors come up when in a regular gnome session by the way. Perhaps I should head over to the compiz forums and try and get to the bottom of this as well.

---

### Post by jordilin on 2006-07-28
Yes, you are right, the problem is the fglrx ati driver. This driver has known bugs that cause freezings. I would try to install the generic ati driver or downloading the latest ones from the ati website.

---

### Post by Grog140 on 2006-07-28
I would use the generic one but I need 3D support.

And does anyone know if the official ATI one is confirmed to work on my card? An ATI Radeon X300? If so then I will install and hope it works.

Thanks for the advice.

---

### Post by jordilin on 2006-07-28
I have the generic ati driver and I have 3D support. Just typing
```
glxinfo | grep rendering
```
and I get:
> direct rendering: Yes

and if I'm not wrong, that means 3D support, right?

---

### Post by Grog140 on 2006-07-28
Oh, wow. I guess I will opt for the generic driver, thanks! :D

---

### Post by jordilin on 2006-07-29
> **jordilin said:**
> I have the generic ati driver and I have 3D support. Just typing
```
glxinfo | grep rendering
```
and I get:

and if I'm not wrong, that means 3D support, right?

I forget to tell that I have an ati radeon 9550.

---

### Post by flargen on 2006-07-29
From [http://ubuntuforums.org/showthread.php?t=150854]("http://ubuntuforums.org/showthread.php?t=150854"):

Add the line:
```
Option       "KernelModuleParm" "agplock=0"
```
to the device section in /etc/X11/xorg.conf. You should be OK without the other extra lines in that thread.

---

