---
title: "Ubuntu Boots to Purple Screen"
date: 2017-10-17
forum: General Help
---

### Post by Bruce_Fleming on 2017-10-17
When I went to do a regular update, it came up with a message that said there was not enough room in /boot. What I have been doing was deleting the last two kernels and leaving the current one and the one before in that directory. I thought I had done the same the last time but now it boots to a purple screen.

When I boot it and hit F1 to get into the Ubuntu options that allow for recovery mode, it allows me to do that. However, when I select one of those it says it cannot find the kernel (if I recall correctly), says it is loading an initramfs and stalls with that last message remaining on the screen.

I used UnetBootin to make a Ubuntu 14.05.5 LiveUSB to use Boot-Repair. I boot using the Try Ubuntu option. Then I install boot-repair from the command line using instructions found here:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
On that page, I use the Getting Boot-Repair > 2nd option: install Boot-Repair in Ubuntu.
Those instructions locate the ppa, update, install it and run it - boot-repair.

I followed instructions to do a Recommended repair. It did not work but I did make BootInfo Summary which made a like to pastebin.

I would experiment but am not sure of the consequences of going into the Advanced Repair.

The kernels listed in recovery mode:
4.4.0-72,   -71,   -66,   -64
When  I select one of those as stated above, that is when it hangs on that screen. It says cannot find the kernel and is loading initramfs.

---

