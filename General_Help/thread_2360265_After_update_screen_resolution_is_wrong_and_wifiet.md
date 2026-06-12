---
title: "After update screen resolution is wrong and wifi/eth is dead"
date: 2017-05-02
forum: General Help
---

### Post by jackall69 on 2017-05-02
Updated my Xubuntu 16.04 recently via the Software Updater. Asked me to restart. After restart the screen resolution is wrong and can't be changed. Also my wifi and ethernet are dead (using a live usb at the moment and internet is working fine on that). Synaptic is showing the kernel needs upgrading but I'm sure thats what the update was for in the first place.

Any help would be appreciated. As I can't connect to the internet via my install, is it possible to fix via live usb if necessary?

Thanks in advance.

---

### Post by ajgreeny on 2017-05-03
Try booting to an older kernel from the grub menu.
There is a bug filed regarding the wifi problem on kernel 4.4.0-77 as of only yesterday when most of us received that kernel version.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1687623](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1687623)

I am not aware of a similar problem related to graphics and resolution, but it is certainly possible that the kernel is the cause of that as well.

---

### Post by jackall69 on 2017-05-03
Thanks for the response. Yes comment #21 in particular explained it all. #CrazyKids

I normally dist-upgrade through terminal but was feeling particularly lazy that day. Oops.

---

