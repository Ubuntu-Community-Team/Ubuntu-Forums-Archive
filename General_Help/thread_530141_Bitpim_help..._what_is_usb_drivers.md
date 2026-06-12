---
title: "Bitpim help... what is usb drivers?"
date: 2007-08-20
forum: General Help
---

### Post by Hopeless on 2007-08-20
Hi,

I installed bitpim for my Samsung phone, in bitpim help it says:

Follow these steps to try and diagnose your issue:

    *      If you are using a USB to serial cable, then you [COLOR="Red"]MUST use device drivers[/COLOR]. BitPim does not speak the USB to serial protocols. This applies to ALL platforms. The drivers are specific to your operating system, the USB to serial chip and product/vendor id used by the chip.

    *      If your phone uses the USB modem protocol which is normal for most phones (eg all Audiovox and Sanyo) then you MUST use device drivers on Windows. [COLOR="Red"]On Linux the acm kernel module should auto-bind to the phone[/COLOR]. The Mac also uses a builtin default USB modem driver. 

and...

In order to take advantage of this feature, make sure that the followings are in place:

    * File /etc/udev/rules.d/60-bitpim.rules exists.
    * [COLOR="Red"]File /usr/bin/bpudev exists.[/COLOR]
    * Group cellusers exists and you belong to that group. 

how do i do the bits in red?

Thanks
:popcorn:

---

### Post by tim15856 on 2007-08-26
Did you get your problem solved yet? I'm waiting for my USB cable to arrive for my Samsung A850. I hope this program works with it. The place I bought the cable from stated that bitpim works with it and doesn't need drivers.

As for " File /usr/bin/bpudev exists.", does "udevinfo -V" show you are running udev version 095 or later? You may need to try the other Linux USB setup procedures.

---

