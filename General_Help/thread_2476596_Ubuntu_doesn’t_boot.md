---
title: "Ubuntu doesn’t boot"
date: 2022-06-30
forum: General Help
---

### Post by he125 on 2022-06-30
I tried to install nvidia drivers because some games were not running but when i tried to it gave me an error ( I do not fully remember the error but it went something like: Failed to install nvidia kernel or something) Now when i try to boot into the system it gets stuck at this screen:
[https://ubuntuforums.org/attachment.php?attachmentid=290679&stc=1](https://ubuntuforums.org/attachment.php?attachmentid=290679&stc=1)
Please help me! ( I have a live usb ready if needed)

---

### Post by TheFu on 2022-06-30
AE_NOT_FOUND are common, unimportant, errors. They are safe to ignore.

If it were me, I'd boot into a Try Ubuntu environment using a flash ISO boot device, then look at the different system logs internal to the system, not the Try Ubuntu environment.  Looks and finding errors, I'd plug those messages into any web-search and learn about each.

And I'd learn to pay attention to errors reported when installing software.  If you hadn't rebooted, it was likely an easier fix.  At this point, you have some partially installed drivers.

If you can blacklist the nvidia drivers and get the system to boot, you can run 
**sudo ubuntu-drivers autoinstall ** on any release prior to 22.04 and hopefully, the correct drivers will be installed.  On 22.04, they deprecated autoinstall for some reasons.  Also, ensure you are NOT using Wayland - use Xorg only with nVidia GPUs.

---

### Post by he125 on 2022-06-30
Actually i realized that i didnt have much on the system i will just backup some files and install ubuntu again thanks for your answer! :)

---

