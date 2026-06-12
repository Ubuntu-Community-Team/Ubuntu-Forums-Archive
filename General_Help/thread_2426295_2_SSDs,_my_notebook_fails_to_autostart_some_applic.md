---
title: "2 SSDs, my notebook fails to autostart some applications correctly"
date: 2019-09-06
forum: General Help
---

### Post by bold33 on 2019-09-06
I have a notebook from Taiwanese manufacturer clevo. It has 2 slots for SSD. I have:

one Samsung SSD 860 PRO
one Samsung 960 PRO NVMe M.2 SSD

I boot xubuntu 19.04 from the Samsung SSD 860 PRO. I use the 960 PRO NVMe M.2 SSD as a storage unit.

The notebook always loaded the autostart applications (terminal and thunar) without problems when only the 860 Pro was installed. After installing the 960, thunar started not to autostart at all. If I tried to load it manually, the whole system would become unresponsive. The only solution at this point was to unplug the power supply.

Questions:

I am reducing the life of my ssds doing this, right? I mean both faulty loading and unplugging the power cable.
How do I solve this?

---

### Post by oldfred on 2019-09-06
Have you updated firmware for both SSDs?
And UEFI for your system?

You should not force shutdown as that can cause file corruption and then you have to run fsck on all ext4 partitions.

        [https://askubuntu.com/questions/4408/what-should-i-do-when-ubuntu-freezes](https://askubuntu.com/questions/4408/what-should-i-do-when-ubuntu-freezes)
[https://ubuntuforums.org/showthread.php?t=617349](https://ubuntuforums.org/showthread.php?t=617349)
Generally pressing and holding Ctrl+Alt and
then PrintScr, R, E, I, S, U, B (Raising Elephants Is So Utterly Boring)
should do a clean reboot.
R gives back control of the keyboard, S issues a sync, E sends all processes but init the term signal, I sends all processes but init the kill signal, U mounts all filesystem ro to prevent a fsck at reboot, B reboots the system

---

