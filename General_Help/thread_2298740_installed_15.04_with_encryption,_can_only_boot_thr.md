---
title: "installed 15.04 with encryption, can only boot through recovery mode"
date: 2015-10-13
forum: General Help
---

### Post by rae_bot on 2015-10-13
Through a series of ignorant mistakes I seriously broke my 14.04 install yesterday and figured I'd just replace it with a fresh install of 15.04. I also figured I'd choose full-disk encryption/LVM, for fun. Everything seems to work fine once booted, video card driver and all, but booting is problematic.

First, it would just show "no signal" on my monitors when attempting to boot unless I then did a manual reboot (that is, using the actual button on the physical computer). I tried checking for broken files and there were two, so I went through recovery mode and fixed the broken stuff. I think once, maybe, it seemed like it was working. I remember actually being able to type my encryption passcode in the normal screen at some point. I have unfortunately failed to adequately document what happened in what order.

Anyway, now when I try to boot, it brings up the encryption password screen, but doesn't allow me to type anything. A manual reboot seems to bring me to the GRUB menu, but attempting to boot normally now apparently just brings me to the blank purple screen of nothingness.

However, if I go through recovery mode, enter the encryption passcode there, and then just resume normal boot, everything seems to be fine.

So basically to boot up I have to turn on the computer, wait until it gives me the useless login screen, manually reboot, use GRUB to get to recovery mode, enter my passcode, resume normal boot. Not okay.

What in the world do I do?

Details that may or may not bear relevance:
[LIST]
[*]GeForce GTX 770 graphics card
[*]NVIDIA 346.96 driver, using Additional Drivers
[*]Additional Drivers also lists a proprietary driver being used for "unknown" device, which did not show up in my 14.04 install. It says, "Using Processor microcode firmware for Intel CPUs from intel-microcode."
[*]I have tried the "quiet splash" to "nomodeset" to no avail. Purple screen of no.
[*]The purple screen did show a couple of lines of white text once, I think maybe after trying "nomodeset," and then got stuck again after "Loading initial ramdisk."
[/LIST]

I'm not sure what's affecting what exactly. And I admit I've not been trying things in the most scientific fashion, so I'm not completely certain what happens after what attempt in certain cases.

---

### Post by rae_bot on 2015-10-14
Anybody?

---

### Post by rae_bot on 2015-10-14
Should this be in a different part of the forum, or on a different Ubuntu website, perhaps? The Stack Exchange is less responsive than these forums, it seems, but I don't know where to turn.

---

### Post by rae_bot on 2015-10-21
Should I file a bug report? Or start a new thread and ask the same question again or what?

---

### Post by atl45 on 2016-05-29
I have a similar (or the same) issue, running 16.04. I posted at [http://ubuntuforums.org/showthread.php?t=2326223&p=13496734#post13496734](http://ubuntuforums.org/showthread.php?t=2326223&p=13496734#post13496734)

Let me know if my own post gives you any insight into your own issue. I, like you, am at a loss with this one. That said, you at least appear to be able to use your system without issues once you get past the LUKS greeter(?). I on the other hand am reliving how to do everything using shells all over again :)

---

### Post by oldos2er on 2016-05-29
Closed. Please don't bump old threads, especially when they concern a version of Ubuntu (15.04) that is no longer supported. Thanks!

---

