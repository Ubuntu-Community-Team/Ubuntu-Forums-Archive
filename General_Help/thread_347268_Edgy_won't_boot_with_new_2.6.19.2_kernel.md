---
title: "Edgy won't boot with new 2.6.19.2 kernel"
date: 2007-01-27
forum: General Help
---

### Post by ronlybonly on 2007-01-27
I just grabbed the sources for the 2.6.19.2 kernel from kernel.org, and I semi-followed the instructions at [http://doc.gwos.org/index.php/Kernel_Compilation_Dapper](http://doc.gwos.org/index.php/Kernel_Compilation_Dapper) The kernel compiled just fine, but... it won't boot. When I try to boot into the new kernel, the splash screen comes up and freezes after about 2 seconds. Does anybody know what is going on here? I would really appreciate any help!

-Andrew

---

### Post by ~LoKe on 2007-01-27
Reboot your computer.  When the message "grub loading" or whatever comes up, hit "Esc" and it'll bring you to a menu.  It'll show you all your kernels and recovery consoles and whatnot.  Use the arrow keys to highlight the new kernel you're trying to boot from then hit "e".  It should bring you to another list, use the arrow keys to move down to the boot line and hit "e" again.  Remove "quiet splash" from the end of the line, then hit "Esc".  Now you should be able to hit "b" to boot.

Now it'll boot without the splash so you can see what's happening.

---

### Post by ronlybonly on 2007-01-27
> **~LoKe said:**
> Now it'll boot without the splash so you can see what's happening.

Okay. When I boot without the "splash" option, I get these messages: 
```

intel_rng: FWH not detected
usb 1-1: device not accepting address 2, error -71

```

Now, when I boot without both the "splash" and "quiet" options, I get these messages:
```

usbcore: registered new interface driver usbhid
drivers/usb/input/hid-core.c: v2.6:USB HID core driver

```

Finally, if I either boot into the recovery kernel or if I disconnect all usb devices, I get:
```

Begin: Waiting for root file system... ...

```
Then it hangs, and the only thing I can do is ctrl-alt-del to reboot.

I have no idea how to interpret these messages, so I'd really appreciate some guidance.

Thanks!
-Andrew

---

### Post by ronlybonly on 2007-01-27
Is there a more appropriate section of the forums to post this question in?

---

