---
title: "Changed CD Drive, now it won't boot..."
date: 2008-04-03
forum: General Help
---

### Post by motorbelly on 2008-04-03
I've had a decently running copy of 7.10 running but the CD drive was acting flakey at best, sometimes worked, sometimes didn't.

So I opened the box and swapped with another drive and tried to reboot. The boot process stops at recognizing that drive, stalls and eventually drops to a initramfs prompt.

I'd just put the old drive back and try but its been disposed already.

How can I tell the system to accept the new drive and boot?

---

### Post by adamitj on 2008-04-03
Your CD-ROM drive is IDE or SATA?

For IDE:

What if you check your BIOS config for IDE drives? Generally is the first option on your CMOS SETUP.

Notice that IDE drives need jumper configuration, but if you can boot the CD-ROM it is working fine...

However, if you CMOS config was static, the LBA and other IDE options like PIO MODE, etc, could be set for the old drive. So you need to set it as aumatic or detect the new options (in most cases using F3 key).


For SATA

SATA drives are like USB, and them are detected automatically. The only need is to set the right setup order, first CD-ROM, later HD.

If your SATA CD-ROM drive is too new, it is a little impossible, but maybe there's no kernel native support for your drive, or it have some incompatibility with the kernel...

---

### Post by motorbelly on 2008-04-03
Thank you for your reply!

It is IDE and I simply opened CMOS and rechecked everything (didn't change anything) but on rebooting it passed the stall it had done at CD. But it stalled again loading the ethernet card and as it dropped I recognize the error above the prompt as the same it had been before:

[INDENT]Check root= bootarg cat /proc/cmdline
or missing modules devices: cat /proc/modules is /dev[/INDENT]
ALERT! /dev/disk/by-uuid/b7da2320-d649-43b0-bc2f-eaac887bb20a does not exist. Dr
opping to a shell


I'm guessing I must be asking the wrong question. Was just hoping to avoid a full re-install.

---

