---
title: "Ubuntu server fails to boot"
date: 2013-04-22
forum: General Help
---

### Post by Chris Jerome on 2013-04-22
Hi All,

I am a linux newbie, although lots of other computer experience (mostly Windows). I installed ubuntu 12.04 server on an old Dell workstation a couple of days ago. After a couple of false starts I had it up and working as a webserver (typical LAMP installation), serving up PHP pages like a champ. Yesterday I did apt-get update and upgrade, and installed R as well. All seemed fine. Today on login I got a message that a restart was needed so I rebooted the server and now it won't come up properly. I can get to the Grub screen and it will run in recovery mode. I checked the files in /var/log to see if I could find any errors. The only ones modified today were wtmp, kern.log, syslog, auth.log, and lastlog. Of those I could read, none contained anything that looked like significant errors. 

I looked at dmesg, which was last written to yesterday. In that file, the only significant stuff seemed to be errors related to a device called i915 (I think) and some ACPI warnings about memory conflicts. But since this file was apparently last modified yesterday, it doesn't seem likely to be related to the current problem.

If I select the non-recovery mode Ubuntu, there is a little bit of disk activity and some mesages scrolling too fast to read, then the screen just goes blank.

I could reinstall and start over, but I'd really like to troubleshoot this and fix it if possible, I just don't know how to proceed. Any help would be greatly appreciated.

Cheers
Chris

---

### Post by papibe on 2013-04-22
Hi Chris Jerome.

Are you able to boot on a previous kernel? Have you tried that?

i915 is the module/driver for Intel integrated graphics. Could you post the result of these commands?
```
lsmod | grep i915

sudo modprobe i915
```
Regards.

---

### Post by Chris Jerome on 2013-04-22
Thanks for your response!

I don't know how to boot on a previous kernel, so no, I have not tried that.

[FONT=Courier New]lsmod | grep i915 gives me:

i915    474913  0
drm_kms_helper  47459  2 radeon,i915
drm  240232 4 radeon,ttm,i915,drm_kms_helper
i2c_algo_bit  13317 2 radeon,i915
video  19117 1 i915

modprobe i915 does not return anything

This machine has VGA on the motherboard, but I am actually using an accessory video card with DVI output (I think it's an ATI card). I don't need that card in there for what I am doing with this machine, I was just thinking about pulling it out and using the onboard VGA instead, in case that was the problem.

Cheers
Chris[/FONT]

---

### Post by papibe on 2013-04-22
Thanks.

It looks like both the Intel and ATI (radeon) modules are loaded. That could be the source of the memory conflict.

IMO, if it is text mode server, you don't need the dedicated graphics.

Some BIOS let you select either the integrated graphics, the dedicated card, or auto (which usually selects the PCI card).

Let us know how it goes.
Regards.

---

### Post by Chris Jerome on 2013-04-22
Hi papibe,

I selected onboard VGA in BIOS, scrambled around and liberated a VGA cable to use, rebooted - and voila! It works!

Thanks so much for your help! Now I can continue with my project....

All the best
Chris

---

